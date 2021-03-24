## Les branches
En général, quand on ajoute une feature, on créé une nouvelle branche sur le repository avec la commande `git branch [BRANCH NAME]`. Ensuite, pour travailler sur la branche nouvellement créée et non plus sur la branche *main*, on utilise la commande `git checkout [BRANCH NAME]`. On peut ensuite **pusher** la branche créée localement sur le repository distant avec `git push -u origin [BRANCH NAME]`.

Une fois que l'on a terminé de développer la nouvelle feature sur la branche, on souhaite généralement la **merger** avec la branche **main**. Les étapes d'un merge sont les suivantes :
- On se replace sur la branche **main** avec `git checkout main`.
- On **pull** pour se mettre à jour avec `git pull origin main`.
- On **merge** les deux branches avec `git merge [BRANCH NAME]`.
- On **push** le résultat du merge avec `git push origin master`.

La commande `git branch --merged` permet de visualiser les branches qui ont été mergées avec la branche courante. On peut enfin supprimer la branche créée temporairement pour le développement de la feature avec :
- Pour le repository local : `git branch -d [BRANCH NAME]`.
- Pour le repository distant : `git push origin --delete [BRANCH NAME]`.
