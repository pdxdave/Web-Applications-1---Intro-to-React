# Web-Applications-1---Intro-to-React
Web Applications 1 - Intro to React

#### What is React?
React is a UI component library

#### Why was it made?
* It was built to deal with state.  For instance, the posts on Facebook represents a lot of data to deal with.    
* How to deal with all the data w/o bogging down the browser?
* Data is now component based and scalable. 
* It is NOT a framework.

* We use JSX to write React components. It's sort of a templating style language to write markup and Javascript

Simple use of Hooks
```
import React, {useState} from 'react';
import './App.css';

function App() {
  const [isBulbOn, setIsBulbOn] = useState(false)
  setTimeout(() => {
    setIsBulbOn(!isBulbOn)
  }, 1000)
  return (
    <div className="App">
      The lightbulb is {isBulbOn ? 'On' : 'Off'}
    </div>
  );
}

export default App;
```
Another exmaple
```
import React, {useState} from 'react';
import './App.css';

const App = () => {

  const[catOn, setCatOn] = useState(false)

  return(
    <div onClick={() => {setCatOn(!catOn)}}>
        <p>{catOn === false ? "Joe" : "frank"}</p>
    </div>
  )
}

export default App;

```
### Composing React components and passing Data Via Props  -  Second part of Intro to React
Exmaple

```
import React, {useState} from 'react';
import './App.css';

const App = () => {

  const[count, setCount] = useState(0)

  const addOne = () => {
    setCount(count + 1)
  }

  const multiply = () => {
    setCount(count * 5)
  }
  return(
    <div>
      <p>The count is {count}</p>
      <button onClick={addOne}>Add By 1</button>
      <button onClick={multiply}>Multiply by 5</button>
      <button onClick={() => setCount(0)}>Reset</button>
    </div>
  )
 } 
 export default App
 ```

Another example
```
import React, {useState} from 'react';
import './App.css';
import './styles.css'

const App = () => {

  const[color, setColor] = useState('Red');

  const styles = {
    color: "E62739"
  }
  
  const handleSetColor = (color) => {
    setColor(color);
  }

  if (color === "Green") {
    styles.color = "#57e278";
  } else if (color === "Pink") {
    styles.color = "#e257c1";
  } else if (color === "Blue") {
    styles.color = "#2e6cd3";
  } else if (color === "Orange") {
    styles.color = "#FFA500";
  } else {
    // red
    styles.color = "#E62739";
  }

  return (
    <div className="counter">
      <p>
        {`color: `}
        <span className="picker-choice">
          {color}
        </span>
      </p>
      <div className="button_container">
        <button className="color_button" onClick={() => {handleSetColor('Blue')}}>
          <span role="img" aria-lable="blue heart">
              💙
          </span>
        </button>
        <button className="color_button" onClick={() => {handleSetColor('Green')}}>
          <span role="img" aria-lable="green heart">
              💚 
          </span>
        </button>
        <button className="color_button" onClick={() => {handleSetColor('Red')}}>
          <span role="img" aria-lable="red heart">
              💗
          </span>
        </button>
        <button className="color_button">
          <span role="img" aria-lable="pink heart">
              💗
          </span>
        </button>

      </div>
    </div>
  )
  export default App;
}
```

### Component Side Effects  -  Third part of Intro to React

#### Side Effects definition: 
It is a general concept about behaviours of functions. A function is said to have side effect if it trys to modify anything outside its body. For example, if it modidifies a global variable, then it is a side effect. If it makes a network call, it is a side effect as well.

Example
```
function App() {

  const[count, setCount] = useState(0)
  const[isHappy, setIsHappy] = useState(false)



  // This is used when the elements outputed have changed since the previous run of the
  // App function.  As soon as the page repaints, the useEffect is executed

  useEffect(() => {
    console.log('you see me every time React finishes with the DOM')
  });

  return(
    <div>
      <h1>Count: {count}</h1>
      {
        isHappy 
          ? <h3>So Happy!</h3>
          : <h3> Not happy at all...</h3>
      }
      <button onClick={(e) => setCount(count + 1)}>Increment Count</button>
      <button onClick={(e) => setIsHappy(true)}>Make Happy</button>
      <button onClick={(e) => setIsHappy(false)}>Make Unappy</button>
    </div>
  )
}
export default App;
```
#### Syncing Effects to changes in state and props

```
function User(props){
  const[color, setColor] = useState("red");

  useEffect(() => {
    console.log('first render and all subsequent renders')
  })
  // This will only run once at the first paint.
  useEffect(() => {
    console.log('first render')
  }, [])
  // This will run if color, in the array, is changed.
  // color is grabbed from the useState
  useEffect(() => {
    console.log('first render color')
  }, [color])


  return(
    <div style={{color, border: `4px solid ${color}`, padding: "8px"}}>
      <div>User id is {props.id}</div>
      <div>User is dressed in {color}</div>
      <button onClick={e => setColor("red")}>Red</button>
      <button onClick={e => setColor("green")}>Green</button>
    </div>
  )
}

function App() {
  const[number, setNumber] = useState(4)


  return(
    <div>
      {number < 4 && <User id={number}/>}
      <button onClick={e => setNumber(number + 1)}>Increment</button>
      <button onClick={e => setNumber(1)}>Reset</button>

    </div>
  )
}
```
Another example.  This is a movie list app.  It consists of three parts: App.js, MovieList, and MovieCard.  It uses Axios along with useEffect.  The API is called through useEffect with Axios inside of that.  This is from a guided project. 

App.js
```
import React from 'react'
import './App.css';
import MovieList from './components/MoveList'
import './style.css'


function App() {
  return(
    <div className="App">
    <div className="logo_container">
      <h1>API</h1>
    </div>
    <MovieList />
  </div>
  )
}

export default App;
```


MovieList.js
```
import React, {useState, useEffect} from 'react';
import axios from 'axios'
import MovieCard from './MovieCard';

const MovieList = () => {

    // setting the reponse to the API in an array
    const[films, setFilms] = useState([])

    useEffect(() => {
        axios.get(`https://ghibliapi.herokuapp.com/films`)
        .then(response => {
            console.log(response.data)
            setFilms(response.data)
        })
        .catch(error => {
            console.log(error)
        })
    }, []) // [] empty dependency array. useEffect will only run once if empty. 
           // otherwise could be infinite loop. this is a second argument

    return(
        <div className="film">
            {films.map(film => {
                return (
                    <MovieCard  key={film.id}
                                title={film.title}
                                description={film.description}
                                release={film.release_date}
                                director={film.director}
                        />
                )
            })}
            
        </div>
    )
}

export default MovieList;

// Notes
/*
    Dependency Array: It is a second parameter used inside useEffect
    Helps stop the API from reaching its limit. Prevents repeated calls

*/

```

MovieCard.js
```
import React from 'react';

const MovieCard = (props) => {
    return(
        <div className="film-list"
            key="{props.film.id}">
                <h2>Film title: {props.title}</h2>
                <p>Description: {props.description}</p>
                <div className="bottom">
                    <p>Director: {props.director}</p>
                    <p>Release date: {props.release_date}</p>
                </div>
                
        </div>
    )
}

export default MovieCard;

```
