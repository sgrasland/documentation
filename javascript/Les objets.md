# Le mot-clé `this`

Par défaut, `this` représente l'objet `window`.</br>
En revanche, utilisé dans un `objet` javascript, `this` représente cet objet.</br>
Par exemple :

```
var eleve = {
  nom: 'Jean',
  description: function() {
    console.log(this)
  }
}
eleve.description()
```
renvoie
```
Object {nom: "Jean"}
```
