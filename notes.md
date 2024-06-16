# project createtion
1. There are many ways to cretae a react js project
2. Here I am using Vite
    - It takes less time to install
    - there will be no extra things

## start react project will VITE
``` 
npm create vite@latest
```
2. enter project name
3. select the tech --> ReactJs
4. GO inside the newly created folder
```
5. npm install
6. npm run dev
```

# evaluated expresstion

```
function APP(){
    const name = "sumit";

    return (
        <>
            i am sumit {name}.
        </>
    )
}

```
1. {name} -- is a evaluated expression. Here you can't write javascript code in the blocks. Only it can contains the final out coume

# onclick

```
function App() {
  const GenarateRandDtaa =() =>{
    alert("I am called");
  }
  return (
    <>
    <h1>I am learning data</h1>
    <button onClick={GenarateRandDtaa}>Click</button>
    </>
  )
}
```

# Hooks 
You can do what ever you want with the variables but when you need to show the data in the UI, we need to perform this operation using Hooks , There are multiple Hooks

## 1. useState
1. it is responsibe for propogate the value into the ui or dom.
2. How to use declare the use state
```
import { useState } from "react";

function App() {
  let [counter, setCounter] = useState(15);
  
  const GenarateRandDtaa = () =>{
    setCounter(counter+1);
  }
  const DeleteRandDtaa = () =>{
    setCounter(counter-1);
  }
  return (
    <>
    <h1>I am learning data</h1>
    <button onClick={GenarateRandDtaa}>this button is clicked for {counter}</button>
    <button onClick={DeleteRandDtaa}>this button is clicked for {counter}</button>
    </> 
  )
}
```
3. `let [counter, setCounter] = useState(15);`
    - `[counter, setCounter]`
        - `counter` is the variable name and 15 is the default value which is hoing to be assigned in the counter valiable.
        - `setCounter` : is function, by using this we are going to assign the value dynamically. 
        - `useState(15)` : 15 is the default value, we can assign an empty array or object or boolean as default value. "useState": will return array as output so that at the left hand side we are taking as array.
4. we can access the counter variable in function
as well

### 1.1 useState : setter method
```
function App() {
  let [counter, setCounter] = useState(15);

  const AddNum =() =>{
    setCounter(counter + 1);
    setCounter(counter + 1);
    setCounter(counter + 1);
    setCounter(counter + 1);
  }
  return (
    <>
    <h1>I am learning data</h1>
    <button onClick={AddNum}>Click {counter}</button>
    </>
  )
}
```
1. by looking the above code we can asume it is going to return the 15+1+1+1+1=19, but actually it is going to return me 16. The "react fiber" is send tasks as batch, becuse of the "diffing algo" task it can consider it as single unique task.
2. However if there is case you need to do it, here is the solution
```
  setCounter(PrevCounter => PrevCounter + 1);
  setCounter(PrevCounter => PrevCounter + 1);
  setCounter(PrevCounter => PrevCounter + 1);
  setCounter(PrevCounter => PrevCounter + 1);
```
`PrevCounter` : this holds the previous value after 1 operation

### 1.2 useState + onclick

```
  let [color, setColor] = useState("green);

  return (
    <>
    <button onClick={()=> setColor("red)}>Click {color}</button>
    </>
  )
```





# props
it is used for component reusability, we can create a component and we pass the dynamic data using props, as a return it will return us a populated components.

1. create a component at 'src/components/cards/basiccard.jsx'
```
import Button from 'react-bootstrap/Button';
import Card from 'react-bootstrap/Card';
function BasicCard(props) {
  return (
    <Card style={{ width: '18rem' }}>
      <Card.Img variant="top" src="holder.js/100px180" />
      <Card.Body>
        <Card.Title>{props.name || "sathi"} (age : {props.data_obj.age})</Card.Title>
        <Card.Text>
          Some quick example text to build on the card title and make up the
          bulk of the card's content.
        </Card.Text>
        <Button variant="primary">Go somewhere</Button>
      </Card.Body>
    </Card>
  );
}

export default BasicCard;
```

2. pass the dynamic data from the the jsx.file
```
import { useState } from "react";
// Import our custom CSS

import BasicCard from "./components/cards/basic";

function App() {
    let some_data = [1,2,3];
    let more_data = {
      "name":"sumit",
      "age":25,
      "contact":"8617811488"
    };
  
  return (
    <div className="container">
      <h1>I am learning data</h1>
      <BasicCard name="sumit" arr={some_data} data_obj={more_data}/>
    </div> 
  )
}

export default App

```
3. `{props.name || "sathi"}`:
  - let someone has not passed the name as props, "||" it check and return default value "sathi", if someone as not passed the "name" props

# React Fiber
The goal of React Fiber is to increase its suitability for areas like animation, layout, and gestures. Its headline feature is incremental rendering: the ability to split rendering work into chunks and spread it out over multiple frames.

Other key features include the ability to pause, abort, or reuse work as new updates come in; the ability to assign priority to different types of updates; and new concurrency primitives.

`Hydration` : some times at the time of loading the the webcontent and buttons arrived but the javascript is not ready for the action. Button are non clickable. This is called hydration.

`reconciliation`: The algorithm React uses to diff one tree with another to determine which parts need to be changed.

# what is virtual dom
Reconciliation is the algorithm behind what is popularly understood as the "virtual DOM." A high-level description goes something like this: when you render a React application, a tree of nodes that describes the app is generated and saved in memory. This tree is then flushed to the rendering environment — for example, in the case of a browser application, it's translated to a set of DOM operations. When the app is updated (usually via setState), a new tree is generated. The new tree is diffed with the previous tree to compute which operations are needed to update the rendered app.


# Bootstrap
```
npm install react-bootstrap bootstrap
```
2. Go to main/index.js and paste it at he abouve somewhere
```
// Importing the Bootstrap CSS
import 'bootstrap/dist/css/bootstrap.min.css';
```
3. Now we are ready to use the bootstrap



# InStall FontAwasome Icons

1. install
```
npm i --save @fortawesome/fontawesome-svg-core
npm i --save @fortawesome/free-solid-svg-icons
npm i --save @fortawesome/free-regular-svg-icons
npm i --save @fortawesome/free-brands-svg-icons
npm i --save @fortawesome/react-fontawesome@latest
```
2. HOw to use it
```
import { FontAwesomeIcon } from '@fortawesome/react-fontawesome'


<p>hi <FontAwesomeIcon className='icon' icon="fa-solid fa-house" style={{color: "rgb(145 225 255)",}} /></p>
```