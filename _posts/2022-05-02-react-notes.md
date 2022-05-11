---
layout: post
title: React Notes [5/5/22]
---

# Week 6 Notes - React

```javascript
ReactDOM.render(
    <ul><li>Thing 1</li><li>Thing 2</li></ul>,
    document.getElementById("root")
)
```


- JSX returns elements for React to run 
- use create react app (need node installed and npm; on local machine)
- **props** help us make a component more reusable

- What does the `.map()` array method do?
    - Returns a new array. Whatever gets returned from the callback function provided is placed at the same index in the new array.

- in react **conditions** look like  
- ```{props.openSpots === 0 && <div className="card--badge">SOLD OUT</div>}```

- event listeners in react: https://reactjs.org/docs/events.html#mouse-events


- **props versus states**
    - can't change props (within the body of the function) states are managed by the component and should be changed
    - When would you want to use props instead of state?
        - Anytime you want to pass data into a component so that component can determine what will get displayed on the screen.
    -  When would you want to use state instead of props?
        - Anytime you want a component to maintain some values from within the component. (And "remember" those values even when React re-renders the component)


- use **callback functions** to update state: 
```javascript 
function add() {
        setCount(prevCount => prevCount + 1)}
```
> event listeners have to be on native objects (ie in order to set a state on a child component)




- example box challenge from scrimba: (switch colors when clicked)
```javascript 
import React from "react"
import boxes from "./boxes"
import Box from "./Box"

export default function App() {
    const [squares, setSquares] = React.useState(boxes)
    
    function toggle(id) {
        setSquares(prevSquares => {
            return prevSquares.map((square) => {
                return square.id === id ? {...square, on: !square.on} : square
            })
        })
    }
    
    const squareElements = squares.map(square => (
        <Box 
            key={square.id} 
            id={square.id}
            on={square.on} 
            toggle={toggle}
        />
    ))
    
    return (
        <main>
            {squareElements}
        </main>
    )

export default function Box(props) {
    const styles = {
        backgroundColor: props.on ? "#222222" : "transparent"
    }
    
    return (
        <div 
            style={styles} 
            className="box"
            onClick={()=>props.toggle(props.id)}
        >
        </div>
    )
}
```

- **controlled inputs in forms: value={formData.firstName}**

- example form with checkbox:

```javascript
export default function Form() {
    const [formData, setFormData] = React.useState(
        {
            firstName: "", 
            lastName: "", 
            email: "", 
            comments: "", 
            isFriendly: true
        }
    )
    
    function handleChange(event) {
        const {name, value, type, checked} = event.target
        setFormData(prevFormData => {
            return {
                ...prevFormData,
                [name]: type === "checkbox" ? checked : value
            }
        })
    }
    
    return (
        <form>
            <input
                type="text"
                placeholder="First Name"
                onChange={handleChange}
                name="firstName"
                value={formData.firstName}
            />
            <input
                type="text"
                placeholder="Last Name"
                onChange={handleChange}
                name="lastName"
                value={formData.lastName}
            />
            <input
                type="email"
                placeholder="Email"
                onChange={handleChange}
                name="email"
                value={formData.email}
            />
            <textarea 
                value={formData.comments}
                placeholder="Comments"
                onChange={handleChange}
                name="comments"
            />
            <input 
                type="checkbox" 
                id="isFriendly" 
                checked={formData.isFriendly}
                onChange={handleChange}
                name="isFriendly"
            />
            <label htmlFor="isFriendly">Are you friendly?</label>
            <br />
        </form>
    )
}
```

- for submit include preventDefault() so it does not rerender the page, etc
 function handleSubmit(event) {
        event.preventDefault()
        submitToApi(formData)
    }
    

- What is a "side effect" in React? What are some examples?
	- Any code that affects an outside system.
	- local storage, API, websockets, two states to keep in sync

- What is NOT a "side effect" in React? Examples?
	- Anything that React is in charge of.
	- Maintaining state, keeping the UI in sync with the data, render DOM elements
- When does React run your useEffect function? When does it NOT run
   the effect function?
	- As soon as the component loads (first render)
	- On every re-render of the component (assuming no dependencies array)
	- Will NOT run the effect when the values of the dependencies in the array stay the same between renders
- How would you explain what the "dependecies array" is?
	- Second paramter to the useEffect function
	- A way for React to know whether it should re-run the effect function

- making API calls in React
	- use effect hook (https://reactjs.org/docs/hooks-effect.html)

```javascript
import React from "react"

export default function App() {
    const [starWarsData, setStarWarsData] = React.useState({})
    const [count, setCount] = React.useState(1)
    
    /**
     * Challenge: Combine `count` with the request URL
     * so pressing the "Get Next Character" button will
     * get a new character from the Star Wars API.
     * Remember: don't forget to consider the dependencies
     * array!
     */
    
    React.useEffect(function() {
        console.log("Effect ran")
        fetch(`https://swapi.dev/api/people/${count}`)
            .then(res => res.json())
            .then(data => setStarWarsData(data))
    }, [count])
    
    return (
        <div>
            <h2>The count is {count}</h2>
            <button onClick={() => setCount(prevCount => prevCount + 1)}>Get Next Character</button>
            <pre>{JSON.stringify(starWarsData, null, 2)}</pre>
        </div>
    )
}
```

- window tracker (scrimba) removeEventListener example
```javascript

import React from "react"

export default function WindowTracker() {
    
    const [windowWidth, setWindowWidth] = React.useState(window.innerWidth)
    
    React.useEffect(() => {
        function watchWidth() {
            console.log("Setting up...")
            setWindowWidth(window.innerWidth)
        }
        
        window.addEventListener("resize", watchWidth)
        
        return function() {
            console.log("Cleaning up...")
            window.removeEventListener("resize", watchWidth)
        }
    }, [])
    
    return (
        <h1>Window width: {windowWidth}</h1>
    )
}
```
