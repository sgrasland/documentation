# `git revert`

Nouveau commit pour annuler des commits précédents.


# `git reset`

Permet de modifier l'état d'une ou de plusieurs des **3 arborescences** (i.e *HEAD*, *Index* et *Working directory*) pour la/les ramener à l'état d'un commit donné. Sans option particulière, la commande `git reset` est l'opposé de la commande `git add`.

Partant de l'état initial suivant :

<img src="https://github.com/sgrasland/documentation/blob/main/git/resources/git-reset-init.png" alt="Etat initial du repository" width="500"/>

Les actions effectuées par `git reset [COMMIT_ID]` sont :

1. **Déplacement du HEAD** vers le commit spécifié. Avec l'option `--soft`, c'est l'unique action effectuée.

<img src="https://github.com/sgrasland/documentation/blob/main/git/resources/git-reset-1.png" alt="git reset --soft" width="500"/>

2. **Modification de l'index** vers le commit spécifié. Avec l'option `--mixed` (et même sans aucune option, comportement par défaut), le `git reset` s'arrête à cette étape.

<img src="https://github.com/sgrasland/documentation/blob/main/git/resources/git-reset-2.png" alt="git reset --mixed" width="500"/>

3. **Modification de la copie de travail** vers le commit spécifié. Avec l'option `--hard` le `git reset` continuera jusqu'à cette étape. A noter que cette dernière option est dangereuse car elle **efface vos modifications locales**.

<img src="https://github.com/sgrasland/documentation/blob/main/git/resources/git-reset-3.png" alt="git reset --mixed" width="500"/>

On peut également passer un **chemin de fichier** en argument de la commande pour effectuer ces actions uniquement sur un fichier donné.

Un cas d'usage intéressant de `git reset` est de pouvoir **écraser des commits**. Par exemple, si au cours du développement on a effectué plusieurs commits du type *work in progress*, une fois l'étape de développement terminée, on peut **replacer l'index** sur l'état initial avec `git reset --soft [INITIAL_COMMIT_ID]` puis exécuter un `git commit` pour englober l'équivalent des commits précédents.
