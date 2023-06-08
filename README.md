# React-JS
# Header Files to be imported:

```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
```

# Create Root API in react18:

```jsx
const root = ReactDOM.createRoot(document.getElementById("root"))
root.render(COMPONENT)
```

# Components:
1. Reusable
2. Component (function name) should start from capital letter
3. It should return only single element (multiple elements wrap in single parent element(Fragments--> <></>)).

```jsx
export default function Card() {
    return (
        <div>
        //ELEMENTS
        <div/>
    )
}
```

# Calling Component in main file: 

1. Import it.
2. Syntax(for static components):
```jsx
<COMPONENT_NAME/>
```

# JS IN JSX

```jsx
function App() {
    const firstName = "Joe"
    const lastName = "Schmoe"
    
    return (
        <h1>Hello {firstName} {lastName}!</h1>
    )
}
```
# Props:
1. Immutable
2. Fetch information from outside
3. Basically like a objects(with properties) or like functions (where prop is parameter).
4. React props are read only.

**METHOD 1:**
```jsx
//item is a prop (data is stored in JSON file and we are extracting it)
export default function Card(props) {
    console.log(props)
    return(
        <div className="card">
        <img src={props.img} className="card_img"></img>
        <div className="stats">
        <span>{props.rating}</span>
        <span> {props.location }</span>
        </div>
        <div className="card_name">
            <h3>{props.title}</h3>
            <h4>Rs.{props.price} /per night</h4>
        </div>
        </div>
    )
}

------------------------------------------------------------------
const cards =data.map(item => {
   return (
     <Card 
     key = {item.id}     //key should be unique
     img = {item.img}
     rating = {item.rating}
     location ={item.location}
     name = {item.title}
     price= {item.price} 
     />

```

**METHOD 2 (ES6 METHOD):**

Else everything same as method 1

```jsx
export default function App() {
    const cards = data.map(item => {
        return (
            <Card
                key={item.id}
                {...item}  
            />
        )
    })   

```



**METHOD 3 (Pass Objects as props):**

**NOTE:** Object property name should be same as in JSON file (from where we are importing data)

```jsx

//Syntax: props.objectName.properyName

export default function Card(props) {
    console.log(props)
    return(
        <div className="card">
        <img src={props.item.img} className="card_img"></img>
        <div className="stats">
        <span>{props.item.rating}</span>
        <span> {props.item.location }</span>
        </div>
        <div className="card_name">
            <h3>{props.item.title}</h3>
            <h4>Rs.{props.item.price} /per night</h4>
        </div>
        </div>
    )
}

------------------------------------------------------------------

export default function App() {
    const cards = data.map(item => {
        return (
            <Card
                key={item.id}
                item={item}
            />
        )
    }
)



```


**Calling dynamic component in Main file:**
```jsx
{COMPONENT_NAME}

//example:
<div className="cards_display">
      {cards}
</div>
```

**Using maps for props:**

```jsx
export default function App() {
    const jokeElements = jokesData.map(joke => {
        return <Joke setup={joke.setup} punchline={joke.punchline} />
    })
    return (
        <div>
            {jokeElements}
        </div>
    )
}
```

# Note:
**Move images to public folder**

# Difference between Props and State
1. Components receive data from outside with props, whereas they can create and manage their own data with state.

2. Props are used to pass data, whereas state is for managing data.

3. Data from props is read-only, and cannot be modified by a component that is receiving it from outside.

4. State data can be modified by its own component, but is private (cannot be accessed from outside)
Props can only be passed from parent component to child (unidirectional flow).

5. Modifying state should happen with the setState ( ) method.
