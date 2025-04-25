# react-notes

> [!IMPORTANT]
> The purpose of this `readme` is simply to consolidate content I find important or useful to me in some way on my journey to learn **React**, and condense them into a single page for my own personal reference.

### Table of contents
* [About React](#about-react)
	* [Key Features](#key-features)
* [Pre-requisites](#pre-requisites)
	* [Node.js](#node.js)
	* [npm](#npm)
* [Tooling](#tooling)
	* [Vite](#vite)
 	* [ESLint](#eslint)	 
 	* [TypeScript](#typescript)
* [Debugging React + Vite in Visual Studio Code](#debugging-react--vite-in-visual-studio-code)
* [React DOM](#react-dom)
* [React Function Components](#react-function-components)
* [JSX](#jsx)
	* [Transpiling JSX](#transpiling-jsx)
  	* [Variables](#variables)
  	* [Commenting JSX](#commenting-jsx)
 	* [Arrays](#arrays)
  	* [Component Declaration](#component-declaration)
  	* [Event Handlers](#event-handlers)
  	  * [Event Propagation](#event-propagation)
  	  * [Passing Event Handlers as Props](#passing-event-handlers-as-props)
  	  * [Preventing Default Event Behavior](#preventing-default-event-behavior)
  	  * [Props](#props)
	* [Callback Handlers](#callback-handlers) 
  	* [Hooks](#hooks) 
  	  * [State](#state)
* [JavaScript](#javascript)
  
  	  
# About React
Created by Facebook in 2013, [React](https://react.dev/learn) is a JavaScript library used for building single-page applications (SPAs), where the user interacts with the page without needing to reload it.

#### Key Features
- **Virtual DOM** - React creates a virtual representation of the DOM and updates only the parts that change, making rendering faster.
- **JSX** - Combines JavaScript with HTML-like syntax for easier UI coding.

# Pre-requisites
React uses JavaScript and therefore React development on Windows requires Node.js and NPM to be installed.

### Node.js
[Node.js](https://nodejs.org/en/about) an asynchronous event-driven JavaScript runtime for building scalable network applications. Basically, [Node.js](https://www.robinwieruch.de/react-js-windows-setup/) is a JavaScript runtime which makes it possible to run JavaScript outside of the browser.

Check if node has been installed.
```bash
node -v
```

### npm
[npm](https://www.npmjs.com/package/npm) is a JavaScript package manager. Basically, [node package manager (NPM)](https://www.robinwieruch.de/react-js-windows-setup/) is used to install libraries, such as React.js, to your project on the command line.

Check if npm has been installed.
```bash
npm -v
```

# Tooling
### Vite
[Vite](https://vite.dev/) is a fast frontend build tool for web development. It consists of a development server, allowing you to run React applications locally.

> [!TIP]
> **vite** has HMR (Hot Module Replacement) built in. HMR lets you update your React components in real-time without reloading the whole page, while keeping your app’s state.
	 
### ESLint
[ESLint](https://eslint.org/) is a tool that analyzes your code for potential errors, bugs, stylistic issues, and code quality problems

### TypeScript
[TypeScript](https://www.typescriptlang.org/) is a superset of JavaScript that adds Type safety resulting in fewer runtime bugs.

How it works is you write TypeScript code in `.ts` files and TypeScript compiles them to regular JavaScript `.js` files.

React normally uses JavaScript (JSX), but with TypeScript (TSX), you get all the typing benefits without giving up JSX.

File Extensions
- `.jsx` → becomes `.tsx` (for components using JSX + TypeScript)
- `.js` → becomes `.ts` (for plain logic or utility files)

# Debugging React + Vite in Visual Studio Code

**1. Start the Vite Dev Server**
From the terminal in your project root:
```BASH
npm run dev
```
This usually starts the server at `http://localhost:5173`.

**2. Edit the Debug Configuration (`launch.json`)**

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Debug Vite React App",
      "type": "chrome",
      "request": "launch",
      "url": "http://localhost:5173",  		👈 url should match the one Vite uses — 5173 is the default.
      "webRoot": "${workspaceFolder}/src",	👈 webRoot should point to where your React components live (usually /src).
      "sourceMaps": true,
      "skipFiles": ["<node_internals>/**"]
    }
  ]
}
```

**3. Set Breakpoints**

**4. Run and Debug**
Select `Debug Vite React App` in the Run and Debug dropdown list (green arrow).

> [!TIP]
> - Browser extension: Make sure you have the Debugger for Chrome extension (or "JavaScript Debugger" built-in in newer VS Code versions).
> - Correct port: Vite uses 5173 by default — adjust url if your Vite server runs on another port.
> - Environment variables: If you're using .env, make sure VITE_ prefixes are used so Vite exposes them to the client.
> - Want to attach to an already open Chrome? Use `"request": "attach"` with `"urlFilter": "http://localhost:5173/*"`.
>
> 
> Download the React DevTools for a better development experience: `https://react.dev/link/react-devtools` <br>
> *WARNING - installing React DevTools will allow it to read and change all your data on all websites*

# React DOM
In a React application, the root component is typically the top-level component that is rendered into the DOM using `ReactDOM.createRoot(...).render(...)` or `ReactDOM.render(...)` (older versions). It acts as the entry point for the component tree.

By convention, this root component is usually named App.

Typical React Project Structure
```
my-react-app/
├── src/
│   ├── assets/         # Optional: images, fonts, icons, etc.
│   ├── components/     # Your reusable React components
│   ├── App.js          # Root React component
│   ├── App.css         # App-specific styles
│   ├── index.css       # Global styles
│   └── main.jsx        # Entry point - renders App into the DOM
├── .gitignore
├── index.html      	# The main HTML file served by your web server
├── package.json
├── README.md
└── ... (other config files)
```

The main HTML file served by your web server is `index.html`. The React entry point is in `main.jsx`, which renders the root React component `App` into the DOM.

`index.html` is the main HTML file served by your web server. React doesn't generate HTML from scratch — it injects your app into the `<div id="root">`.
```HTML
<!doctype html>
<html lang="en">
  <!-- code removed for brevity -->
  <body>
    <div id="root"></div>   <!-- 👈 React injects your app into the <div id="root"> -->
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

`src/main.jsx` is the entry point of the application. It tells React to render the `App` component inside the `#root` div from `index.html`.
```JSX
import React from 'react';
import ReactDOM from 'react-dom/client'; /* 👈 React DOM is used once to hook React into the native HTML world. */
import './index.css';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <StrictMode>     	{/* 👈 <StrictMode> lets you find common bugs in your components early during development. */}
    <App />		{/* 👈 React renders the App component inside the #root div from index.html */}
  </StrictMode>
);
```

`src/App.js` is the root component of your React component tree.
```JSX
import React from 'react';
import './App.css';

function App() {
  return (
    <div className="App">
      <h1>Welcome to My React App</h1>
    </div>
  );
}

export default App;
```

# React Function Components
**React function component** names must be in Pascal case i.e. where the first letter of each word starts with an upper case letter. This is because React treats components that begin with a lowercase letter as DOM tags (like `<div>`, `<span>`, etc.). So if a component starts with a lower case React will think it's a native HTML tag.

The function of a component runs every time a component is displayed or updated.

```JSX
const title = 'React'; /* 👈 variables outside the function will only get defined once... */

function App() {

  /* 👈 function variables and additional code goes here... */

  return (
      <div>
        <h1>Hello {title}</h1>
      </div>
  );
}

export default App
```

# JSX
JSX (JavaScript XML) is a syntax extension used in React that allows you to write HTML-like code inside JavaScript. JSX expressions are JavaScript expressions embedded within curly braces in JSX, allowing dynamic content. JSX isn't mandatory for React, however it is recommended and is widely used.

### Transpiling JSX
Browsers don't understand JSX so is transpiled to regular JavaScript, using tools like [Babel](https://babeljs.io/docs/#jsx-and-react). The **Babel** plugin `@babel/preset-react` transforms JSX into plain JavaScript by transpiling JSX into `React.createElement()` calls before execution.

```JSX
/* This JSX code... */
const element = <h1>Hello, world!</h1>;

/* Gets transpiled into this JavaScript... */
const element = React.createElement('h1', null, 'Hello, world!');
```

```JSX
/* and this JSX...*/
<div>
  <h1>Title</h1>
  <p>Description</p>
</div>

/* Gets transpiled into this JavaScript... */
React.createElement(
  'div',
  null,
  React.createElement('h1', null, 'Title'),
  React.createElement('p', null, 'Description')
);
```

### Variables
In JSX variables can be embedded using curly braces e.g. `<h1>Hello {title}</h1>`. Everytime it a component is displayed or updated, the variables defined in the function’s body will be re-defined.

> [!TIP]
> To avoid unnecessarily redefining a variable every time a component is displayed or updated, define it outside the function component unless it needs something from within the function component’s body (e.g. parameters).

### Commenting JSX
Wrap JSX code comment text in `{/* */}` e.g. `{/* Hello World! */}`

### Arrays
In [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) the `map()` method of Array instances creates a new array populated with the results of calling a provided function on every element in the calling array.
```JS
const array1 = [1, 4, 9, 16];

// Pass a function to map
const map1 = array1.map((x) => x * 2);

console.log(map1);
// Expected output: Array [2, 8, 18, 32]
```

In **React** the `map()` method tranforms a list by returning JSX for each item. React requires a `key` prop when rendering lists to track which items changed, were added, or removed. This helps React optimize re-renders.

In the example below:
- `users.map(...)` loops through each user.
- For each one, it returns a `UserCard` function component.
- `key={user.id}` helps React track changes to the function component efficiently.

```JSX
const users = [
  { id: 1, name: 'Alice', role: 'Admin' },
  { id: 2, name: 'Bob', role: 'User' },
  { id: 3, name: 'Charlie', role: 'Moderator' }
];

function UserList() {
  return (
    <div>
      {users.map(user => (
        <UserCard key={user.id} name={user.name} role={user.role} />
      ))}
    </div>
  );
}
```

### Component Declaration
Components can be declared using the **standard function** declaration, or as **arrow functions**. With arrow functions parameters are passed inside the parentheses. Callback functions can also be declared using arrow functions. Furthermore, arrow functions that only return a value can remove the return statement. In a **concise body** an implicit return statement is attached.

```JSX
function List() { 			/* 👈 function declaration */
  return (
    <ul>
      {list.map(function (item) {	/* 👈 function declaration */
        return (
          <li key={item.objectID}>{item.author}</li>
        );
      })}
    </ul>
  );
}

const List = () => {			/* 👈 arrow declaration with block body */
  return (
    <ul>
      {list.map((item) => {		/* 👈 arrow declaration with block body */
        return (
          <li key={item.objectID}>{item.author}</li>
        );
      })}
    </ul>
  );
}

const List = () => (			/* 👈 arrow declaration with concise body */
    <ul>
      {list.map((item) => (		/* 👈 arrow declaration with concise body */
          <li key={item.objectID}>{item.author}</li>
        );
      )}
    </ul>
  );

/* a example of a one line arrow function with parameter and concise body */
const incrementVal = (val) => val + 1;
```

### Event Handlers
In HTML we add event handlers on elements using `addEventListener()` method programmatically on a DOM node. React also lets you add event handlers to your JSX, which is essentially a wrapper around the browser’s native event.

Event handler functions:
- Are usually defined inside your components.
- Have names that start with `handle`, followed by the name of the event.

```JSX
const Search = () => {

  const handleChange = (event) => {
    console.log(event.target.value);
  }

  return(
    <div>
      <label htmlFor="search">Search: </label>
      <input id="search" type="text" onChange={handleChange} />
    </div>
  );
};
```
> [!WARNING]
> 
> Functions passed to event handlers must be passed, not called. The difference is subtle.
> 
> In this example `<button onClick={handleClick}>`, the `handleClick` function is passed as an `onClick` event handler, telling React to only call your function when the user clicks the button.
>
> In this example `<button onClick={handleClick()}>`, the brackets in `handleClick()` fires the function immediately during rendering, without any clicks. This is because JavaScript inside the JSX braces `{ and }` executes right away.

#### Event Propagation
Event handlers will also catch events from any child components. An event “bubbles” (or “propagates”) up the component tree.

All events propagate in React except `onScroll`, which only works on the JSX tag you attach it to.

To prevent an event propagating call `e.stopPropagation()`.

#### Passing Event Handlers as Props
In the following example, 
```JSX
function MyButton({ onClick, children }) {
  return (
    <button onClick={onClick}>
      {children}
    </button>
  );
}

function PlayButton({ movieName }) {
  return (
    <MyButton onClick={() => alert('Playing!')}>
      Play
    </MyButton>
  );
}

function UploadButton() {
  return (
    <MyButton onClick={() => alert('Uploading!')}>
      Upload
    </MyButton>
  );
}
```

#### Preventing Default Event Behavior
Some browser events have default behavior associated with them. You can call `e.preventDefault()` on the event object to stop this from happening.
     
### Props
Parent components can pass information to its child components by giving them **props**. Props are the information that you pass to a JSX tag. 

Props are passed in as attributes of a component, and received into the component as one function parameter called `props`. 

> [!IMPORTANT]
> Once a props have been passed into a component they are readonly. They can be consumed, but not changed.

```JSX
export default function Profile() {
  return (
    <Avatar person={{ firstname: 'Jane', surname: 'Masters' }} /* 👈 use “double curlies” to pass a JS object in JSX */
 	    age={21}
    /> 
  );
}

function Avatar(props) {  /* 👈 props is the only arg to the component */
  let person = props.person;
  let size = props.age;
  // ...
}

function Avatar({ person, age }) { /* 👈 you can destructure props into individual props */
  // person and age are available here...
}

function Avatar({ person, age = 20 }) { /* 👈 you can specify default values */
  // person and age are available here...
}
```

### Callback Handlers
Callback handlers are typically implemented as functions passed as props from a parent component to child component, allowing the child component to call the callback handler in response to something.

```JSX
import React from 'react';

/* Parent component */
function ParentComponent() {
  const handleClick = (message) => {       /* 👈 Callback handler in the parent */
    console.log("Callback from child: " + message);
  };

  return (
    <div>
      <ChildComponent onButtonClick={handleClick} /> {/* 👈 Callback handler passed as a prop */}
    </div>
  );
}

{/* Child component */}
function ChildComponent({ onButtonClick }) { /* 👈 Callback handler received as a prop */
  const handleButtonClick = () => {
    onButtonClick("Hello from Child!");  /* 👈 Child calls the callback handler */
  };

  return (
    <div>
      <button onClick={handleButtonClick}>Click Me</button>
    </div>
  );
}
```

### Hooks
Hooks let you use different React features from your components such as state, handle side effects, and access other features.

### State
Props are readonly. To change their value, you introduce **state**, which is a mutable data structure.

You define state using the `useState` hook, passing in an initial value and a *setter* function. React stores the state internally and associates it with the component. Calling the state *setter* function updates the value of the state variable and marks the component as **dirty**, meaning it needs to be re-rendered.
On the next render cycle, React calls the component function again and creates a new virtual DOM tree using the using the updated state (the latest state value from its ***closure***). A diff is done comparing the new Virtual DOM with the previous one, and React efficiently updates only the parts in the real DOM that has changed.

```JSX
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```






# JavaScript
- memory model ?
- garbage collection ?
- DOM ?
- etc...
