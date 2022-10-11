0) Project Overview:
- The final goal of this project is to create an interactive typewriter in react. There will be two major components in the application: the keyboard and the text display. The keyboard will be a live version of the user keyboard whose keys will "light up" when a user types a letter. The text display will be a simple component that shows what the user has typed.
- In creating this application we will practice handling user events, updating the react component states, passing data through props, and composing react component structures.
- Note: This assignment writeup will provide a high level overview of what to implement and where. How you decide to implement the functionality is up to you. Any repo that can be run with "npm start" and has the intended functionality working will be accepted. Hints, suggestions and certain necessary pieces of code will be provided.

1) Project Setup:
- Create a new github repo called react-typewriter:
- Clone the repo to your computer and add the link to populi
- cd into the react-typewriter directory
- Run 'npx create-react-app .' to initialize react in the repository
- Run 'npm start' after react has finished installing
- If the above worked properly, you should see the react start page on localhost:3000
- Open App.js and replace the file with the following code:

--START--

import { useState, useRef, useEffect } from "react";
import "./App.css";

const App = () => {
return (
<div className="App-header">
<KeyboardGrid/>
</div>
);
}

const KeyboardGrid = (props) => {

const keyBoardArr = [
[
{ letter: "`", isPressed: false },
{ letter: "1", isPressed: false },
{ letter: "2", isPressed: false },
{ letter: "3", isPressed: false },
{ letter: "4", isPressed: false },
{ letter: "5", isPressed: false },
{ letter: "6", isPressed: false },
{ letter: "7", isPressed: false },
{ letter: "8", isPressed: false },
{ letter: "9", isPressed: false },
{ letter: "0", isPressed: false },
{ letter: "-", isPressed: false },
{ letter: "=", isPressed: false },
{ letter: "Backspace", isPressed: false }
],
[
{ letter: "Tab", isPressed: false },
{ letter: "Q", isPressed: false },
{ letter: "W", isPressed: false },
{ letter: "E", isPressed: false },
{ letter: "R", isPressed: false },
{ letter: "T", isPressed: false },
{ letter: "Y", isPressed: false },
{ letter: "U", isPressed: false },
{ letter: "I", isPressed: false },
{ letter: "O", isPressed: false },
{ letter: "P", isPressed: false },
{ letter: "[", isPressed: false },
{ letter: "]", isPressed: false },
{ letter: "\\", isPressed: false },
],
[
{ letter: "CapsLock", isPressed: false },
{ letter: "A", isPressed: false },
{ letter: "S", isPressed: false },
{ letter: "D", isPressed: false },
{ letter: "F", isPressed: false },
{ letter: "G", isPressed: false },
{ letter: "H", isPressed: false },
{ letter: "J", isPressed: false },
{ letter: "K", isPressed: false },
{ letter: "L", isPressed: false },
{ letter: ";", isPressed: false },
{ letter: "'", isPressed: false },
{ letter: "Enter", isPressed: false }
],
[
{ letter: "Shift", isPressed: false },
{ letter: "Z", isPressed: false },
{ letter: "X", isPressed: false },
{ letter: "C", isPressed: false },
{ letter: "V", isPressed: false },
{ letter: "B", isPressed: false },
{ letter: "N", isPressed: false },
{ letter: "M", isPressed: false },
{ letter: ",", isPressed: false },
{ letter: ".", isPressed: false },
{ letter: "/", isPressed: false },
{ letter: "Shift", isPressed: false },
],
[
{ letter: " ", isPressed: false }
]
];

const [keyRows, setKeyRows] = useState(keyBoardArr);

const handleKeyDown = (event) => {
console.log(event.key)
};

const handleKeyUp = (event) => {
console.log(event.key)
};


const ref = useRef(null);

useEffect(() => {
ref.current.focus();
}, []);

return (
<div
className="Keyboard-grid"
ref={ref}
tabIndex={-1}
onKeyDown={handleKeyDown}
onKeyUp={handleKeyUp}
>

</div>
);
};

export default App;

--END--

- Open App.css and replace the file with the following code:

--START--

.App-header {
background-color: #282c34;
min-height: 100vh;
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
font-size: calc(10px + 2vmin);
color: white;
}

.Keyboard-key {
display: flex;
justify-content: center;
align-items: center;
flex-grow: 1;
border-radius: 10%;
padding: 7px 18px;
margin: 3px;
height: 35px;
background-color: slategray;
color: white
}

.Keyboard-row {

}

.Keyboard-grid {

}

--END--

2) Displaying the Keyboard:
- Create a new react component called <KeyboardRow/>
- The enclosing div of <KeyboardRow/> should be assigned the class name of "Keyboard-row"
- In the JSX of <KeyboardGrid/>, map through keyRows and return a <KeyboardRow/> component in the .map callback function. Name the first parameter of the .map callback function "keyRow" and pass keyRow into the <KeyboardRow/> component as a prop.
- Create a new react component called <KeyboardKey/> 
- The enclosing div of <KeyboardKey/> should be assigned the class name of "Keyboard-key"
- In the JSX of <KeyboardRow/>, map through the keyRow prop and return a <KeyboardKey/> component in the .map callback function. Name the first parameter of the .map callback function "keyObject" and pass keyObject into the <KeyboardKey/> component as a prop. 
- In the JSX of <KeyboardKey/>, display the value {props.keyObject.letter}
- Add flexbox properties to Keyboard-row and/or Keyboard-grid to display the keyboard as shown in the screenshot# react-Typewriter

