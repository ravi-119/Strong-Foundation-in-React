# Understanding React, JSX, and Custom Rendering Concepts

This guide will help you build a strong conceptual foundation in React, JSX, and how rendering works—both with React and with a custom implementation.

---

## 1. What is React?

- **React** is a JavaScript library for building user interfaces, especially single-page applications.
- It uses a **component-based architecture**, where each part of the UI is a reusable component.
- React efficiently updates and renders just the right components when your data changes, using a concept called the **Virtual DOM**.

---

## 2. What is JSX?

- **JSX (JavaScript XML)** is a syntax extension for JavaScript, used with React to describe what the UI should look like.
- JSX looks similar to HTML, but it is actually syntactic sugar for `React.createElement` calls.
- JSX makes code more readable and easier to write.

**Example:**
```jsx
const element = <h1>Hello, world!</h1>;
// This is transformed to:
const element = React.createElement('h1', null, 'Hello, world!');
```

---

## 3. React Components

- **Functional Components:** JavaScript functions that return JSX.
- **Class Components:** ES6 classes that extend `React.Component` (less common in modern React).
- Components can accept **props** (inputs) and manage **state** (internal data).

**Example:**
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

---

## 4. Rendering in React

- React uses `ReactDOM.createRoot(...).render(<App />)` to render the root component into the DOM.
- The component tree starts from the root and branches out to all child components.
- React handles updates efficiently using the Virtual DOM.

**Example:**
```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';

ReactDOM.createRoot(document.getElementById('root')).render(<App />);
```

---

## 5. How React.createElement Works

- JSX is compiled to `React.createElement(type, props, ...children)`.
- This function returns a plain JavaScript object describing the element.

**Example:**
```jsx
const link = <a href="https://google.com">Visit Google</a>;
// Compiles to:
const link = React.createElement('a', { href: 'https://google.com' }, 'Visit Google');
```

---

## 6. Custom Rendering (How React Works Internally)

You can create a simple custom renderer to understand how React might work under the hood.

**Example:**
```javascript
function customRender(reactElement, container) {
    const domElement = document.createElement(reactElement.type);
    domElement.innerHTML = reactElement.children;
    for (const prop in reactElement.props) {
        if (prop === 'children') continue;
        domElement.setAttribute(prop, reactElement.props[prop]);
    }
    container.appendChild(domElement);
}

const reactElement = {
    type: 'a',
    props: {
        href: 'https://google.com',
        target: '_blank'
    },
    children: 'Click me to visit google'
};

const mainContainer = document.querySelector('#root');
customRender(reactElement, mainContainer);
```
- This code creates a DOM element based on a plain object structure (similar to what `React.createElement` returns).
- It sets attributes and appends the element to the DOM.

---

## 7. Key Concepts Illustrated in the Provided Code

- **JSX vs. React.createElement:**  
  JSX is just a more readable way to write what `React.createElement` does.
- **Rendering:**  
  ReactDOM (or a custom renderer) takes the element description and turns it into real DOM nodes.
- **Component Structure:**  
  Components can be composed and reused, making code modular and maintainable.
- **Props and State:**  
  Props are inputs to components; state is internal data that can change over time.

---

## 8. Example: Combining Concepts

**main.jsx**
```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'

function MyApp() {
    return (
        <div>
            <h1>Custom App | chai</h1>
        </div>
    )
}

const anotherElement = (
    <a href="https://google.com" target='_blank'>Visit google</a>
)

const reactElement = React.createElement(
    'a',
    { href: 'https://google.com', target: '_blank' },
    'click me to visit google',
    anotherElement
)

ReactDOM.createRoot(document.getElementById('root')).render(
    reactElement
)
```
- This shows how you can use both JSX and `React.createElement` to create elements.
- You can nest elements and pass them as children.

---

## 9. Summary Table

| Concept                | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| JSX                    | HTML-like syntax for describing UI in JavaScript                            |
| React.createElement    | Function that creates a plain object representing a DOM node                |
| Functional Component   | Function returning JSX                                                      |
| Rendering              | Turning React elements/components into real DOM nodes                       |
| Custom Renderer        | Manual process of converting element objects to DOM (for learning purposes) |
| Props                  | Data passed to components                                                   |
| State                  | Internal, changeable data in components                                     |

---

## 10. Conclusion

- React abstracts away manual DOM manipulation, making UI development declarative and efficient.
- JSX improves readability, but understanding how it compiles to `React.createElement` helps you grasp React’s internals.
- Building a custom renderer deepens your understanding of how React interacts with the DOM.
- Mastering these concepts is key to becoming proficient in React development.

---

# Concept of Evaluated Props in React

In React, **evaluated props** refer to the use of JavaScript expressions inside JSX to dynamically set the values of props or content. These expressions are evaluated at runtime, allowing you to inject variables, function results, or any valid JavaScript expression into your UI.

---

## Example Explained

```jsx
function App() {
  const username = "chai aur code";

  return (
    <>
      <Chai />
      <h1>chai aur react {username}</h1>
      <p>test para</p>
    </>
  );
}
```

### Breakdown

- **`const username = "chai aur code";`**  
  A variable is declared in the component.

- **`<h1>chai aur react {username}</h1>`**  
  The `{username}` part is an evaluated prop.  
  - The curly braces `{}` allow you to embed any JavaScript expression inside JSX.
  - Here, the value of `username` is evaluated and inserted into the rendered output.
  - The final output will be:  
    `<h1>chai aur react chai aur code</h1>`

- **`<Chai />`**  
  This renders another component called `Chai`.

---

## Key Points

- **Curly braces `{}` in JSX** are used to evaluate JavaScript expressions.
- You can use variables, function calls, arithmetic, or any valid expression inside `{}`.
- This makes your UI dynamic and responsive to data changes.

---

## Summary

Evaluated props in React allow you to inject dynamic values into your components using curly braces `{}` in JSX. This is a core feature that makes React powerful and flexible for building UIs.




