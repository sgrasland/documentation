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
