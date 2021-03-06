
# Syntaxes de déclaration

On peut utiliser plusieurs syntaxes pour déclarer une fonction javascript :

```
function maFonction(mesArguments) {
  
}
```
> nb : La syntaxe précédente permet d'utiliser la fonction avant qu'elle ne soit définie dans le fichier .js
```
const maFonction = function(mesArguments) {
  
}
```
```
const myFunction = (mesArguments) => {

}
```

# Remarques

- Si une fonction prend **2 arguments** et qu'on l'appelle en ne lui en donnant qu'**1 argument**, alors le second argument est **undefined** lors de l'exécution.
- On peut déclarer des fonctions à l'intérieur d'objets puis y accéder via les propriétés de l'objet. Par exemple, l'objet intégré à Javascript **Math** possède de nombreuses fonctions en propriétés. Les fonctions en propriétés d'objets sont appelées **méthodes**.
- Les objets de type **String** et **Number** sont des objets classiques qui ont également des méthodes intégrées. On peut par exemple exécuter `"Coucou".toUpperCase()` ou `465.toString()`.
- Les méthodes du **prototype** sont utilisables directement sur la valeur : `"Coucou".toUpperCase()`. Au contraire, les méthodes **globales** s'utilisent de la manière suivante : `Array.isArray([1, 2, 3])`.
