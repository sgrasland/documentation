## Introduction
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

Pour cloner un repository existant :
`git clone [URL] [LOCAL PATH]`

Pour obtenir des informations sur l'état du repository local : `git status`. Cela permet de savoir **sur quelle branche on se trouve**, la **liste des fichiers non versionnés** dans le répertoire, et la **liste des commits effectués** sur le repository local.

Pour obtenir des informations sur le repository distant : `git remote -v`. Cela permet de consulter l'URL du repository distant ainsi que sa copie locale.

Pour obtenir des informations sur les branches des repository distant et local : `git branch -a`

*nb : Le mot-clé **origin** dans les commandes git signifie qu'on effectue une opération avec le repository distant à partir duquel on a cloné notre repository local.*

## Installation et configuration

# Les 3 arborescences

Git peut-être représenté sous la forme d'un gestionnaire de contenu de 3 **arborescences** différentes (comprendre **collections de fichiers**) :
- Le **HEAD** : Représente la **dernière validation** effectuée sur la branche actuelle. C'est un **pointeur sur le dernier commit effectué** sur cette branche.
- L'**Index** : Représente le **prochain commit**. C'est à dire tout ce qui sera validé si on exécute la commande `git commit`.
