.gitignore

Pour déclarer une liste de fichiers et/ou de répertoires à ne pas inclure dans le repository, on créé un fichier .gitignore qui contiendra une ligne par élément. En général on souhaite versionner ce fichier. Par exemple on peut décider d'ignorer :

- Le fichier toto.cpp : toto.cpp
- Tous les fichiers .log : *.log
- Le répertoire build : /build/*
- Tout fichier ou répertoire tmp contenu dans le répertoire src ou dans un de ses sous-répertoires : /src/**/tmp
