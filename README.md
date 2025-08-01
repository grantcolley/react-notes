# react-notes

> [!IMPORTANT]
> The purpose of this `readme` is simply to consolidate content I find important or useful to me in some way on my journey to learn **React**, and condense them into a single page for my own personal reference.
>
> A significant amount of this content, including code samples, is AI generated.

### Table of contents
* [About React](#about-react)
	* [Key Features](#key-features)
* [Pre-requisites](#pre-requisites)
	* [Node.js](#node.js)
	* [npm](#npm)
* [Tooling](#tooling)
	* [Vite](#vite)
 	* [ESLint](#eslint)
  	* [Prettier](#prettier)
* [Libraries](#libraries)
	* [shadcn/ui](#shadcnui)
 	* [React Router](#react-router)
  	* [React Hook Form](#react-hook-form)
  	* [Zod](#zod)
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
  	  * [`useState`](#usestate)
  	  * [`useReducer`](#usereducer)
  	  * [`useEffects`](#useeffects)
  	  * [`useRef`](#useref)
  	  * [Memoization in React](#memoization-in-react) 
  	    * [`useCallback`](#usecallback)
  	    * [`useMemo`](#usememo)
  	  * [Custom Hooks](#custom-hooks)
* [CSS](#css)
	* [CSS-in-CSS](#css-in-css)
 	* [CSS-in-JS](#css-in-js)
  	* [CSS-in-CSS vs CSS-in-JS](#css-in-css-vs-css-in-js)
  	* [Tailwind CSS](#tailwind-css)
* [SVGs](#svgs)
* [Native Browser](#native-browser)
  	* [Fetch API](#fetch-api)
* [Deploy a React Application](#deploy-a-react-application)
	* [Build Process](#build-process)
* [React Router](#react-router-1)
	* [`<BrowserRouter>`](#browserrouter)
  	* [`<Routes>` & `<Route>`](#routes--route)
 	  * [Route Index](#route-index) 
 	  * [Nested Routes using `<Outlet />`](#nested-routes-using-outlet-) 
	* [`<Link>`](#link)
	* [`useNavigate`](#usenavigate)
  	* [Routing Parameters and `useParams`](#routing-parameters-and-useparams)
  	* [`useSearchParams`](#usesearchparams)
	* [Example](#example)
 	* [`createBrowserRouter`](#createbrowserrouter)
  	  * [The `loader` function](#the-loader-function)
	* [`<Form>`](#form)
* [React Hook Form Example](#react-hook-form-example)
* [React Hook Form + Zod Example](#react-hook-form--zod-example)
* [React Context](#react-context)
* [JavaScript](#javascript)
	* [JavaScript Types](#javascript-types)
 	  * [Primitive Types](#primitive-types)
 	  * [Object Types](#object-types) 
	* [Destructuring](#destructuring)
 	  * [Array Destructuring](#array-destructuring)
 	  * [Object Destructuring](#object-destructuring)
  	  * [Nested Destructuring](#nested-destructuring)
  	* [Spread and Rest Operators](#spread-and-rest-operators)
  	  * [Spread Operator](#spread-operator)
  	  * [Rest Operator](#rest-operator)
  	* [Promise](#promise)
  	* [async/await](#asyncawait)
* [TypeScript vs JavaScript](#typescript-vs-javascript)
	* [Static vs. Dynamic Typing](#static-vs-dynamic-typing)
 	* [Type Inference](#type-inference)
	* [Type Annotations](#type-annotations)
	* [Advanced Type Features in TypeScript](#advanced-type-features-in-typescript)
* [TypeScript](#typescript)
	* [TypeScript Type Annotations](#typescript-type-annotations)
	* [TypeScript Types](#typescript-types)
 	  * [Special Types](#special-types)
 	  * [Advanced Types](#advanced-types)
	* [Type Aliases](#type-aliases)
	* [Interfaces](#interfaces)
	* [Classes](#classes)
 	  * [Access Modifiers](#access-modifiers)
 	  * [Inheritance (Extends)](#inheritance-extends)
 	  * [Implementing an Interface](#implementing-an-interface)
 	  * [Static Members](#static-members)
 	  * [Getters and Setters](#getters-and-setters)
	  * [Abstract Classes and Methods](#abstract-classes-and-methods)
	* [Enumerations](#enumerations)
   	* [Union Type](#union-type)
   	  * [Unions and Variables](#unions-and-variables)
   	  * [Flexible Function Parameters](#flexible-function-parameters)
   	  * [Unions with Custom Types](#unions-with-custom-types)
   	  * [Union of Literal Types](#union-of-literal-types)
  	* [React.ReactNode Property](#reactreactnode-property)
  	* [Generics](#generics)
	  * [Generic Functions](#generic-functions)
  	  * [Generic Interfaces](#generic-interfaces)
  	  * [Generic Classes](#generic-classes)
  	  * [Generic Constraints](#generic-constraints)
  	  * [Default Generic Types](#default-generic-types)
  	  * [Generics Summary](#generics-summary)

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

### Prettier
[Prettier](https://prettier.io/) is a popular tool capable of formatting React and TypeScript code.

> [!TIP]
> Install Prettier as an extension in Visual Studio Code. Open the Extensions area in Visual Studio Code and search for an extension called `Prettier – Code formatter`.

# Libraries
### shadcn/ui
[shadcn/ui](https://ui.shadcn.com/) is a free component library providing prebuilt components using [Tailwind](https://tailwindcss.com/) + Radix UI (very modern, stylish).

### React Router
[React Router](https://reactrouter.com/) is a routing library for React applications, and is responsible for selecting what to show in the app for a requested path.

### React Hook Form
[React Hook Form](https://react-hook-form.com/) is a library for building forms for React applications. See [React Hook Form Example](#react-hook-form-example) below.

### Zod
[Zod](https://github.com/colinhacks/zod) is a TypeScript-first schema validation with static type inference. Zod is very popular when building React applications uing `React Hook Form + TypeScript`. See [React Hook Form + Zod Example](#react-hook-form--zod-example) below.

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

#### `useState`
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

#### `useReducer`
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

#### `useEffects`
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

#### `useRef`
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

##### `useCallback`
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

##### `useMemo`
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

> [!TIP]
>
> CSS-in-JS supports inheritance like in the example below.

 ```JSX
const Button = styled.button`
  background-color: blue;
  color: white;
  padding: 10px 20px;
  border-radius: 5px;

  &:hover {
    background-color: darkblue;
  }
`;

const StyledButtonSmall = styled(StyledButton)`
  padding: 5px;
`;

const StyledButtonLarge = styled(StyledButton)`
  padding: 10px;
`;
```

### CSS-in-CSS vs CSS-in-JS
| Feature                   | **CSS-in-CSS**                             | **CSS-in-JS**                                |
| ------------------------- | ------------------------------------------ | -------------------------------------------- |
| **Style location**        | Separate `.css` (or `.scss`) files         | Inside JavaScript/React files                |
| **Scoping**               | Global by default (unless using modules)   | Scoped to the component automatically        |
| **Dynamic styling**       | Limited, requires classes or inline styles | Easy (uses props, state, themes)             |
| **Tooling required**      | None (basic setup)                         | Requires a library (e.g., styled-components) |
| **Familiarity**           | Familiar to most web developers            | May require learning curve                   |
| **Reusability**           | Class-based, often global reuse            | Component-based, easily reusable             |
| **Performance**           | Generally faster (less JS overhead)        | Slight runtime or compile-time overhead      |
| **Maintainability**       | Separate files can aid large codebases     | Co-locating styles improves readability      |
| **Media queries/support** | Full CSS feature support                   | Full support with most libraries             |
| **Server-side rendering** | Requires setup with CSS bundling           | Libraries often provide built-in support     |

### Tailwind CSS
[Tailwind](https://tailwindcss.com/) is a set of prebuilt CSS classes that can be used to style an app. It is referred to as a **utility-first CSS framework** because the prebuilt classes can be thought of as flexible utilities.

The Tailwind library is installed as a development dependency because it’s not required at runtime.
\
\
`npm i -D tailwindcss` 

A key point of Tailwind is that we don’t write new CSS classes for each element we want to style – instead, we use a large range of well-thought-through existing classes. A benefit of this approach is that it helps an app look nice and consistent.

Instead of writing:
```CSS
.button {
  background-color: blue;
  padding: 1rem;
  border-radius: 0.5rem;
}
```
Using Tailwind CSS you write:
```HTML
<button className="bg-blue-500 p-4 rounded-lg">Click me</button>
```

> [!NOTE]
>
> An important point is that Tailwind doesn’t add all its CSS classes – that would produce a massive CSS file! Instead, it only adds the CSS classes used in the app.

# SVGs
[heroicons](https://heroicons.com/) is one source of SVGs.

Vite doesn't come aith SVG support so install a Vite plugin and modify the `vite,config.js`.

```CMD
npm install vite-plugin-svgr --save-dev
```

```JS
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import svgr from "vite-plugin-svgr"; // 👈 import the plugin

// https://vite.dev/config/
export default defineConfig({
  plugins: [react(), svgr()], // 👈 add the plugin
});
```

Example usage:
```SVG
<!-- check.svg -->
<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
  <path stroke-linecap="round" stroke-linejoin="round" d="m4.5 12.75 6 6 9-13.5" />
</svg>
```
```JSX
import Check from "./check.svg?react";

<Check height="18px" width="18px" />
```
 
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

# Deploy a React Application
### Build Process
Build the application from the command line to create a new `dist/` folder in the project with the bundled application. This folder can be deployed onto a hosting provider now.
```CMD
npm run build
```

Vite’s local HTTP server can also serve the application.

```CMD
npm run preview
```

# React Router
[React Router](https://reactrouter.com/start/modes) is in a package called `react-router-dom`, which can be installed from the Visual Studio Code terminal.

```CMD
npm i react-router-dom
```

> [!TIP]
>
> TypeScript types are included in `react-router-dom`, so there is no need for a separate installation.

React by itself doesn’t include built-in routing. For real-world apps with multiple pages or views (e.g., `/home`, `/about`, `/profile/:id`), you need a routing solution. React Router is a standard library for routing in React applications. It enables navigation between different components (or “pages”) in a React app, without requiring a full page reload—creating a single-page application (SPA) experience.

### `<BrowserRouter>`
`<BrowserRouter></BrowserRouter>` wraps your app and enables the use of routing features using the HTML5 history API.

```JSX
import { BrowserRouter } from 'react-router-dom';

<BrowserRouter>
  <App />
</BrowserRouter>
```

### `<Routes>` & `<Route>`
`<Routes></Routes>` and `<Route />` defines which component to show for which URL path and supports dynamic parameters like `:id`

```JSX
import { Routes, Route } from 'react-router-dom';

<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
  <Route path="/users/:id" element={<UserProfile />} />
</Routes>
```
#### Route Index
An index route is the default child route. If no no children match the parent route, it will deisplay the index route, if one is defined.
```JSX
{
  path: "/",
  element: <App />,
  children: [
    {
      index: true,		{/* 👈 specifying the index route */}
      element: <HomePage />,
    },
    ...,
  ]
}
```

#### Nested Routes using `<Outlet />`
Nested routes allows you to create layouts that share components e.g. navigation bars or sidebars, while rendering different content inside them depending on the URL.

In the following example, `<Dashboard />` is a parent route (page), while `<Profile />` and `<Settings />` are child routes, whose element (component) will be redered inside `<Dashboard />` when selected. 
```JSX
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Dashboard from "./Dashboard";
import Profile from "./Profile";
import Settings from "./Settings";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/dashboard" element={<Dashboard />}>  {/* 👈 Parent Route */}        
          <Route path="profile" element={<Profile />} />   {/* 👈 Child Route */}
          <Route path="settings" element={<Settings />} /> {/* 👈 Child Route */}
        </Route>
      </Routes>
    </BrowserRouter>
  );
}
```
Dashboard Layout Component
```JSX
import { Outlet, Link } from "react-router-dom";  // 👈 import Outlet

function Dashboard() {
  return (
    <div>
      <h2>Dashboard Layout</h2>
      <nav>
        <Link to="profile">Profile</Link>
        <Link to="settings">Settings</Link>
      </nav>

      <Outlet /> {/* 👈 Render nested child route here */}
    </div>
  );
}
```
### `<Link>`
`<Link />` replaces `<a href="...">` to allow client-side navigation without full page reloads.

```JSX
import { Link } from 'react-router-dom';

<Link to="/about">About</Link>
```

### useNavigate
`useNavigate` is used for programmatic navigation inside functions or effects.

```JSX
import { useNavigate } from 'react-router-dom';

const navigate = useNavigate();
navigate("/dashboard");
```

### Routing Parameters and `useParams`
Route parameters are defined using a colon `:` followed by a parameter name.

Here, route `{ path: '/product/:id', element: <Product /> }` defines an `:id` parameter.
\
This can be reached with the path `/products/123/`.

Multiple route parameters can be used in a path as follows: 
```JSX
{
  path: '/customer/:customerId/orders/:orderId',
  element: <CustomerOrder />,
}
```

`useParams` accesses dynamic URL segments like `:id` from the route.

```JSX
import { useParams } from 'react-router-dom';

const { id } = useParams(); // e.g., for /users/:id
```

### Example
```JSX
import {
  BrowserRouter,
  Routes,
  Route,
  Link,
  useParams,
} from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>                 {/* 👈 <BrowserRouter> wraps the app and enabling routing */}
      <nav>
        <Link to="/">Home</Link> | <Link to="/users/123">User 123</Link> {/* 👈 <Link> */}
      </nav>
      <Routes>   				
        <Route path="/" element={<Home />} />   {/* 👈 <Route> specifies the component to show  */}
        <Route path="/users/:id" element={<User />} />
      </Routes>
    </BrowserRouter>
  );
}

function Home() {
  return <h2>Home Page</h2>;
}

function User() {
  const { id } = useParams();   {/* 👈 access dynamic URL segments with useParams */}
  return <h2>User ID: {id}</h2>;
}
```

### `useSearchParams`
`useSearchParams` is a React router hook for getting and setting search params.

Search parameters come at the end of the `url` after the `?`, and are separated by `&`.

e.g `https:\\mysite.com?param1=one&param2=two`

```JSX
const [searchParams, setSearchParams] = useSearchParams();

const type = searchParams.get('param1');

setSearchParams({ param1: 'one', param2: 'two' });
```

### createBrowserRouter
Use createBrowserRouter when you're working with the data routers API in React. Use `createBrowserRouter` instead of `<BrowserRouter></BrowserRouter>` when you want to:
- Use loaders to fetch data before rendering a route
- Use actions to handle form submissions or mutations
- Handle route-level errors with error elements
- Define routes outside JSX in a config-driven way

```JSX
import {
  createBrowserRouter,
  RouterProvider,
} from 'react-router-dom';

const router = createBrowserRouter([
  {
    path: "/",
    element: <Home />,
    loader: async () => {
      const res = await fetch('/api/home');
      return res.json();
    },
    errorElement: <ErrorPage />,
  },
  {
    path: "/users/:id",
    element: <User />,
    loader: async ({ params }) => {
      const res = await fetch(`/api/users/${params.id}`);
      return res.json();
    },
  },
]);

function App() {
  return <RouterProvider router={router} />;
}
```

#### The `loader` function

The `loader` function runs before the route renders, allowing you to fetch data and access it via a `useLoaderData` hook.
```JSX
import { useLoaderData } from 'react-router-dom';

function Home() {
  const data = useLoaderData();
  return <div>{data.message}</div>;
}
```

> [!TIP]
> 
> When to prefer `createBrowserRouter`
> - You’re building a complex app with nested routes and layout-based design.
> - You want route-aware data fetching.
> - You want better error handling and forms integration.
> - If you just need basic client-side routing (`pages`, `links`, and `navigation`), `BrowserRouter` and `<Routes>` are simpler and totally fine.

### `<Form>`
React Router's form navigation refers to handling navigation via form submissions, instead of using `useNavigate()` or `<Link>`. This is useful for cases like submitting data with `POST`, `PUT`, or `DELETE` methods, where traditional hyperlink navigation doesn't work. React Router's `<Form>` component enhances regular HTML forms by integrating with the router.
```JSX
import { Form } from 'react-router-dom';

<Form method="post" action="/login">  {/* 👈 sends  POST request to the "/login" target route */}
  <input type="text" name="username" />
  <input type="password" name="password" />
  <button type="submit">Login</button>
</Form>
```

# React Hook Form Example
[React Hook Form](https://react-hook-form.com/) is a library for building forms for React applications.

```CMD
npm install react-hook-form
```

Basic login form example
```TypeScript
import { useForm } from 'react-hook-form';

function LoginForm() {
  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm();

  const onSubmit = (data) => {
    console.log('Form Data:', data);
    // You can send data to an API here
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)} className="p-4 max-w-md mx-auto">
      <div className="mb-4">
        <label>Email:</label>
        <input
          {...register('email', { required: 'Email is required' })}
          type="email"
          className="border rounded w-full p-2"
        />
        {errors.email && <p className="text-red-500">{errors.email.message}</p>}
      </div>

      <div className="mb-4">
        <label>Password:</label>
        <input
          {...register('password', {
            required: 'Password is required',
            minLength: {
              value: 6,
              message: 'Password must be at least 6 characters',
            },
          })}
          type="password"
          className="border rounded w-full p-2"
        />
        {errors.password && <p className="text-red-500">{errors.password.message}</p>}
      </div>

      <button type="submit" className="bg-blue-500 text-white px-4 py-2 rounded">
        Log In
      </button>
    </form>
  );
}

export default LoginForm;
```

Key Features
| Feature            | How it works                         |
| ------------------ | ------------------------------------ |
| `useForm()`        | Initializes the form                 |
| `register()`       | Binds inputs to React Hook Form      |
| `handleSubmit()`   | Handles form submission              |
| `formState.errors` | Contains validation error messages   |
| Validation         | Done inline via `register()` options |

# React Hook Form + Zod Example
[Zod](https://github.com/colinhacks/zod) is a TypeScript-first schema validation with static type inference.

Here is the same login form above, using [Zod](https://github.com/colinhacks/zod) for form validation.

```TypeScript
// LoginForm.tsx
import { useForm } from 'react-hook-form';
import { z } from 'zod';
import { zodResolver } from '@hookform/resolvers/zod';

// 1. Define the Zod schema
const schema = z.object({
  email: z.string().email({ message: 'Invalid email address' }),
  password: z.string().min(6, { message: 'Password must be at least 6 characters' }),
});

// 2. Infer TypeScript types from schema
type LoginFormData = z.infer<typeof schema>;

export default function LoginForm() {
  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm<LoginFormData>({
    resolver: zodResolver(schema),
  });

  const onSubmit = (data: LoginFormData) => {
    console.log('Submitted Data:', data);
    // handle API call or login logic
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)} className="p-4 max-w-md mx-auto">
      <div className="mb-4">
        <label>Email:</label>
        <input
          type="email"
          {...register('email')}
          className="border rounded w-full p-2"
        />
        {errors.email && <p className="text-red-500">{errors.email.message}</p>}
      </div>

      <div className="mb-4">
        <label>Password:</label>
        <input
          type="password"
          {...register('password')}
          className="border rounded w-full p-2"
        />
        {errors.password && <p className="text-red-500">{errors.password.message}</p>}
      </div>

      <button type="submit" className="bg-blue-500 text-white px-4 py-2 rounded">
        Log In
      </button>
    </form>
  );
}
```

Advantages of Zod in this setup.
| Benefit                     | What It Means                           |
| --------------------------- | --------------------------------------- |
| `z.infer<typeof schema>`    | Automatically get form input types      |
| Precise error messages      | Defined alongside your validation logic |
| Works great with TypeScript | Fully typed form inputs and submission  |
| Self-contained validation   | No need for external Yup schemas/types  |

# React Context
React Context is a feature in React that allows you to share data between components without having to explicitly pass props through every level of the component tree. It’s useful for global data like themes, authenticated user info, or any data that needs to be accessible by many components at different nesting levels.

> [!IMPORTANT]
> When a context value updates React re-renders every component that uses `useContext()` or `<Context.Consumer>` and is within the provider's subtree, regardless of whether they actually care about the changed part of the value.

```TypeScript
// context.js
import React from 'react';
export const ThemeContext = React.createContext('light');  // 👈 Context creation

// App.js
import { ThemeContext } from './context';

function App() {
  return (
    <ThemeContext.Provider value="dark">   // 👈 Provider provides the context to its children.
      <Toolbar />
    </ThemeContext.Provider>
  );
}

// Toolbar.js
import { useContext } from 'react';
import { ThemeContext } from './context';

function Toolbar() {
  const theme = useContext(ThemeContext); // 👈 Context accessed via useContext Hook
  return <div>Theme is {theme}</div>;
}
```

> [!NOTE]
> Use React Context when:
> - You need to pass data through many levels of components.
> - Props drilling becomes difficult or cluttered.
> - You have globally accessible data (like theme, locale, auth state).

> [!WARNING]
> Avoid overusing context for frequent updates (like high-frequency state changes), as it can lead to unnecessary re-renders.
> For complex global state, consider state management tools like Redux or Zustand.

# JavaScript
### JavaScript Types
#### Primitive Types
Primitive Types are immutable and passed by value.
- **string**: textual data e.g. `"Hello"`, `'World'`, ``Template Literal``
- **number**: both integer and floating-point numbers e.g. `42, 3.14, -0, Infinity, NaN`
- **bigint**: integers of arbitrary length e.g. `1234567890123456789012345678901234567890n`
- **boolean**: true or false e.g. `true`, `false`
- **undefined**: a variable that has been declared but not assigned a value e.g. `let x; // x is undefined`
- **null**: represents the intentional absence of any value e.g.  `let y = null;`
- **symbol**: a unique and immutable value, often used as object keys e.g. `const sym = Symbol('desc');`

### Object Types
Object Types are mutable and passed by reference.
- **Object**: generic collections of key-value pairs e.g. `{ name: "Alice", age: 30 }`
- **Array**: ordered collections e.g. `[1, 2, 3]`
- **Function**: callable objects e.g. `function greet() { return "Hello"; }`
- **Date**, **RegExp**, **Map**, **Set**, **WeakMap**, **WeakSet**, etc.
- Built-in objects with specialized behavior.

> [!IMPORTANT]
>
> - Type coercion: JavaScript is dynamically typed, so variables can change type at runtime.
>
> - Arrays are technically objects, but you can detect them using `Array.isArray(arr)`
> 
> - `typeof` operator: Can be used to check most types, but some quirks exist:
> \
> `typeof null === "object"` (this is a historical bug in JavaScript)

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

# TypeScript vs JavaScript
| Feature                     | JavaScript | TypeScript |
| --------------------------- | ---------- | ---------- |
| Static typing               | ❌          | ✅          |
| Interfaces & custom types   | ❌          | ✅          |
| Compile-time error checking | ❌          | ✅          |
| Enums                       | ❌          | ✅          |
| Access modifiers            | ❌          | ✅          |
| Generics                    | ❌          | ✅          |
| IDE auto-complete accuracy  | 🔶 Partial  | ✅          |

### Static vs. Dynamic Typing
JavaScript - Dynamically typed. Variables can hold any type, and types are checked at runtime.
\
TypeScript - Statically typed (with optional typing). Types are checked at compile time.
```JS
// JavaScript
let value = 42;  // number
value = "hello"; // now a string
```
```TS
// TypeScript
let value: number = 42;
value = "hello"; // Error: Type 'string' is not assignable to type 'number'
```

### Type Inference
JavaScript - No type inference; types are only known at runtime.
\
TypeScript - Uses type inference to deduce variable types even when not explicitly declared.
```TS
// TypeScript
let message = "Hi"; // inferred as string
message = 123;      // Error
```

### Type Annotations
JavaScript - No built-in syntax for type annotations.
\
TypeScript - Allows explicit type annotations for variables, function parameters, return types, etc.
```TS
// TypeScript
function greet(name: string): string {
  return "Hello, " + name;
}
```

### Advanced Type Features in TypeScript
TypeScript supports many type system features not available in JavaScript:
- Interfaces & Types
- Generics
- Tuples
- Enums
- Union & Intersection Types
- Literal Types
- Mapped & Conditional Types

# TypeScript
[TypeScript](https://www.typescriptlang.org/) was first released in 2012. It is a superset of JavaScript that adds Type safety resulting in fewer runtime bugs.

When a JavaScript codebase grows, it can become hard to read and maintain. TypeScript’s type system solves this problem. TypeScript uses the type system to allow code editors to catch type errors as developers write problematic code.

TypeScript can’t be executed directly in a browser – it must be transpiled into JavaScript first.

How it works is you write TypeScript code in `.ts` files and TypeScript compiles them to regular JavaScript `.js` files.

React normally uses JavaScript (JSX), but with TypeScript (TSX), you get all the typing benefits without giving up JSX.

File Extensions
- `.jsx` → becomes `.tsx` (for components using JSX + TypeScript)
- `.js` → becomes `.ts` (for plain logic or utility files)

> [!NOTE]
>
> Start a new Vite + React + TypeScript project
> ```CMD
> npm create vite@latest my-app -- --template react-ts
> cd my-app
> npm install
> ```
> This sets up everything, including:
> - React
> - Vite
> - TypeScript
> - Basic tsconfig.json

### TypeScript Type Annotations
In TypeScript, type annotations enable variables to be declared with specific types allowing the TypeScript compiler to check the code adheres to these types.
```TypeScript
let unitPrice: number;			// 👈 declare variable type
unitPrice = 123;

let quantity = 10;			// 👈 inferred type

let total = getTotal(unitPrice, quantity);

function getTotal(
	unitPrice: number,		// 👈 declare parameter type
	quantity: number
	): number {   			// 👈 declare function return type
 const total = unitPrice * quantity;
 return total;
}
```

### TypeScript Types
TypeScript supports all [JavaScript types](#javascript-types) and adds many more powerful ones.

#### Special Types
| **Type**  | **Description**                                 | **Example**                                     |
| --------- | ----------------------------------------------- | ----------------------------------------------- |
| `any`     | Turns off type checking                         | `let x: any = 5;`                               |
| `unknown` | Like `any`, but must be type-checked before use | `let x: unknown = 5;`                           |
| `void`    | No return value (used in functions)             | `function log(): void {}`                       |
| `never`   | Represents values that never occur              | `function fail(): never { throw new Error(); }` |
| `enum`    | Enumerated values                               | `enum Color { Red, Green }`                     |

#### Advanced Types
| **Type**                     | **Example**                                                       |
| ---------------------------- | ----------------------------------------------------------------- |
| **Union**                    | <code>let id: string &#124; number = "abc"; // variable holds many types</code> |
| **Intersection**             | `type A = { a: string }; type B = { b: number }; type C = A & B;` |
| **Literal**                  | <code>let dir: "up" \| "down"; // value is literally fixed</code> |
| **Type Aliases**             | `type Point = { x: number, y: number };`                          |
| **Interfaces**               | `interface Person { name: string; age: number; }`                 |
| **Generics**                 | `function identity<T>(arg: T): T { return arg; }`                 |
| **Type Assertions**          | `let val = <string>someValue;` or `someValue as string;`          |
| **Mapped/Conditional Types** | Advanced meta-programming with types                              |

### Type Aliases
In TypeScript, type aliases are a way to give a name to a type and are defined using the `type` keyword.

Type aliases can be applied to primitives, objects, functions, and generic types. Union types aliases allow a variable to represent more than one possible type. Type aliases are not the same as interfaces, but they can often be used interchangeably for object types.

```TypeScript
// Basic type alias syntax
type AliasName = ExistingType;
```
```TypeScript
// Primitive type alias
type Age = number;
let myAge: Age = 30;
```

```TypeScript
// Object type alias
type User = {
  name: string;
  age: number;
};

let user: User = {
  name: "Alice",
  age: 25
};
```

```TypeScript
// Union type alias
type ID = string | number;

let userId: ID = "abc123";
userId = 42; // valid
```

```TypeScript
// Function type alias
type GreetFunction = (name: string) => string;

const greet: GreetFunction = (name) => `Hello, ${name}`;
```

```TypeScript
// Generic type alias
type Response<T> = {
  data: T;
  status: number;
};

const userResponse: Response<User> = {
  data: { name: "Alice", age: 25 },
  status: 200
};
```

Intersection types combines multiple types into one. You can create an intersection using the `&` operator. They are great for composition. The resulting type has all the properties from each of the intersected types.
```TypeScript
type Person = {
  name: string;
  age: number;
};

type Employee = {
  employeeId: number;
  department: string;
};

// Intersection
type EmployeeProfile = Person & Employee; // 👈 create an intersection using the `&` operator

const john: EmployeeProfile = {
  name: "John Doe",
  age: 30,
  employeeId: 101,
  department: "Engineering"
};
```
> [!WARNING]
>
> If two types have conflicting property types, TypeScript will throw an error.

### Interfaces
Interfaces describes what properties and methods an object should have without implementing them.

```TypeScript
interface Person {
  readonly id: number;	// 👈 id is readonly
  name: string;		// 👈 name is mandatory
  email?: string; 	// 👈 email is optional
}
```

Inheritance using `extends`.
```TypeScript
interface Employee {
  id: number;
}

interface Manager extends Employee { // 👈 inherit Employee using `extends`
  teamSize: number;
}

const mgr: Manager = {
  id: 1,
  teamSize: 5
};
```

Function interface.
```TypeScript
interface Greeter {
  (name: string): string;
}

const greet: Greeter = (name) => `Hello, ${name}`;
```

### Classes
Classes create objects with specific structure and behavior, supporting features like constructors, methods, inheritance, access modifiers, and interfaces.

```TypeScript
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): void {
    console.log(`Hello, my name is ${this.name}.`);
  }
}

const john = new Person("John", 30);
john.greet(); // "Hello, my name is John."
```

#### Access Modifiers
| Modifier    | Description                            |
| ----------- | -------------------------------------- |
| `public`    | (default) Accessible everywhere        |
| `private`   | Accessible only within the class       |
| `protected` | Accessible within class and subclasses |
| `readonly`  | Can only be set during initialization  |
```TypeScript
class BankAccount {
  private balance: number = 0;

  deposit(amount: number) {
    this.balance += amount;
  }

  getBalance(): number {
    return this.balance;
  }
}
```

#### Inheritance (Extends)
```TypeScript
class Animal {
  move(): void {
    console.log("Moving...");
  }
}

class Dog extends Animal {
  bark(): void {
    console.log("Woof!");
  }
}

const d = new Dog();
d.move(); // from Animal
d.bark(); // from Dog
```

#### Implementing an Interface
```TypeScript
interface Flyable {
  fly(): void;
}

class Bird implements Flyable {
  fly(): void {
    console.log("Flapping wings...");
  }
}
```

#### Static Members
```TypeScript
class MathUtil {
  static PI = 3.14;

  static square(x: number): number {
    return x * x;
  }
}

console.log(MathUtil.PI); // 3.14
console.log(MathUtil.square(5)); // 25
```

#### Getters and Setters
```TypeScript
class User {
  private _username: string = "";

  get username(): string {
    return this._username;
  }

  set username(name: string) {
    if (name.length < 3) throw new Error("Too short");
    this._username = name;
  }
}
```

#### Abstract Classes and Methods
An abstract class cannot be instantiated and abstract methods must be implemented by subclasses.
```TypeScript
abstract class Shape {
  abstract area(): number;
}

class Square extends Shape {
  constructor(private side: number) {
    super();
  }

  area(): number {
    return this.side * this.side;
  }
}
```

### Enumerations
An `enum` is a special data type that allows you to define a set of named constants.

`enum` is numeric by default, but can also be string.

```TypeScript
enum Direction {
  North, // 0    // 👈 enums are numeric by default
  East,  // 1
  South, // 2
  West   // 3
}

let dir: Direction = Direction.North;
console.log(dir); // 0


enum Status {
  Pending = "PENDING", // 👈 string enums are supported
  InProgress = "IN_PROGRESS",
  Done = "DONE"
}

let taskStatus: Status = Status.InProgress;
console.log(taskStatus); // "IN_PROGRESS"
```

> [!TIP]
>  Const Enums (const enum)
>
> Use `const enum` to improve performance by inlining values during compilation — removes enum object from the output
> ```TypeScript
> const enum Direction {
>  Up,
>  Down
> }
>
> let move = Direction.Up; // Compiled as: let move = 0;
>``` 

> [!NOTE]
>
> Enum vs Union Types
> For simpler sets of values, consider using union types instead.
> ```TypeScript
> type Direction = "North" | "East" | "South" | "West";
> ```

### Union Type
A union type lets you specify that a variable, parameter, or return value can be one of several types.

#### Unions and Variables
```TypeScript
let value: string | number;

value = "hello"; // ✅
value = 42;      // ✅
value = true;    // ❌ Error: boolean is not assignable
```

#### Flexible Function Parameters
```TypeScript
function printId(id: string | number) {
  console.log(`ID: ${id}`);
}

printId("abc123"); // ✅
printId(100);      // ✅
```

#### Unions with Custom Types
```TypeScript
type Cat = { meow: () => void };
type Dog = { bark: () => void };

type Pet = Cat | Dog;

function makeSound(pet: Pet) {
  if ("meow" in pet) {
    pet.meow();
  } else {
    pet.bark();
  }
}
```

#### Union of Literal Types
```TypeScript
type Direction = "North" | "South" | "East" | "West";

function move(dir: Direction) {
  console.log(`Moving ${dir}`);
}
```

### React.ReactNode Property
In TypeScript, a property with the type React.ReactNode is used to indicate that the property can accept any valid React content as its value. This includes virtually everything you can render in a React component.

The primary purpose of using React.ReactNode is to allow a component prop to accept arbitrary renderable content, such as:
- JSX elements: `<div>Hello</div>`
- Strings: `'Hello'`
- Numbers: `123`
- Booleans (ignored in rendering): `true`, `false`
- `null` or `undefined` (render nothing)
- Arrays of the above
- Fragments (`<>...</>`)
- Other React components

```TypeScript
// component props
type MyComponentProps = {
  children: React.ReactNode;
};

// component accepts props with a React.ReactNode property called children
const MyComponent: React.FC<MyComponentProps> = ({ children }) => {
  return <div>{children}</div>;
};

// component usage
<MyComponent>
  <h1>Title</h1>
  <p>This is a paragraph.</p>
</MyComponent>
```

### Generics
TypeScript generics are a powerful feature that allow you to write flexible, reusable, and type-safe code. Generics let you create components (like functions, classes, or interfaces) that can work with any data type while still preserving type safety.

`T` is a placeholder for any type, and TypeScript keeps track of it.

#### Generic Functions
```TypeScript
function merge<T, U>(a: T, b: U): [T, U] {
  return [a, b];
}

const result = merge({ name: "Alice" }, 42); 
// result is [{ name: string }, number]
```

#### Generic Interfaces
```TypeScript
interface Box<T> {
  value: T;
}

const stringBox: Box<string> = { value: "Hello" };
const numberBox: Box<number> = { value: 123 };
```

#### Generic Classes
```TypeScript
class Stack<T> {
  private items: T[] = [];

  push(item: T): void {
    this.items.push(item);
  }

  pop(): T | undefined {
    return this.items.pop();
  }
}

const numStack = new Stack<number>();
numStack.push(1);
numStack.push(2);
```

#### Generic Constraints
```TypeScript
function getLength<T extends { length: number }>(value: T): number {
  return value.length;
}

getLength("hello");      // ✅ OK
getLength([1, 2, 3]);    // ✅ OK
getLength(123);          // ❌ Error: number has no 'length'
```

#### Default Generic Types
```TypeScript
function createBox<T = string>(value: T): Box<T> {
  return { value };
}

const box1 = createBox("hello"); // Box<string>
const box2 = createBox(123);     // Box<number>
```

#### Generics Summary
| Concept           | Example                           |
| ----------------- | --------------------------------- |
| Generic Function  | `function identity<T>(arg: T): T` |
| Generic Interface | `interface Box<T> { value: T }`   |
| Generic Class     | `class Stack<T> {}`               |
| Constraint        | `T extends { length: number }`    |
| Default Type      | `function<T = string>(arg: T)`    |


