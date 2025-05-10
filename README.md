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
* [package.json](#packagejson)
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
 	* [Lifting State](#lifting-state)
  	* [React Controlled Components](#react-controlled-components)
  	* [Props Destructuring](#props-destructuring)
  	* [React Fragments](#react-fragments)
  	* [Children Props](#children-props)
  	* [Passing JSX into named Prop](#passing-jsx-into-named-prop)
  	* [Inline Handlers in JSX](#inline-handlers-in-jsx)
  	* [React Conditional Rendering](#react-conditional-rendering)
  	* [React Forms](#react-forms)
  	* [Hooks](#hooks)
  	  * [useState](#usestate)
  	  * [useReducer](#useReducer)
  	  * [useEffects](#useeffects)
  	  * [useRef](#useref)
  	  * [Memoization in React](#memoization-in-react) 
  	    * [useCallback](#usecallback)
  	    * [useMemo](#usememo)
  	  * [Custom Hooks](#custom-hooks)
* [CSS](#css)
	* [CSS-in-CSS](#css-in-css)
 	* [CSS-in-JS](#css-in-js)  
* [JavaScript](#javascript)
	* [Destructuring](#destructuring)
 	  * [Array Destructuring](#array-destructuring)
 	  * [Object Destructuring](#object-destructuring)
  	  * [Nested Destructuring](#nested-destructuring)
  	* [Spread and Rest Operators](#spread-and-rest-operators)
  	  * [Spread Operator](#spread-operator)
  	  * [Rest Operator](#rest-operator)
  	* [Promise](#promise)
  	* [async/await](#asyncawait)
* [Native Browser](#native-browser)
  	* [Fetch API](#fetch-api)
  	  
# About React
Created by Facebook in 2013, [React](https://react.dev/learn) is a JavaScript library used for building single-page applications (SPAs), where the user interacts with the page without needing to reload it.

#### Key Features
- **Virtual DOM** - React creates a in-memory representation of the DOM for diffs, and updates the real DOM with only the parts that change, making rendering faster.
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

# package.json
In a React app's `package.json`, the scripts section defines shortcuts for commands you can run in the terminal.
```json
{
  // removed for brevity...

  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint .",
    "preview": "vite preview"
  },

  // removed for brevity...
}
```

- `dev` — usually runs the app in development mode.
It starts a development server (like Vite, Next.js, or Create React App) that watches your files for changes and hot-reloads the page.
```bash
npm run dev
```

- `build` — creates an optimized production version of your app.
It bundles and minifies the code, making it ready for deployment (smaller and faster).
```cmd
npm run build
```

- `lint` — checks your code for syntax/style issues according to a linter configuration (like ESLint).
It helps catch bugs and enforce coding standards.
```cmd
npm run lint
```

- `preview` — serves the production build locally so you can test what the deployed app will look like.
This doesn't rebuild, it just hosts the already-built files.
```cmd
npm run preview
```

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
Callback handlers are typically implemented as a function passed as a prop to child component, allowing the child component to call the callback handler and coommunicate with the parent component.

Callback handlers:
- are popular for handling form submissions and updating state in the parent component
- can receive parameters passed by the child component
- can be asynchronous
- can pass through multiple layers of components

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

### Lifting State
Lifting state describes a common practice in React development where state that is is lifted from a child component to a parent component. This allows multiple child components consume state from the closest common parent. 

> [!TIP]
> Callback functions are used to pass state data from child to parent when lifting state.
>
> An example of lifting state is a parent component with a list of data, and two child components. One child component provides input for filtered text, the other component displays the filtered list. The state of the filtered text is lifted up to the parent component. Changing the filtered

### React Controlled Components
In React, a controlled component is a form element (like an `<input>`, `<textarea>`, or `<select>`) whose value is controlled by React state instead of the DOM.
Basically:
- The form element's value is set by the component's state using a prop.
- Any change to the form element triggers an event (like onChange), where you update the state.
- The state then updates the displayed value.

### Props Destructuring
React `props` is simply a JavaScript object, which allows us to apply JavaScript features like object destructuring, to pull values out of objects or arrays.

```JSX
const Search = (props) => { 		{/* 👈 props is simply a JavaScript object */}
  const { search, onSearch } = props; 	{/* 👈 destructuring props pulls the values out of it */}

  return (
    <div>
      <input
	id="search"
	type="text"
	value={search} 		{/* 👈 using a value pulled out of destructured props */}
        onChange={onSearch}	{/* 👈 using a value pulled out of destructured props */}
      />
    </div>
  );
};
```

The `props` object can also be destructured in the function signature.

```JSX
const Search = ({ search, onSearch }) => ( {/* 👈 destructure props in the functions signature */}
  <div>
    <input
      id="search"
      type="text"
      value={search}
      onChange={onSearch}
    />
  </div>
);
```

React (JavaScipt) also supports nested destructuring.

```JavaScript
const user = {
  name: 'Alice',
  address: {
    city: 'London',
  },
};

const {
  name,
  address: {
    city,
  },
} = user  /* 👈 nested destructuring of complex user object */
```

### React Fragments
All react components need to return one top-level HTML element e.g. `<div></div>`. A React fragment can be used instead, wrapping sibling elements in a top-level element without rendering one to the output. 

The different between using `React.Fragment` and a `<div>` is Fragments don’t create an extra DOM node, providing a cleaner HTML structure compared to using `div` containers.

> [!TIP]
> Fragments support key's when mapping over a list of elements.

```JSX
const Search = ({ search, onSearch }) => (
  <div>  				{/* 👈 top-level HTML element */}
    <label htmlFor="search">Search: </label>
    <input id="search" type="text" value={search} onChange={onSearch} />
  </div>
);

const Search = ({ search, onSearch }) => (
  <React.Fragment> 			{/* 👈 using React.Fragment won't render the top-level element to the output */}
    <label htmlFor="search">Search: </label>
    <input id="search" type="text" value={search} onChange={onSearch} />
  </React.Fragment>
);

const Search = ({ search, onSearch }) => (
  <> 					{/* 👈 using the more common short hand version of React.Fragment */}
    <label htmlFor="search">Search: </label>
    <input id="search" type="text" value={search} onChange={onSearch} />
  </>
);
```

### Children Props
In React, the `children` prop is a special prop that automatically includes whatever you wrap inside a component when you use it. “Children” in React refers to the content placed between the opening and closing tags of a component. You can wrap anything and the component doesn't have to know what it is ahead of time.

In the following example `<h1>Hello World!</h1>` is passed into `<Wrapper>` component as `props.Children`. 
```JSX
function Wrapper(props) {
  return <div className="wrapper">{props.children}</div>;
}

export default function App() {
  return (
    <Wrapper>
      <h1>Hello World!</h1>
    </Wrapper>
  );
}
```

### Passing JSX into named Prop
In React, "slots" usually just means passing components or JSX into named props — not just children, but any prop you define.

In short:
- children = default slot
- Named props = custom slots
  
```JSX
function MainLayout(props) {
  return (
    <div className="layout">
      <div className="top">{props.top}</div>
      <div className="left">{props.left}</div>
      <div className="center">{props.center}</div>
    </div>
  );
}

<MainLayout
  left={<NavigationPanel/>}
  top={<Toolbar/>}
  center={<Body/>}
/>
```

### Inline Handlers in JSX
An inline handler is when you define an event handling function directly inside the JSX markup, instead of writing a separate function elsewhere.

In this example the `onClick` event is attached directly to the button where the handler is an arrow function `() => alert('Button clicked!')` written inline (i.e., directly inside the `onClick` attribute).
```JSX
<button onClick={() => alert('Button clicked!')}>Click Me</button>
```
> [!WARNING]
> Inline handlers are quick and convenient for very simple actions however; there is a performance cost. A new function is created every time the component renders, which can hurt performance if used carelessly in big apps.

### React Conditional Rendering
Using an `if-else` statement directly (inlined) in JSX is discouraged because JSX expects JavaScript expressions, not statements. Instead, you can use a ternary operator, which *is* an expression

```JSX
return (
  <div>
    {if (condition) { return <A /> } else { return <B /> }}  	// 👈 🚫 don't use if-else
  </div>
);

return (
  <div>
    {condition ? <A /> : <B />}  				{ /* 👍 ✅ use ternary operator instead */ }
  </div>
);
```
> [!WARNING]
> Hooks cannot be used within conditional statements or loops as they must be used at the top level of a function component. 

### React Forms
Forms in React work a bit differently than in plain HTML. Instead of the browser handling form elements and their state, React takes control by managing the form data in the component's state. This approach is called controlled components.

In a controlled component, form data is handled by React state. Every form input element (like `<input>`, `<textarea>`, or `<select>`) gets its value from state and updates that state on change.

```JSX
import { useState } from 'react';

function MyForm() {
  const [name, setName] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault(); // prevent page reload
    alert(`Submitted name: ${name}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input 
          type="text" 
          value={name} 
          onChange={(e) => setName(e.target.value)} 
        />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

```

You can manage multiple fields using a single state object.
```JSX
const [formData, setFormData] = useState({ name: '', email: '' });

const handleChange = (e) => {
  const { name, value } = e.target;
  setFormData(prev => ({ ...prev, [name]: value }));
};

<input name="name" value={formData.name} onChange={handleChange} />
<input name="email" value={formData.email} onChange={handleChange} />
```

### Hooks
Hooks let you use different React features from your components such as state, handle side effects, and access other features.

#### useState
Props are readonly. To change their value, you introduce **state**, which is a mutable data structure.

You define state using the `useState` hook, passing in an initial value and a *setter* function. React stores the state internally and associates it with the component. Calling the state *setter* function updates the value of the state variable and marks the component as **dirty**, meaning it needs to be re-rendered.
On the next render cycle, React calls the component function again and creates a new virtual DOM (React’s in-memory representation of the DOM) using the updated state (the latest state value from its ***closure***). A diff is done comparing the new Virtual DOM with the previous virtual DOM, and React efficiently updates only the parts in the real DOM that have changed.

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

#### useReducer
A React reducer is a function used with the `useReducer` Hook to **manage complex state logic** in a React component, especially when:
- actions trigger multiple state changes.
- state depends on previous state
- you have multiple sub-values in state

A reducer is just a function that takes the current `state` and an `action`, and returns a new `state`.

In the example below we `dispatch` `action`'s to change `state`:
- `state` = the state object is `count`
- `action` = the type is either `increment` or `decrement`, which tells us how to change the value of `count` 
- `dispatch` = the `changeCount` function, which tells us how to handle updates to `state` based on the type of `action` specified.
```JSX
import React, { useReducer } from 'react';

function changeCount(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(changeCount, { count: 0 });  // 👈 state = count, dispatch = changeCount

  return (
    <div>
      <p>{state.count}</p>     		{ /* 👈 consume `count` as a property of `state` */ }
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </div>
  );
}
```

#### useEffects
React side-effects are anything your component does besides rendering e.g. interacting with third party API's, and you manage them using the `useEffect` hook!

Examples of side-effects:
- Changing the DOM
- Fetching data from an API
- Setting a timer (setTimeout)
- Manually changing state or localStorage
- Subscribing to a service (like WebSocket)

In React, when a component causes one of these side-effects, React needs a special place to manage them, so they don't happen chaotically. This is in the `useEffect` hook.

Inside `useEffect`, you can safely:
- Fetch data
- Set up listeners
- Set timers
- Update things outside of React, e.g. local storage

The `useEffect` hook lets us opt into React’s component lifecycle when mounting, updating and unmounting the component. It can be triggered when the component is first mounted, but also if one of its values (state, props, derived values from state/props) is updated.

How useEffect Works
- It runs after the render.
- It can cleanup when the component unmounts (goes away).

```JSX
import { useEffect } from 'react';

function ExampleComponent() {
  useEffect(() => {
    console.log('This runs after the component renders!');
  });
  
  return <h1>Hello World</h1>;
}

// Example of cleanup
useEffect(() => {
  const timer = setTimeout(() => {
    console.log('Timer done!');
  }, 3000);

  return () => clearTimeout(timer); /* 👈 The return inside useEffect is a cleanup function. */
});

// Controlling when useEffect runs by passing a second argument: an array of dependencies.

useEffect(() => {
  console.log('Runs only once');
});  /* 👈 no second parameter → means "run on every render (initial and update renders). */

useEffect(() => {
  console.log('Runs only once');
}, []);  /* 👈 [] → means "run once when the component mounts" (like componentDidMount). */

useEffect(() => {
  console.log('Runs when `count` changes');
}, [count]); /* 👈 [count] → means "run when count changes." */
```

**Common Side-Effect Patterns**
| Task | useEffect Pattern|
| ---- | ---------------- |
| Fetching data on mount | useEffect(() => { fetchData() }, []) |
| Setting up event listeners | useEffect(() => { window.addEventListener(...) }, []) with cleanup |
| Running code when a prop or state changes | useEffect(() => { ... }, [propName]) |

**Why are side-effects separated?**
\
Because rendering should stay pure — meaning given the same inputs (props/state), it should always behave the same.
\
Side-effects (like fetching data) change the world, so they must happen separately after rendering.

#### useRef
`useRef` is a hook that gives you a way to persist a value across renders without causing a re-render when it changes.

It’s main purpose is for:
- Accessing DOM elements directly (like grabbing an input field to focus it).
- Storing mutable values but don't want to trigger re-renders when it changes (like a timer ID, previous state, etc.).

Example 1: Accessing DOM elements directly
```JSX
import { useRef } from 'react';

function MyComponent() {
  const inputRef = useRef(); 	/* 👈 inputRef is a reference object with a `.current` property. */

  const focusInput = () => {
    inputRef.current.focus(); 	/* 👈 current points to the actual input DOM node */
  };

  return (
    <div>
      <input ref={inputRef} type="text" /> {/* 👈 sets inputRef.current to the DOM input element */}
      <button onClick={focusInput}>Focus the input</button>
    </div>
  );
}
```

Example 2: Storing a mutable value without triggerring a re-render when it changes
```JSX
function Timer() {
  const count = useRef(0);

  function increment() {
    count.current += 1;   /* 👈 updating a `ref` doesn't trigger re-renders like state does */
    console.log(count.current);
  }

  return <button onClick={increment}>Click me</button>;
}
```

> [!TIP]
> `useRef(initialValue)` creates an object like `{ current: initialValue }`.

#### Memoization in React
> [!NOTE]
> A memoized function in a React component is a function that has been cached so that it doesn't get re-created on every render unless its dependencies change. This improves performance by avoiding unnecessary recalculations or re-renders.
>
> In React, memoization is typically done using `useMemo` or `useCallback`.
> 
> React components re-render frequently. Without memoization:
> - New function instances are created each time.
> - Child components that depend on those functions might re-render unnecessarily.
> - Performance can degrade, especially with complex UIs or large data sets.

##### useCallback
`useCallback` memoizes a function so that it's not recreated unless its dependencies change. It's useful when passing functions as props to child components to prevent unnecessary re-renders.

```jSX
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]);
```

> [!WARNING]
> If the dependencies array is empty, the memoized function is created only once and remains the same throughout the component’s lifecycle.

This example uses a `useCallback` to memoize a function passed to a child component. This prevents unnecessary re-renders of the child when the parent re-renders for unrelated reasons.
If `increment` were not memoized, every render of `Parent` would pass a new function, triggering an unnecessary re-render of `Child`.
```JSX
/* Parent */
function Parent() {
  const [count, setCount] = useState(0);
  const [toggle, setToggle] = useState(false);

  const increment = useCallback(() => {  /* 👈 memoize the increment function so it's not re-created unless its dependencies change. */
    setCount(prevCount => prevCount + 1);
  }, []);

  return (
    <div>
      <h1>Count: {count}</h1>
      <Child onClick={increment} />
      <button onClick={() => setToggle(!toggle)}> {/* 👈 changing unrelated state doesn’t cause Child to re-render. */}
        Toggle Parent State
      </button>
    </div>
  );
}

/* Child */
const Child = React.memo(({ onClick }) => {  /* 👈 Child is wrapped in `React.memo`, so it only re-renders if its props change. */
  return (
    <button onClick={onClick}>Increment Count</button>
  );
});
```

##### useMemo
`useMemo` memoizes a computed value returned from a function. It's useful when you have expensive calculations that shouldn’t re-run unless needed.

```JSX
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

#### Custom Hooks
Custom hooks are JavaScript functions that utilize React hooks to encapsulate and reuse logic in function components. The main purpose of custom hooks is promoting code reuse, abstraction of complex logic, and maintainability in React function components.
\
To create a custom hook, create a function starting with **“use”** and use existing React hooks or other custom hooks within it.

Here we create a custom hook `useCounter` to manage a Counter.
- `useCounter` is a custom hook that manages the logic for counting.
- It uses `useState` inside to track the number.
- The hook returns functions (`increment`, `decrement`, `reset`) and the current `count` value so you can easily reuse it in any component!

```JSX
import { useState } from 'react';

function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);

  const increment = () => setCount(prev => prev + 1);
  const decrement = () => setCount(prev => prev - 1);
  const reset = () => setCount(initialValue);

  return { count, increment, decrement, reset };
}

export default useCounter;
```

Here we use `useCounter` in a component
```JSX
import React from 'react';
import useCounter from './useCounter';

function CounterComponent() {
  const { count, increment, decrement, reset } = useCounter(5); // starting at 5

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={increment}>Increase</button>
      <button onClick={decrement}>Decrease</button>
      <button onClick={reset}>Reset</button>
    </div>
  );
}

export default CounterComponent;
```
# CSS
### CSS-in-CSS
The **CSS-in-CSS** approach in React refers to styling components using traditional external CSS stylesheets (or occasionally inline `<style>` tags), rather than embedding styles directly into JavaScript or components.

**Key characteristics of CSS-in-CSS:**
- Styles are written in `.css` (or `.scss`, `.less`, etc.) files.
- Classes and IDs are defined in those files.
- React components reference those classes via the className attribute.

Pros:
- Familiar for anyone with standard HTML/CSS experience.
- Works well with CSS preprocessors like Sass or Less.
- Keeps styling concerns separate from logic and markup.

Cons:
- Styles are global by default, which can lead to conflicts.
- Doesn't support dynamic styling as easily as CSS-in-JS.
- Harder to scope styles without tools like CSS Modules.

```CSS
.button {
  background-color: blue;
  color: white;
  padding: 10px 20px;
  border-radius: 5px;
}
```
```JSX
import './styles.css';

function ButtonComponent() {
  return <button className="button">Click Me</button>;
}
```

### CSS-in-JS
The CSS-in-JS approach in React means writing your CSS styles directly within your JavaScript code, typically scoped to a specific component. This allows for dynamic, component-level styling and often uses JavaScript objects or tagged template literals to define styles.

**Key Characteristics of CSS-in-JS:**
- Styles are co-located with the components they affect.
- Styles can be dynamic based on props, state, or themes.

You typically use a library like:
- styled-components
- Emotion
- Stitches
- JSS

Pros:
- Styles are scoped to components by default.
- Easier to apply dynamic styles (e.g., based on props or theme).
- Reduces global CSS conflicts.
- Encourages modular, reusable design.

Cons:
- Adds a runtime (or build-time) dependency.
- May have performance overhead in large apps.
- Can be less familiar for developers used to traditional CSS.

> [!NOTE]
>
> In the example below, we see the styled object gives you access to an HTML `button` element as a function. Calling the function returns a React component.

```cmd
npm install styled-components
```

```JSX
import styled from 'styled-components';

const Button = styled.button`
  background-color: blue;
  color: white;
  padding: 10px 20px;
  border-radius: 5px;

  &:hover {
    background-color: darkblue;
  }
`;

function ButtonComponent() {
  return <Button>Click Me</Button>;
}
```

# JavaScript
### Destructuring
Destructuring is a way to unpack values from arrays or properties from objects into individual variables easily.

Key difference:
- Arrays → Based on position.
- Objects → Based on property name.

#### Array Destructuring
```JS
const colors = ['red', 'green', 'blue'];
const [firstColor, secondColor] = colors; // 👈 pull out items by their position.
console.log(firstColor); // 'red'
console.log(secondColor); // 'green'

const [, , thirdColor] = colors;
console.log(thirdColor); // 'blue' 	 // 👈 you can skip items too
```
#### Object Destructuring
```JS
const user = { name: 'Alice', age: 25 };
const { name, age } = user; 		 // 👈 pull out items by their property names.
console.log(name); // 'Alice'
console.log(age);  // 25
```

#### Nested Destructuring
```JS
const person = {
  name: 'Bob',
  address: {
    city: 'Paris',
  }
};

const { address: { city } } = person;
console.log(city); // 'Paris'
```

### Spread and Rest Operators
Both spread and rest operators use `...`, but how they are used depends on the context.

Key difference:
- Spread → Expand out
- Rest → Gather in

#### Spread Operator
The spread operator `...` expands (spreads) elements of an array or object into individual elements.
> [!IMPORTANT]
> The spread operator creates a shallow copy of an object, meaning nested objects are still references to the original.
```JS
const numbers = [1, 2, 3];
const newNumbers = [...numbers, 4, 5];
console.log(newNumbers); // [1, 2, 3, 4, 5]  // 👈 spread each item from numbers into newNumbers

const user = { name: 'Alice', age: 25 };
const updatedUser = { ...user, location: 'NYC' };
console.log(updatedUser);
// { name: 'Alice', age: 25, location: 'NYC' } 👈 copied properties of user into updatedUser, then added a new one.
```

#### Rest Operator
The rest operator `...` gathers multiple elements into a single array or object.
```JS
function sum(...numbers) { //👈 ...numbers collects all arguments into an array.
  return numbers.reduce((acc, curr) => acc + curr, 0);
}

console.log(sum(1, 2, 3, 4)); // 10

// Example using object destructuring
const { name, ...details } = { name: 'Bob', age: 30, city: 'Paris' };
console.log(name);    // 'Bob'
console.log(details); // { age: 30, city: 'Paris' } //👈 name is grabbed separately, and details gathered the rest.
```

### Promise
A JavaScript **Promise** is a built-in object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

A Promise has three states:
- **Pending** – Initial state; neither fulfilled nor rejected.
- **Fulfilled** – The operation completed successfully.
- **Rejected** – The operation failed.

The promise methods `then()`, `catch()`, and `finally()` are used to associate further action with a promise that becomes settled.

```JavaScript
// Creating a promise
let promise = new Promise((resolve, reject) => {
  // Do something asynchronous
  if (success) {
    resolve("Success!");
  } else {
    reject("Error occurred.");
  }
});

// Consuming a promise
promise
  .then(result => {	// 👈 then() handles success (resolved)
    console.log("Resolved with:", result);
  })
  .catch(error => {	// 👈 catch() handles errors (rejected)
    console.log("Rejected with:", error);
  })
  .finally(info => { 	// 👈 finally() when the promise is settled (either fulfilled or rejected)
    console.log("All done");
  });
```

Promises can be chained.
```JavaScript
promise
  .then(handleFulfilledA, handleRejectedA)
  .then(handleFulfilledB, handleRejectedB)
  .then(handleFulfilledC, handleRejectedC);
```

### async/await
`async` and `await` are keywords in JavaScript used for handling asynchronous operations. A function is declared with the `async` keyword and `await` is used within the function to handle promises. The `await` keyword enables asynchronous, promise-based behavior to be written in a cleaner style and avoiding the need to explicitly configure promise chains.

- `async` marks the function as asynchronous, meaning it always returns a Promise.
- `await` can only be used inside an `async` function and pauses the function execution until the Promise is resolved or rejected.

An `async function` declaration creates an [AsyncFunction](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/AsyncFunction) object. Each time when an `async function` is called, it returns a new Promise which will be resolved with the value returned by the `async function`, or rejected with an exception uncaught within the `async function`.

```JSX
async function fetchData() {  // 👈 `async` marks the function as asynchronous
  try {
    const response = await fetch('https://api.example.com/data');  // 👈 `await` pauses until fetch is done
    const data = await response.json(); // 👈 `await` pauses until JSON is parsed
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}
```

Key Benefits of `async/await`
- Simplifies async flow – code looks synchronous
- Easier error handling with `try/catch`
- Improves readability over `.then()` chains

> [!Note]
>
> await only works with Promises.
>
> Using await blocks execution of the current async function until the Promise resolves.

> [!Tip]
>
> Use `Promise.all()` to handle multiple asynchronous operations concurrently in an async function.
 
# Native Browser
### Fetch API
> [!Note]
> ...from [mdn wed docs](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
>
> "The Fetch API provides an interface for fetching resources (including across the network). It is a more powerful and flexible replacement for [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest).
>
> The Fetch API uses [Request](https://developer.mozilla.org/en-US/docs/Web/API/Request) and [Response](https://developer.mozilla.org/en-US/docs/Web/API/Response) objects (and other things involved with network requests), as well as related concepts such as CORS and the HTTP Origin header semantics.
>
> For making a request and fetching a resource, use the [fetch()](https://developer.mozilla.org/en-US/docs/Web/API/Window/fetch) method. It is a global method in both [Window](https://developer.mozilla.org/en-US/docs/Web/API/Window) and [Worker](https://developer.mozilla.org/en-US/docs/Web/API/WorkerGlobalScope) contexts. This makes it available in pretty much any context you might want to fetch resources in.
>
> The `fetch()` method takes one mandatory argument, the path to the resource you want to fetch. It returns a [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to the [Response](https://developer.mozilla.org/en-US/docs/Web/API/Response) to that request — as soon as the server responds with headers — even if the server response is an HTTP error status."
>
```JSX
    React.useEffect(() => {
      dispatchStories({ type: 'STORIES_FETCH_INIT' });

      fetch(`${API_ENDPOINT}react`)         	// 👈 calling the native browsers fetch API
      .then((response) => response.json())      // 👈 for the fetch API, the response needs to be translated into JSON
      .then(result => {
        dispatchStories({
          type: 'STORIES_FETCH_SUCCESS',
          payload: result.hits,                 // 👈 the returned result has a different data structure `result.hits`
        });
      })
      .catch(() =>
         dispatchStories({ type: 'STORIES_FETCH_FAILURE' }));
      }, []);
```


<!--
- memory model ?
- garbage collection ?
- DOM ?
- etc...
-->
