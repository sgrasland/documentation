# Git Basics
Contrairement à SVN, Git est un système de contrôle de version **distribué** alors que SVN est **centralisé**. Cela signifie que lorsque le repository local Git est synchronisé avec un repository distant, il contient exactement les mêmes informations.

### Installation et configuration
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

### Etapes d'un commit :
![alt text](https://github.com/sgrasland/documentation/blob/main/git/resources/git_steps.png "Etapes d'un commit")
- On commence par vérifier quelles sont les modifications que l'on est sur le point d'ajouter avec la commande `git diff`.
- On ajoute nos modifications dans la **staging area** avec la commande `git add [FILE]` ou `git add -A` pour ajouter d'un seul coup toutes nos modifications. On peut vérifier les **changements prêts à être commités** avec la commande `git status`.
On peut annuler ces ajouts avec la commande `git reset [FILE]` ou `git reset` pour annuler tous les ajouts d'un seul coup. `git status` permet encore une fois de vérifier la bonne prise en compte.
- On **commit** nos modifications sur le repository local avec la commande `git commit -m "[MESSAGE]"`. Encore une fois, `git status` pour vérifier la bonne prise en compte. La commande `git log` permet de consulter la liste des commits effectués sur le repository.

### .gitignore
Pour déclarer une liste de fichiers et/ou de répertoires à ne **pas inclure** dans le repository, on créé un fichier **.gitignore** qui contiendra une ligne par élément. En général on souhaite versionner ce fichier.
Par exemple on peut décider d'ignorer :
- Le fichier toto.cpp : `toto.cpp`
- Tous les fichiers **.log** : `*.log`
- Le répertoire **build** : `/build/*`
- Tout fichier ou répertoire **tmp** contenu dans le répertoire **src** ou dans un de ses sous-répertoires : `/src/**/tmp`
