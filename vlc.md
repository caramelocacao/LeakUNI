# VLC 

Dans ce module nous verrons comment développer des sripts.lua et compiler vlc. 

## Installation 

Une fois l'installation et la première compilation faite gràce à la doc https://code.videolan.org/jbk/small_vlc_projects/-/blob/main/README.md. Nous modifierons et développerons des scripts dans le path suivant `modules/gui/qt/`.
Pour exécuter notre application nous l'appellerons de cette manière `./vlc`.

## Compilation 

La compilation se passe au niveau du Makefile vous devrez ajouter le chemin de votre script à partir de la 95 ligne `lua/playlist/tiktok.luac` ainsi qu'à partir de la ligne 1158 `lua/playlist/tiktok.lua`. Pour compiler VLC il faut `make` dans le chemin du repo depuis le cli pour compiler les scripts. 


## Etape 1: 

Pour lire une video video ou bien de soundcloud il faut depuis l'application aller dans "media", puis dans "open network strem" et insérer votre lien. 

- soundcloud : https://soundcloud.com/kalashofficial/kalash-tombolo
- vimeo : https://vimeo.com/697175330 

## Etape 2 : 

Pour lire une video vlc utiise deux fonctions, la fonction `probe()`, et la fonction `parse()`. La première permet de verifier grâce à la méthode `vlc.access` si c'est bien un lien `http` ou `https` et si c'est le cas on verifie si ça match avec le pattern du lien de tiktok. 

```lua
function probe()
    return (vlc.access == "http" or vlc.access == "https")
    and string.match( vlc.path, "^www%.tiktok%.com/.+/.+/.+")
end
```

Ensuite viens la fonction `parse()` qui est appelé que si `probe()` renvoie `true`. Cette dernière va scrapper les données ligne par ligne pour en fonction du pattern donné en paramètre pour lire le lien. 

```lua

function parse()
    if string.match( vlc.path, "^www%.tiktok%.com/.+/.+/.+" ) then
        -- The /config API will return the data on a single line.
        -- Otherwise, search the web page for the config.
        local config = vlc.readline()
        while true do
            local line = vlc.readline()
            if not line then break end
            if string.match( line, "var config = {" ) then --@id"/.+/.+/video              |         (pour moi ) x  @id":"https://www.tiktok.com/.+/video 
                config = line
                break
            end
        end

    end
  ```
