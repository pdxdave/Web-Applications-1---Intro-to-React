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


