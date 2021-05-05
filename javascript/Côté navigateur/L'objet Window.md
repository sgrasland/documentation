# Import des fichiers Javascript dans un fichier HTML

L'import des fichiers Javascript peut se faire à deux endroits dans notre fichier HTML :
- Dans la balise `head`. Dans ce cas, le code Javascript sera exécuté avant que la page HTML ne soit chargée.
- A la fin de la balise `body`. Dans ce cas, le contenu du fichier HTML sera chargé avant que le Javascript ne s'exécute. Cette deuxième option permet de ne pas bloquer l'exécution de la page.

# L'objet `window`

[Documentation MDN de l'objet Window.](https://developer.mozilla.org/fr/docs/Web/API/Window)<br/>
L'objet `window` existe par défaut dans une page web. Lorsqu'on déclare une variable, cette variable se retrouvera en propriété de l'objet `window`. Par exemple :

```
var test = "toto"
console.log(window.test)
```

renvoie "toto".<br/>

## Méthodes de l'objet `window`

### `alert`

`window.alert('Ceci est une alerte')` ouvre une pop-up avec un bouton *OK*. Le code qui suit un `window.alert()` n'est exécuté que lorsque l'utilisateur a cliqué sur le bouton *OK* de la pop-up.

### `prompt`

```
var userEntry = window.prompt('Entrez une valeur')
console.log(userEntry)
```

ouvre une pop-up avec un bouton *OK/Annuler* et un champ de saisie pour l'utilisateur. Le code qui suit un `window.prompt()` n'est exécute que lorsque l'utilisateur a cliqué sur le bouton *OK* ou *Annuler*.

### `confirm`

```
var userConfirmed = window.confirm('Confirmez')
console.log(userConfirmed)
```

ouvre une pop-up avec un bouton *OK/Annuler*. Le code qui suit un `window.confirm()` n'est exécute que lorsque l'utilisateur a cliqué sur le bouton *OK* ou *Annuler*.
La valeur renvoyée est `true` si l'utilisateur a cliqué sur *OK* et `false` s'il a cliqué sur *Annuler*.

### `setInterval`


