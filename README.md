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
Another exmaple

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
