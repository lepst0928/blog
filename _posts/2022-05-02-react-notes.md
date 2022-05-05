---
layout: post
title: React Notes [5/5/22]
---

# Week 6 Notes - React

```React
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
``` 
function add() {
        setCount(prevCount => prevCount + 1)}
```
> event listeners have to be on native objects (ie in order to set a state on a child component)




- example box challenge from scrimba: (switch colors when clicked)
```react 
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

```react
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
