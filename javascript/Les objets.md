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

## `Object.create()`
Cette méthode n'est généralement pas non plus utilisée, mais elle permet d'obtenir le même résultat sans accéder directement à l'attribut `__proto__` :

```
[...]

var jean = Object.create(eleve)
jean.nom = "Jean"
jean.notes = [10, 20]

var pierre = Object.create(eleve)
jean.nom = "Pierre"
jean.notes = [12, 16]

jean.moyenne()
pierre.moyenne()
```

fonctionne et renvoie :

```
Ma moyenne est de 15
Ma moyenne est de 14
```

## Les constructeurs
Cette méthode est la plus largement utilisée pour faire de l'héritage en javascript. La syntaxe est la suivante (par convention on met une majuscule au nom de la **classe** pour la différencier des **instances**) :

```
var Eleve = function(nom, notes) {
  this.nom = nom,
  this.notes = notes,
  this.moyenne = function() {
    const reducer = (accumulator, currentValue) => accumulator + currentValue;
    const sommeNotes = this.notes.reduce(reducer)
    console.log("Ma moyenne est de " + sommeNotes/this.notes.length)
  }
}

var jean = new Eleve("Jean", [10, 20])
var pierre = new Eleve("Pierre", [12, 16])

jean.moyenne()
pierre.moyenne()
```
fonctionne et renvoie :

```
Ma moyenne est de 15
Ma moyenne est de 14
```

On pourrait également définir la classe `Eleve`, **qui est en réalité une fonction**, en utilisant l'attribut `prototype` des **fonctions** javascript. 
> Nb : L'attribut `prototype` d'une fonction javascript est un objet contenant un attribut `constructor` qui représente la fonction elle-même.

On peut utiliser l'attribut `prototype`de la fonction `Eleve` pour définir une nouvelle méthode accessible par tous les objets instanciés à partir d'`Eleve` de la façon suivante :

```
Eleve.prototype.leveLaMain = function () {
  console.log(this.nom + " lève la main !")
}
```

On pourra alors utiliser :

```
jean.leveLaMain()
pierre.leveLaMain()
```

## En résumé

Généralement, on utilisera la syntaxe suivante pour faire de l'héritage en javascript :


```
var Eleve = function(nom, notes) {
  this.nom = nom,
  this.notes = notes,
}

Eleve.prototype.moyenne = function () {
  const reducer = (accumulator, currentValue) => accumulator + currentValue;
  const sommeNotes = this.notes.reduce(reducer)
  console.log("Ma moyenne est de " + sommeNotes/this.notes.length)
}

Eleve.prototype.leveLaMain = function () {
  console.log(this.nom + " lève la main !")
}

var jean = new Eleve("Jean", [10, 20])
var pierre = new Eleve("Pierre", [12, 16])
```
