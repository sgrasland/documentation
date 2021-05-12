Le **DOM** signifie **Document Object Model**. Il s'agit d'une **interface** vers une page HTML que l'on peut utiliser pour modifier cette page.</br>
L'objet javascript **document** représente la page HTML courante. L'ensemble des méthodes utilisables sur l'objet **document** 
est disponible sur [la documentation MDN](https://developer.mozilla.org/fr/docs/Web/API/Document).

# Accéder à des éléments du DOM

## document.getElementById()

`document.getElementById('toto')` renvoie l'élément du DOM identifié par l'Id `'toto'`.

## document.getElementsByClassName()

`document.getElementsByClassName('tutu')` renvoie un tableau contenant tous les éléments du DOM ayant la classe `'tutu'`.

## document.getElementsByTagName()

`document.getElementsByTagName('p')` renvoie un tableau contenant tous les éléments du DOM qui sont des `<p>`.

## document.querySelector()

Cette méthode est plus générique et peut se substituer aux 3 méthodes précédentes.
Elle permet de sélectionner un élément du DOM correspondant au **premier résultat** renvoyé par le **sélecteur CSS** qu'on lui passe.</br>
Exemples :

- `document.querySelector('#toto')` renvoie l'élément du DOM identifié par l'Id `'toto'`.
- `document.querySelector('.tutu')` renvoie le premier élément du DOM rencontré qui a la classe `'tutu'`.
- `document.querySelector('p')` renvoie le premier élément du DOM rencontré qui est un `<p>`.
- `document.querySelector('#toto p')` renvoie le premier élément du DOM rencontré qui est un `<p>` enfant de l'élément identifié par l'Id `'toto'`

## document.querySelectorAll()

Cette méthode est similaire à `document.querySelector()` sauf qu'elle retourne un **tableau** contenant l'ensemble des éléments identifiés par le **sélecteur CSS** qu'on lui passe.</br>
Exemple :
- `document.querySelectorAll('#toto p')` renvoie un tableau contenant tous les `<p>` enfants de l'élément identifié par l'Id `'toto'`

# Modifier un élément

## Changer la classe

On peut changer la classe des éléments ayant pour classe `'tutu'` avec `document.querySelectorAll('.tutu').className = 'tutu titi'`.
Ainsi, tous les éléments de classe `'tutu'` auront désormais les classes `'tutu'` et `'titi'`.</br></br>
De manière plus moderne, on peut également utiliser le `'classList'` à la place du `'className'` pour accéder à la liste des classes d'un élément et intéragir avec de manière plus simple. Par exemple, `document.querySelectorAll('.tutu').classList.add('titi')` ajoute la classe `'titi'` aux éléments de classe `'tutu'`.
