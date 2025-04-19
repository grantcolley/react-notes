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
* [React Function Components](#react-function-components)
  
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

# React Function Components
**React function component** names must be in Pascal case i.e. where the first letter of each word starts with an upper case letter. This is because React treats components that begin with a lowercase letter as DOM tags (like `<div>`, `<span>`, etc.). So if a component starts with a lower case React will think it's a native HTML tag.

The function of a component runs every time a component is displayed or updated. Everytime it runs, the variables defined in the function’s body will be re-defined.

> [!TIP]
> To avoid unnecessarily redefining a variable every time a component is displayed or updated, define it outside the function component unless it needs something from within the function component’s body (e.g. parameters).

```JSX

const title = 'React'; // 👈 variables outside the function will only get defined once...

function App() {   // 👈 React components must start with an upper case letter

// 👈 function variables and additional code goes here...

  return (
      <div>    
        <h1>Hello {title}</h1>
      </div>
  );
}

export default App
```





