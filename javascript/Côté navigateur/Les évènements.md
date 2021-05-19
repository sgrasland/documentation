En Javascript, on peut réagir à des évènements grâce à la méthode `addEventListener` qui s'utilise sur un élément du DOM. Cette méthode prend 2 paramètres :
- Le type d'évènement auquel on souhaite réagir
- La fonction à exécuter lorsque l'évènement survient
Exemple :
```
const p = document.querySelector('p')
const setRed = function() {
  p.style.setProperty('color', 'red')
}
p.addEventListener('click', setRed)
```
Si on souhaite passer des paramètres à la fonction à exécuter on peut passer par une fonction anonyme :
```
const p = document.querySelector('p')
const setColor = function(elem, color) {
  elem.style.setProperty('color', color)
}
p.addEventListener('click', function(){setColor(p, 'blue')})
```
