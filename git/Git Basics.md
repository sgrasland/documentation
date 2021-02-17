# Git Basics
Contrairement à SVN, Git est un système de contrôle de version **distribué** alors que SVN est **centralisé**. Cela signifie que lorsque le repository local Git est synchronisé avec un repository distant, il contient exactement les mêmes informations.

## Installation et configuration
Installation :
`sudo apt-get install git`

Configuration initiale :
`git config --global user.name "[USERNAME]"`
`git config --global user.email "[EMAIL]"`

Lister les configurations :
`git config --list`

Manuel d'utilisation :
`git help [COMMANDE]`

Initialisation d'un repository git à partir d'un répertoire contenant du code :
`git init`

Cela créé un répertoire **.git** qui contiendra tout ce qui est lié au repository git. Pour arrêter de versionner le projet avec Git il suffit de supprimer ce répertoire.

## Commandes de base :
Pour obtenir des informations sur l'état du repository local : `git status`. Cela permet de savoir **sur quelle branche on se trouve**, la **liste des fichiers non versionnés** dans le répertoire, et la **liste des commits effectués** sur le repository local.

Pour ajouter un fichier au repository : `git add [FILE]`

### .gitignore
Pour déclarer une liste de fichiers et/ou de répertoires à ne **pas inclure** dans le repository, on créé un fichier **.gitignore** qui contiendra une ligne par élément. Par exemple on peut décider d'ignorer :
- Le fichier toto.cpp : `toto.cpp`
- Tous les fichiers **.log** : `*.log`
- Le répertoire **build** : `/build/*`
- Tout fichier ou répertoire **tmp** contenu dans le répertoire **src** ou dans un de ses sous-répertoires : `/src/**/tmp`
