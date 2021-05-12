Le **DOM** signifie **Document Object Model**. Il s'agit d'une **interface** vers une page HTML que l'on peut utiliser pour modifier cette page.</br>
L'objet javascript **document** représente la page HTML courante. L'ensemble des méthodes utilisables sur l'objet **document** 
est disponible sur [la documentation MDN](https://developer.mozilla.org/fr/docs/Web/API/Document).

# Accéder à des éléments du DOM

## `document.getElementById()`

`document.getElementById('toto')` renvoie l'élément du DOM identifié par l'Id `'toto'`.

## `document.getElementsByClassName()`

`document.getElementsByClassName('tutu')` renvoie un tableau contenant tous les éléments du DOM ayant la classe `'tutu'`.

## `document.getElementsByTagName()`

`document.getElementsByTagName('p')` renvoie un tableau contenant tous les éléments du DOM qui sont des `<p>`.

## `document.querySelector()`

Cette méthode est plus générique et peut se substituer aux 3 méthodes précédentes.
Elle permet de sélectionner un élément du DOM correspondant au **premier résultat** renvoyé par le **sélecteur CSS** qu'on lui passe.</br>
Exemples :

- `document.querySelector('#toto')` renvoie l'élément du DOM identifié par l'Id `'toto'`.
- `document.querySelector('.tutu')` renvoie le premier élément du DOM rencontré qui a la classe `'tutu'`.
- `document.querySelector('p')` renvoie le premier élément du DOM rencontré qui est un `<p>`.
- `document.querySelector('#toto p')` renvoie le premier élément du DOM rencontré qui est un `<p>` enfant de l'élément identifié par l'Id `'toto'`

## `document.querySelectorAll()`

Cette méthode est similaire à `document.querySelector()` sauf qu'elle retourne un **tableau** contenant l'ensemble des éléments identifiés par le **sélecteur CSS** qu'on lui passe.</br>
Exemple :
- `document.querySelectorAll('#toto p')` renvoie un tableau contenant tous les `<p>` enfants de l'élément identifié par l'Id `'toto'`

## `children/childNodes`, `parentElement`, `nextElementSibling`

On peut récupérer les éléments proches d'un élément HTML avec les propriétés suivantes :
- `children` renvoie les **éléments HTML** enfants de l'élément donné.
- `childNodes` renvoie **tous les éléments** endants de l'élément donné, y compris les éléments **text**.
- `parentElement` renvoie **le parent** de l'élément donné.
- `nextElementSibling`/`previousElementSibling` renvoie l'élément **suivant** ou **précédent** l'élément donné.

Prenons par exemple le code HTML suivant :

```
<ul>
  <li id='1'>1</li>
  <li id='2'>2</li>
  <li id='3'>3</li>
</ul>
```

- `document.querySelector('ul').children` renvoie `[<li id='1'>1</li>, <li id='2'>2</li>, <li id='3'>3</li>]`
- `document.querySelector('ul').childNodes` renvoie `[#text, <li id='1'>1</li>, #text, <li id='2'>2</li>, #text, <li id='3'>3</li>, #text]`
- `document.querySelector('ul').firstChild` renvoie `#text`
- `document.querySelector('ul').firstElementChild` renvoie `<li id='1'>1</li>`
- `document.querySelector('#1').parentElement` renvoie `<ul>...</ul>`
- `document.querySelector('#1').nextElementSibling` renvoie `<li id='2'>2</li>`

# Modifier un élément

## Changer la classe

On peut changer la classe de l'élément `'toto'` avec `document.querySelector('#toto').className = 'titi'`.
Ainsi, l'élément d'Id `'toto'` aura désormais la classe `'titi'`.</br></br>
De manière plus moderne, on peut également utiliser le `'classList'` à la place du `'className'` pour accéder à la liste des classes d'un élément et intéragir avec de manière plus simple. Par exemple, `document.querySelector('#toto').classList.add('titi')` ajoute la classe `'titi'` à l'élément d'Id `'toto'`.

## Changer le style

On récupère le style de l'élément `'toto'` avec `document.querySelector('#toto').style` qui renvoie un élément **CSSStyleDeclaration** contenant tous les styles CSS de l'élément (tous les styles que l'élément n'a pas sont aussi représentés, mais sont vides).</br></br>
Par exemple, on peut modifier la **font-size** de l'élément `'toto'` avec `document.querySelector('#toto').style.fontSize = '20px'`.

## Changer le contenu d'un élément

On peut récupérer le contenu de l'élément `'toto'` avec `document.querySelector('#toto').innerHTML`. On peut par exemple remplacer son contenu avec `document.querySelector('#toto').innerHTML = '<strong>Salut</strong>'`.</br></br>
Si on souhaite modifier uniquement le texte contenu dans un élément sans toucher aux balises HTML, on peut utiliser `document.querySelector('#toto').textContent = 'Salut'`.
