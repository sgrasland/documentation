# Le Try... Catch

La syntaxe est la suivante :

```
try {
  // Code à exécuter
} catch (e) {
  // Gestion des cas d'erreur
}
```

L'objet `e` renvoyé est un objet de type `Error` ([Documentation MDN](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Error)).<br/>
On peut également ajouter un bloc `finally` pour exécuter du code en cas d'erreur :

```
try {
  // Code à exécuter
} catch (e) {
  // Gestion des cas d'erreur
} finally {
  // Code qui sera toujours exécuté, même si une erreur survient dans le bloc "try"
}
```

# Les erreurs personnalisées

On peut renvoyer des erreurs *personnalisées* avec `throw new Error()` comme dans l'exemple suivant :

```
if (myNumber < 0) {
  throw new Error('Ce nombre ne peut pas être négatif')
}
```
L'erreur générée peut alors être rattrappée dans un bloc `try... catch`. 
