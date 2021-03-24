## Annulation de changements

### `git revert`

Nouveau commit pour annuler des commits précédents.

### `git reset`

Permet de modifier l'état d'une ou de plusieurs des **3 arborescences** (i.e *HEAD*, *Index* et *Working directory*) pour la/les ramener à l'état d'un commit donné.

Partant de l'état initial suivant :

<img src="https://github.com/sgrasland/documentation/blob/main/git/resources/git-reset-init.png" alt="Etat initial du repository" width="500"/>

Les actions effectuées par `git reset [COMMIT_ID]` sont :

1. **Déplacement du HEAD** vers le commit spécifié. Avec l'option `--soft`, c'est l'unique action effectuée.

<img src="https://github.com/sgrasland/documentation/blob/main/git/resources/git-reset-1.png" alt="git reset --soft" width="500"/>

2. **Modification de l'index** vers le commit spécifié. Avec l'option `--mixed` (et même sans aucune option, comportement par défaut), le `git reset` s'arrête à cette étape.

<img src="https://github.com/sgrasland/documentation/blob/main/git/resources/git-reset-2.png" alt="git reset --mixed" width="500"/>

3. **Modification de la copie de travail** vers le commit spécifié. Avec l'option `--hard` le `git reset` continuera jusqu'à cette étape. A noter que cette dernière option est dangereuse car elle **efface vos modifications locales**.

<img src="https://github.com/sgrasland/documentation/blob/main/git/resources/git-reset-3.png" alt="git reset --mixed" width="500"/>
