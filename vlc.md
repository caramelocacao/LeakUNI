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


