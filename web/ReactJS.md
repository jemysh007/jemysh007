# ReactJS Cheat Sheet

This cheat sheet provides a quick reference to common ReactJS concepts, components, hooks, and methods.

## Table of Contents

1. [Introduction](#introduction)
2. [JSX](#jsx)
3. [Components](#components)
4. [Props](#props)
5. [State](#state)
6. [Lifecycle Methods](#lifecycle-methods)
7. [Hooks](#hooks)
8. [Event Handling](#event-handling)
9. [Conditional Rendering](#conditional-rendering)
10. [Lists and Keys](#lists-and-keys)
11. [Forms](#forms)
12. [Context API](#context-api)
13. [React Router](#react-router)
14. [Higher-Order Components (HOC)](#higher-order-components-hoc)
15. [Error Boundaries](#error-boundaries)
16. [Best Practices](#best-practices)

---

## Introduction

ReactJS is a JavaScript library for building user interfaces. It allows developers to create reusable UI components.

---

## JSX

JSX is a syntax extension for JavaScript that looks similar to XML or HTML.

### Basic JSX

```jsx
// src/App.js
const element = <h1>Hello, world!</h1>;
```

### Embedding Expressions

```jsx
// src/App.js
const name = 'John';
const element = <h1>Hello, {name}!</h1>;
```

### JSX Attributes

```jsx
// src/App.js
const element = <img src={user.avatarUrl} alt={user.name} />;
```

### JSX Children

```jsx
// src/App.js
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

---

## Components

Components let you split the UI into independent, reusable pieces.

### Function Component

Function components are simple functions that return JSX.

```jsx
// src/components/Welcome.js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

### Class Component

Class components are ES6 classes that extend from `React.Component` and have a `render` method.

```jsx
// src/components/Welcome.js
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

---

## Props

Props are read-only attributes used to pass data from parent to child components.

### Using Props

Props are passed to components via HTML attributes.

```jsx
// src/App.js
import Welcome from './components/Welcome';

function App() {
  return <Welcome name="Sara" />;
}

export default App;
```

---

## State

State is a built-in object that stores property values that belong to the component.

### Using State in Class Component

State is managed within the component and can change over time.

```jsx
// src/components/Clock.js
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = { date: new Date() };
  }

  render() {
    return <h2>It is {this.state.date.toLocaleTimeString()}.</h2>;
  }
}
```

### Using State in Function Component with Hooks

Hooks like `useState` allow you to add state to function components.

```jsx
// src/components/Counter.js
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}

export default Counter;
```

---

## Lifecycle Methods

Lifecycle methods are special methods in class components that run at different points in a component's lifecycle.

### Common Lifecycle Methods

- `componentDidMount()`: Called after the component is mounted.
- `componentDidUpdate(prevProps, prevState)`: Called after the component is updated.
- `componentWillUnmount()`: Called before the component is unmounted.

Example:

```jsx
// src/components/Clock.js
class Clock extends React.Component {
  componentDidMount() {
    this.timerID = setInterval(() => this.tick(), 1000);
  }

  componentWillUnmount() {
    clearInterval(this.timerID);
  }

  tick() {
    this.setState({
      date: new Date()
    });
  }

  render() {
    return <h2>It is {this.state.date.toLocaleTimeString()}.</h2>;
  }
}
```

---

## Hooks

Hooks let you use state and other React features without writing a class.

### useState

`useState` is a Hook that lets you add state to function components.

```jsx
// src/components/Counter.js
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}

export default Counter;
```

### useEffect

`useEffect` is a Hook that lets you perform side effects in function components.

```jsx
// src/components/Clock.js
import React, { useEffect, useState } from 'react';

function Clock() {
  const [date, setDate] = useState(new Date());

  useEffect(() => {
    const timerID = setInterval(() => setDate(new Date()), 1000);
    return () => clearInterval(timerID);
  }, []);

  return <h2>It is {date.toLocaleTimeString()}.</h2>;
}

export default Clock;
```

### useContext

`useContext` is a Hook that lets you subscribe to React context without introducing nesting.

```jsx
// src/components/MyComponent.js
import React, { useContext } from 'react';
import { MyContext } from '../context/MyContext';

function MyComponent() {
  const value = useContext(MyContext);
  return <div>{value}</div>;
}

export default MyComponent;
```

---

## Event Handling

Handling events in React is similar to handling events in DOM elements.

### Handling Events

Event handlers are passed as props to elements.

```jsx
// src/components/Button.js
function handleClick() {
  console.log('Button clicked');
}

function Button() {
  return <button onClick={handleClick}>Click me</button>;
}

export default Button;
```

### Passing Arguments to Event Handlers

You can pass arguments to event handlers using arrow functions.

```jsx
// src/components/Button.js
function handleClick(id) {
  console.log('Button clicked', id);
}

function Button() {
  return <button onClick={() => handleClick(1)}>Click me</button>;
}

export default Button;
```

---

## Conditional Rendering

Render different UI based on different conditions.

### Using if-else

Use JavaScript `if-else` statements to conditionally render components.

```jsx
// src/components/Greeting.js
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  }
  return <h1>Please sign up.</h1>;
}

export default Greeting;
```

### Using Ternary Operator

Use the ternary operator for inline conditional rendering.

```jsx
// src/components/Greeting.js
const isLoggedIn = true;
const element = isLoggedIn ? <h1>Welcome back!</h1> : <h1>Please sign up.</h1>;
```

### Using Logical && Operator

Use the logical `&&` operator to render a component only if the condition is true.

```jsx
// src/components/Greeting.js
const isLoggedIn = true;
const element = isLoggedIn && <h1>Welcome back!</h1>;
```

---

## Lists and Keys

Rendering lists of data and using keys to identify elements.

### Rendering Lists

Use the `map` function to render lists of elements.

```jsx
// src/components/NumberList.js
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li key={number.toString()}>{number}</li>
);

function NumberList() {
  return <ul>{listItems}</ul>;
}

export default NumberList;
```

### Keys

Keys help React identify which items have changed, are added, or are removed.

```jsx
// src/components/TodoList.js
const todoItems = todos.map((todo) =>
  <li key={todo.id}>{todo.text}</li>
);

function TodoList() {
  return <ul>{todoItems}</ul>;
}

export default TodoList;
```

---

## Forms

Handling form inputs and submission.

### Controlled Components

Controlled components have their form data controlled by React state.

```jsx
// src/components/NameForm.js
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = { value: '' };

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({ value: event.target.value });
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}

export default NameForm;
```

### Handling Multiple Inputs

Use a single change handler to handle multiple form inputs.

```jsx
// src/components/Reservation.js
class Reservation extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      isGoing: true,
      numberOfGuests: 2
    };

    this.handleInputChange = this.handleInputChange.bind(this);
  }

  handleInputChange(event) {
    const target = event.target;
    const value = target.type === 'checkbox' ? target.checked : target.value;
    const name = target.name;

    this.setState({
      [name]: value
    });
  }

  render() {
    return (
      <form>
        <label>
          Is going:
          <input
            name="isGoing"
            type="checkbox"
            checked={this.state.isGoing}
            onChange={this.handleInputChange} />
        </label>
        <br />
        <label>
          Number of guests:
          <input
            name="numberOfGuests"
            type="number"
            value={this.state.numberOfGuests}
            onChange={this.handleInputChange} />
        </label>
      </form>
    );
  }
}

export default Reservation;
```

---

## Context API

Context provides a way to pass data through the component tree without having to pass props down manually at every level.

### Creating Context

Create a context using `React.createContext`.

```jsx
// src/context/MyContext.js
import React from 'react';

const MyContext = React.createContext(defaultValue);

export default MyContext;
```

### Providing Context

Wrap your component tree with a `Provider` and pass the context value.

```jsx
// src/App.js
import React from 'react';
import MyContext from './context/MyContext';
import MyComponent from './components/MyComponent';

function App() {
  return (
    <MyContext.Provider value="Hello, World!">
      <MyComponent />
    </MyContext.Provider>
  );
}

export default App;
```

### Consuming Context

Use the `useContext` Hook to consume the context value.

```jsx
// src/components/MyComponent.js
import React, { useContext } from 'react';
import MyContext from '../context/MyContext';

function MyComponent() {
  const value = useContext(MyContext);
  return <div>{value}</div>;
}

export default MyComponent;
```

---

## React Router

React Router is a library for routing in React applications.

### Basic Setup

Set up routing using `BrowserRouter`, `Route`, and `Switch`.

```jsx
// src/App.js
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
import Home from './components/Home';
import About from './components/About';
import Users from './components/Users';

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/about">
          <About />
        </Route>
        <Route path="/users">
          <Users />
        </Route>
        <Route path="/">
          <Home />
        </Route>
      </Switch>
    </Router>
  );
}

export default App;
```

### Link Component

Use the `Link` component to create navigation links.

```jsx
// src/components/Navbar.js
import { Link } from 'react-router-dom';

function Navbar() {
  return (
    <nav>
      <ul>
        <li>
          <Link to="/">Home</Link>
        </li>
        <li>
          <Link to="/about">About</Link>
        </li>
        <li>
          <Link to="/users">Users</Link>
        </li>
      </ul>
    </nav>
  );
}

export default Navbar;
```

---

## Higher-Order Components (HOC)

A higher-order component is a function that takes a component and returns a new component.

### Example HOC

HOCs are used to add additional functionality to existing components.

```jsx
// src/hoc/withLogging.js
import React from 'react';

function withLogging(WrappedComponent) {
  return class extends React.Component {
    componentDidMount() {
      console.log('Component mounted');
    }

    render() {
      return <WrappedComponent {...this.props} />;
    }
  };
}

export default withLogging;
```

---

## Error Boundaries

Error boundaries are React components that catch JavaScript errors anywhere in their child component tree.

### Creating an Error Boundary

Error boundaries use lifecycle methods to catch errors.

```jsx
// src/components/ErrorBoundary.js
import React from 'react';

class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    console.log(error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }

    return this.props.children; 
  }
}

export default ErrorBoundary;
```

### Using an Error Boundary

Wrap your components with an error boundary to catch errors.

```jsx
// src/App.js
import React from 'react';
import ErrorBoundary from './components/ErrorBoundary';
import MyComponent from './components/MyComponent';

function App() {
  return (
    <ErrorBoundary>
      <MyComponent />
    </ErrorBoundary>
  );
}

export default App;
```

---

## Best Practices

- **Keep components small and focused**: Each component should ideally do one thing.
- **Use functional components and hooks**: Prefer functional components and hooks over class components.
- **Lift state up**: Move state up to the closest common ancestor when multiple components need to share the same state.
- **Use PropTypes**: Validate props using PropTypes to catch bugs early.
- **Avoid inline functions in render**: Define functions outside of the render method to avoid unnecessary re-renders.
- **Use keys in lists**: Always use unique keys when rendering lists to help React identify which items have changed.

---

## Conclusion

This ReactJS cheat sheet covers all the essential ReactJS concepts and techniques you’ll need for building modern web applications. Whether you are creating components, managing state, or handling events, this guide will help you work more effectively with ReactJS.
