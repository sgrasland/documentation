# Etapes d'un commit
![Etapes d'un commit](https://github.com/sgrasland/documentation/blob/main/git/resources/git_steps.png "Etapes d'un commit")
- On commence par vérifier quelles sont les modifications que l'on est sur le point d'ajouter avec la commande `git diff`.
- On ajoute nos modifications dans la **staging area** (i.e l'**Index**) avec la commande `git add [FILE]` ou `git add -A` pour ajouter d'un seul coup toutes nos modifications. On peut vérifier les **changements prêts à être commités** avec la commande `git status`.
On peut annuler ces ajouts avec la commande `git reset [FILE]` ou `git reset` pour annuler tous les ajouts d'un seul coup. `git status` permet encore une fois de vérifier la bonne prise en compte.
- On **commit** nos modifications sur le repository local avec la commande `git commit -m "[MESSAGE]"`. Encore une fois, `git status` pour vérifier la bonne prise en compte. La commande `git log` permet de consulter la liste des commits effectués sur le repository.
- On met à jour son repository local en faisant un **pull** sur la branche voulue du repository distant avec la commande `git pull origin main` (équivalent du *svn update*).
- On **push** son commit sur la branche voulue du repository distant avec la commande `git push origin main`.

# Modifier son dernier commit
- Pour modifier le **message** du dernier commit, on exécute `git commit --amend`
- Pour modifier le **contenu** du dernier commit, on exécute un `git add` ou `git rm` puis un `git commit --amend` qui modifiera votre commit précédent en y incluant ces modifications. **Attention** : Il ne faut pas faire ça si le dernier commit a déjà été **pushé** car la commande modifie l'identifiant du commit.
