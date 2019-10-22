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
