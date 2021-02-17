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

## Utilisation
Initialisation d'un repository git à partir d'un répertoire contenant du code :
`git init`

Cela créé un répertoire **.git** qui contiendra tout ce qui est lié au repository git. Pour arrêter de versionner le projet avec Git il suffit de supprimer ce répertoire.
