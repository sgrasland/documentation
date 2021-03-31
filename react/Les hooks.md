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
