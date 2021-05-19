# `addEventListener()`

En Javascript, on peut réagir à des évènements grâce à la méthode `addEventListener` qui s'utilise sur un élément du DOM. Cette méthode prend 2 paramètres :
- Le type d'évènement auquel on souhaite réagir
- La fonction à exécuter lorsque l'évènement survient

Exemple :
```
const p = document.querySelector('p')
const setRed = function() {
  this.style.setProperty('color', 'red')
}
p.addEventListener('click', setRed)
```
> A noter que `this` vaut ici l'objet `p` sur lequel le listener a été ajouté.

Si on souhaite passer des paramètres à la fonction à exécuter on peut passer par une fonction anonyme :
```
const p = document.querySelector('p')
const setColor = function(elem, color) {
  elem.style.setProperty('color', color)
}
p.addEventListener('click', function(){setColor(p, 'blue')})
```
On peut également récupérer l'objet évènement dans la fonction à exécuter de la façon suivante :
```
const p = document.querySelector('p')
const setColor = function(elem, color) {
  elem.style.setProperty('color', color)
}
p.addEventListener('click', function(event){
  setColor(p, 'blue')
  console.log(event)
})
```
Ou encore si on veut extraire la définition de la fonction de l'eventListener :
```
const p = document.querySelector('p')
const setColor = function(elem, color) {
  elem.style.setProperty('color', color)
}
const onClick = function(event) {
  setColor(this, 'blue')
  console.log(event)
}
p.addEventListener('click', onClick)
```

> Dans la console de Google Chrome, on peut visualiser la liste des évènement écoutés par un élément donné en cliquant sur le sous-onglet **Event Listeners** dans le menu **Elements**

# `removeEventListener()`

Cette méthode permet de retirer une fonction ajoutée via un `addEventListener()` sur un élément :

```
p.addEventListener('click', onClick)
p.removeEventListener('click', onClick)
```

# `event.preventDefault()`

La méthode `preventDefault()` permet de ne pas effectuer l'action par défaut induite par l'évènement. Par exemple :
- Si on clique sur un bouton pour soumettre un formulaire, `preventDefault()` annule la soumission du formulaire
- Si on clique sur un lien vers un site externe, `preventDefault()` annule la redirection vers ce site

`preventDefault()` annule également la propagation de l'évènement dans les éléments parents de celui sur lequel l'`eventListener` a été ajouté. On peut également utiliser la méthode `stopPropagation()` si on souhaite uniquement annuler la propagation de l'évènement.

Exemple d'utilisation :
```
const link = document.querySelector('a')
p.addEventListener('click', function(event){
  event.preventDefault()
})
```
