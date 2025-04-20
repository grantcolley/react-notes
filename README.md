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
* [React Entry Point](#react-entry-point)
* [React Function Components](#react-function-components)
* [JSX](#jsx)
	* [Transpiling JSX](#transpiling-jsx)
  	* [Variables](#variables)
  	* [Commenting JSX](#commenting-jsx)
 	* [Arrays](#arrays)
  	  
# About React
Created by Facebook in 2013, [React](https://react.dev/learn) is a JavaScript library used for building single-page applications (SPAs), where the user interacts with the page without needing to reload it.

#### Key Features
- **Virtual DOM** - React creates a virtual representation of the DOM and updates only the parts that change, making rendering faster.
- **JSX** - Combines JavaScript with HTML-like syntax for easier UI coding.

# Pre-requisites
React uses JavaScript and therefore React development on Windows requires Node.js and NPM to be installed.

### Node.js
[Node.js](https://nodejs.org/en/about) an asynchronous event-driven JavaScript runtime for building scalable network applications. Basically, [Node.js](https://www.robinwieruch.de/react-js-windows-setup/) is a JavaScript runtime which makes it possible to run JavaScript outside of the browser.

### npm
[npm](https://www.npmjs.com/package/npm) is a JavaScript package manager. Basically, [node package manager (NPM)](https://www.robinwieruch.de/react-js-windows-setup/) is used to install libraries, such as React.js, to your project on the command line.

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

# React Entry Point
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
  /* code removed for brevity */
  <body>
    <div id="root"></div>   <!-- 👈 React injects your app into the <div id="root"> -->
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

`src/main.jsx` is the entry point of the application. It tells React to render the `App` component inside the `#root` div from `index.html`.
```JSX
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <StrictMode>
    <App />		<!-- 👈 React renders the `App` component inside the `#root` div from `index.html` -->
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

