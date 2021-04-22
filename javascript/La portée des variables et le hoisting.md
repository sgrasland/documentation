# La portée des variables

Une variable déclarée dans une **fonction** n'est accessible qu'à l'intérieur de celle-ci. Par exemple :
```
var demo = function() {
  var a = "toto"
}
demo()
console.log(a)
```
Affichera *undefined* dans la console. </br>
En revanche, une variable déclarée **avant** la définition de la fonction pourra être accédée dans la fonction. Par exemple :
```
var a = "toto"
var demo = function() {
  console.log(a)
}
demo()
```
Affichera *toto* dans la console.

# Le hoisting
Il s'agit du fait que les variables et les fonctions (uniquement sous la forme **function test () {...}**) déclarées dans un fichier .js sont *hissées* en début de fichier lors de l'exécution.</br>
Ainsi, l'exemple suivant :
```
console.log(a)
var a = "toto"
```
Correspond en réalité à :
```
var a
console.log(a)
a = "toto"
```
Et affichera *undefined* dans la console (mais ne fera pas d'erreur).
>Nb : cela explique pourquoi les fonctions définies sous la forme **var test = function () {...}** renvoient *undefined is not a function* si on les exécute avant de les avoir déclarées.
