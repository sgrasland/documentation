# Pourquoi les hooks existent ?

Les **hooks** permettent d'utiliser un **state** dans un **_functional component_**.

> **_Class component_** : What should I render at what stage of my existence. </br>
> **_Hooks_** : What should my data look like.

Traduction : Les hooks permettent de passer d'une logique où on **contrôle l'affichage du composant** à une logique où on contrôle **l'état des données du composant**.

# Utilisation

Les hooks doivent être déclarés au **début** du composant :

```
function MyComponent() {
useHook();

[...]

}
```

# Principaux hooks

## useState

**useState** prend la valeur par défaut qu'on veut donner au **state** en paramètre (0 dans l'exemple ci-dessous).
```
const [count, setCount] = useState(0);
```

## useEffect

**useEffect** remplace les fonctions de gestion du **cycle de vie** d'un composant que sont :
```
componentDidMount() {
  // Appelé lors de l'initialisation
}
componentDidUpdate() {
  // Appelé lorsque le state a été mis à jour
}
componentWillUnmount() {
  // Appelé lorsque le composant a été détruit
}
```

**useEffect** permet d'exécuter du code à chaque fois que le composant est chargé ou quand son state change (**componentDidMount()** et **componentDidUpdate()**).</br>
Le **return** du **useEffect** est exécuté lorsque le composant est détruit (équivalent du **componentWillUnmount()**).</br>
Pour éviter les boucles infinies si par exemple on modifie le **state** à l'intérieur du **useEffect**, on peut indiquer au hook les **dépendances** qu'il a :
```
useEffect(
  () => {
    // Code à exécuter, équivalent componentDidMount() et componentDidUpdate()
    return () => {
      // Code à exécuter, équivalent componentWillUnmount()
    }
  },
  [//Dépendances]
)
```
Si le tableau des dépendances est vide, alors **useEffect** n'est exécuté qu'à l'initialisation du composant.

## useContext

**useContext** permet de transmettre des données entre les composants sans passer par leurs **props**.</br>
Exemple :
```
const moods = {
  happy: ':D',
  sad : ':('
}

const MoodContext = createContext(moods);

function App(props) {
  return (
    <MoodContext.Provider value={moods.happy}>
      <MoodElement />    
    </MoodContext.Provider>
  )
}

function MoodElement() {
  const mood = useContext(MoodContext); // Valeur récupérée du provider parent le plus proche
}
```
## useRef

**useRef** renvoie un objet qui va exister pendant la durée de vie du composant. Quand sa valeur change, le composant **n'est pas redessiné**.
On accède à la valeur courante de l'objet via la propriété **.current**. Le paramètre de **useRef()** est sa valeur initiale.</br>
Exemple :

```
function App() {

  const compteur = useRef({count: 0})
  
  const handleClick = () => {
    compteur.current.count++
    console.log(compteur)
  }
  
  return <div>
    <button onClick={handleClick} >Incrémenter le compteur</button>
  </div>
}
```

Le cas d'utilisation le plus courant est de **récupérer un élément HTML du DOM** :

```
function App() {

  const input = useRef(null)
  
  const handleClick = () => {
    console.log(input.current.value)
  }
  
  return <div>
    <input type='text' ref={input} />
    <button onClick={handleClick} >Loguer la valeur</button>
  </div>
}
```

## useReducer

**useReducer** permet d'appliquer la logique de **Redux** au **state** du composant. Contrairement au hook **useState** qui permet de modifier directement le **state** du composant, **useReducer** va **dispatcher** une action qui sera traitée par un **reducer** pour modifier le **state**.</br>
**useReducer** renvoie un tableau à deux éléments qui sont :
1. La nouvelle valeur du **state** après passage dans le hook
2. La fonction permettant de **dispatcher** une action

Et prend deux paramètres :

1. La fonction **reducer** à utiliser 
2. La valeur par défaut du state

`const [state, dispatch] = useReducer(reducerFunction, initialStateValue)`
</br></br>
Exemple :

```
function myReducer(state, action) {
  switch(action.type) {
    case 'increment':
      return state + 1;
    case 'decrement':
      return state - 1;
    default:
      throw new Error();
  }
}

function App() {

  const [state, dispatch] = useReducer(myReducer, 0);
   
  return <div>
    Count : {state}
    <button onClick={() => dispatch({type: 'decrement'})}> - </button>
    <button onClick={() => dispatch({type: 'increment'})}> + </button>
  </div>
}
```

## useMemo

Ce hook permet d'améliorer les performances de son appli en mettant en cache des résultats de fonctions. **useMemo** prend en second argument un tableau des dépendances pour que le calcul ne soit fait que quand certaines conditions sont réunies. </br>
Exemple :

```
function App() {

  const [count, setCount] = useState(0);
  
  const expensiveCount = useMemo(() => {
    return count ** 2;
  }, [count])
  
  return [...]
}
```

## useCallback

Lorsqu'on définit une fonction dans un composant en React, un objet **fonction** est créé à chaque fois que le composant est redessiné. Un moyen d'éviter cela est d'utiliser le hook **useCallback** qui va mémoriser la fonction et ne pas recréer d'objet à chaque redessin du composant. Un cas d'utilisation classique est lorsque l'on souhaite passer la même fonction à plusieurs composants enfants.</br>
Exemple :

```
function App() {

  const [count, setCount] = useState(0);
  
  const showCount = useCallback(() => {
    alert(`Count ${count}`);
  }, [count])
  
  
  return <SomeChild handler={showCount} />
}
```

# Les hooks de React Router

Avant **React Router 5**, les propriétés **match**, **location** et **history** étaient passées implicitement aux composants **React Router**. Depuis la version 5, ce n'est plus le cas et il faut utiliser les hooks pour y accéder.

## useHistory

Permet d'accéder à la propriété **history** de **React Router** et d'utiliser ses fonctions ([*cf documentation de **React Router***](https://reactrouter.com/web/api/)) comme par exemple **push** :</br>

```
function HomeButton() {
  let history = useHistory();

  function handleClick() {
    history.push('/home');
  }

  return (
    <button type="button" onClick={handleClick}>
      Go home
    </button>
  );
}
```

## useLocation

Permet d'accéder à la propriété **location** de **React Router** qui représente l'URL courante. On peut par exemple obtenir les **query params** de la façon suivante :</br>
 ```
 const location = useLocation();
 const queryParams = location.search;
 ```

## useParams

Permet d'accéder à la propriété **match.params** de **React Router** qui représente les paramètres de l'URL courante. Par exemple :</br>

```
<Route path="/:id/about">
 <About />
</Route>

function About() {
 const { id } = useParams();
 return (
  <div>
   <h2>Now showing post {id}</h2>
  </div>
 );
}
```
