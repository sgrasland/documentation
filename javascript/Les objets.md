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

# Les prototypes

En javascript, les objets possèdent tous un attribut `__proto__` (le prototype). Lorsqu'on appelle une méthode sur cet objet, le javascript commence par regarder si cette méthode existe directement dans l'objet. S'il ne la trouve pas, il va regarder si elle existe dans l'attribut `__proto__` (S'il ne la trouve toujours pas, il va regarder dans l'attribut `__proto__` du `__proto__` et ainsi de suite).

## L'attribut `__proto__` permet de faire de l'héritage

L'exemple suivant illustre comment on pourrait utiliser l'attribut `__proto__` pour faire de l'héritage en javascript :

```
var eleve = {
  moyenne: function() {
    const reducer = (accumulator, currentValue) => accumulator + currentValue;
    const sommeNotes = this.notes.reduce(reducer)
    console.log("Ma moyenne est de " + sommeNotes/this.notes.length)
  }
}

var jean = {
  nom: "Jean",
  notes: [10, 20]
}
var pierre = {
  nom: "Pierre",
  notes: [12, 16]
}

jean.__proto__ = eleve
pierre.__proto__ = eleve

jean.moyenne()
pierre.moyenne()
```

fonctionne et renvoie :

```
Ma moyenne est de 15
Ma moyenne est de 14
```

A noter qu'en pratique **on n'utilisera jamais directement cette méthode pour faire de l'héritage en javascript**.

## L'héritage en pratique
Pour faire de l'héritage en javascript, on n'utilisera **jamais directement** l'attribut `__proto__`. On utilise plutôt la méthode `Object.create()` comme illustré par l'exemple suivant :
