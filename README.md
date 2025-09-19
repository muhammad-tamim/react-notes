<h1 align="center">React Notes</h1>

<h4>Table of Contents</h4>


- [Introduction](#introduction)
    - [The story of react:](#the-story-of-react)
    - [what is components:](#what-is-components)
    - [what is virtual DOM and How virtual dom work:](#what-is-virtual-dom-and-how-virtual-dom-work)
    - [library vs framework](#library-vs-framework)
    - [react vs next vs vue](#react-vs-next-vs-vue)
    - [Create React App with Vite:](#create-react-app-with-vite)
- [jsx](#jsx)
    - [How JSX Works:](#how-jsx-works)
    - [JSX rules:](#jsx-rules)




# Introduction

React is a component-based JavaScript frontend library developed by Facebook for building dynamic and interactive user interfaces, especially for single-page applications. It allows developers to create reusable UI components with efficiently update the DOM using a virtual DOM.

### The story of react:

Back in the early 2010s, Facebook engineers were in trouble. Their web applications, especially the news feed and the ads system, needed frequent updates. Every little change meant updating the real DOM directly — and that was slow, clunky, and full of bugs. The UI became harder to manage, and performance dropped.

In 2011, one Facebook engineer, Jordan Walke, decided to experiment. He built a prototype called FaxJS. The idea was bold: instead of updating the DOM directly, create a Virtual DOM — a lightweight copy of the actual DOM. Whenever something changed, compare the new Virtual DOM with the old one, and then update only the parts that actually changed in the real DOM. The results were stunning. Suddenly, apps ran smoother and faster.

By 2012, this new approach was powering Facebook news feeds and Ads, and later, Instagram. The success inside Facebook was undeniable.

Then came 2013. At JSConf US, Facebook decided to release this tool to the world. At first, developers didn’t know what to make of it. JSX — writing HTML inside JavaScript — looked strange. Some argued it broke the rules of traditional MVC (is a design pattern that separates an application into three parts: model, view, controller) patterns. A few even called it “the worst idea ever.”

By 2014, people started noticing that React apps were faster, more predictable, and easier to maintain. The component-based architecture encouraged reuse, and teams could build complex interfaces without drowning in spaghetti code.

Then came 2015, a breakthrough year. Big companies like Netflix, airBnb adopted React. The state management library Redux was released, solving complex data flow issues. React Native made it possible to use the same principles to build mobile apps for iOS and Android. Even developer tools like the React DevTools browser extension were launched, making debugging easier. React was no longer just a Facebook experiment — it was becoming the industry standard.

Over the following years, React kept evolving. Updates brought new features, performance boosts, and better developer experience. One of the biggest shifts came with Hooks (like useState, useEffect, and useContext). With Hooks, developers no longer needed class components for state and lifecycle management. Functional components became powerful and simple, and writing React apps became cleaner than ever.

From a hack at Facebook to a global phenomenon, React completely changed the way we think about building user interfaces. Today, React powers not only web applications but also mobile apps (React Native), desktop apps, and even experiments in VR.

### what is components:
A component is basically a reusable, independent piece of UI. Components can be small (like a button) or large (like a whole form or page).

![](./images/components.jpg)

### what is virtual DOM and How virtual dom work:
The Virtual DOM is a lightweight, in-memory copy of the real DOM.

![image](./images/virtual-dom.png)

Here, we have a component that has a `<div>` and inside the `<div>` two elements:
- First, React creates a Virtual DOM for this component, based on the actual DOM.
- Then, when we change something—like adding a new `<h3>` element—React creates a new Virtual DOM for the updated component.
- Next, React compares the newly created Virtual DOM with the previous Virtual DOM. This process is called diffing.
- After comparing, React updates only the parts of the real DOM that changed. This process is called reconciliation.



### library vs framework


| library                                                                                                                                                  | framework                                                                                                                             |
| -------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| A library is a collection of pre-written code that you can pick and use whenever you need. You decide when to call it and how to use it in your program. | A framework is a pre-defined structure that you must follow to build your application. It decides when your code runs and how to use. |
| you cal the library, means you decide when and how to use it.                                                                                            | the framework cal you, means it decide when and how to use it.                                                                        |
| more flexible, you can combine with others tolls                                                                                                         | less flexible, you must follow its rules and conventions                                                                              |
| focus on specific task                                                                                                                                   | provides a full solution for building entire apps                                                                                     |

### react vs next vs vue

|              | React                                  | Next.js                                                       | Vue.js                                       |
| ------------ | -------------------------------------- | ------------------------------------------------------------- | -------------------------------------------- |
| Type         | UI Library                             | Full-stack React Framework                                    | Progressive Framework                        |
| Developed by | Facebook                               | Vercel                                                        | Evan You (ex-Google)                         |
| Purpose      | Build UI components (Frontend only)    | Build full-stack web apps                                     | Build frontend apps; full-stack with Nuxt.js |
| Rendering    | Client-Side Rendering (CSR) by default | Supports CSR, SSR, SSG, ISR (Incremental Static Regeneration) | CSR by default; SSR available with Nuxt.js   |
| Flexibility  | Very flexible                          | less flexible                                                 | Balanced                                     |
| Performance  | Good, but CSR-only may affect SEO      | Excellent (SSR, SSG make it SEO-friendly & fast)              | Good (Nuxt adds performance benefits)        |
| Routing      | using react router or others libraries | Built-in file based                                           | built-in                                     |
| Best For     | Single page apps                       | SEO focused large scale apps                                  | single page to medium apps                   |

### Create React App with Vite:

Vite is a modern build tool that offers lightning-fast startup and optimized development experience for React and other frameworks.

**Step 1: Create React App with Vite** 
```bash
npm create vite@latest project-name -- --template react
```

**Step 2:  Install Dependencies**

```bash
cd my-react-app
npm i tailwindcss @tailwindcss/vite -D daisyui@latest
```

**Step 3: run you project on vs code**

```js
code .
```

**step 4: setup tailwind and daisyui:**

vite.config.js:

```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import tailwindcss from '@tailwindcss/vite'

// https://vite.dev/config/
export default defineConfig({
  plugins: [react(), tailwindcss()],
})
```

Import Tailwind CSS and daisyUi to index.css:

```js
@import "tailwindcss";
@plugin "daisyui";
```

**step 5: Run the development server:**

```bash
npm run dev
```

![image not found](./images/react-page.png)

---

# jsx

JSX stands for JavaScript XML. JSX allows you to HTML directly inside JavaScript, enabling you to create UI components more efficiently.

![image](./images/jsx.png)


**Without JSX:**

```js
const element = React.createElement("h1", null, "Hello, React!");
```

**With jSX**

```jsx
const element = <h1>Hello, React!</h1>;
```

note: JSX is just syntactic sugar for React.createElement.
  - Syntactic sugar is a programming term that means a special syntax is provided to make code easier to read or write, but it doesn’t add new functionality.It’s just “sweeter” (more human-friendly) syntax for something you could already do in a more verbose way.

### How JSX Works:

```jsx
const element = <h1 className="title">Hello</h1>;
```

Behind the scenes, Babel (a compiler that convert jsx to raw js) converts this into:

- 1st babel convert it into, react.createElement
  
```jsx
const element = React.createElement(
  "h1",
  { className: "title" },
  "Hello"
);
```

- then a plain js object: 

```js
{
  type: "h1",
  props: {
    className: "title",
    children: "Hello"
  }
}
```

React then uses this object to update the Virtual DOM.

### JSX rules: 

- You can embed JavaScript expressions inside { }: 

```jsx
const name = "Tamim";
const element = <h1>Hello, {name}!</h1>;
```

- JSX attributes are written like HTML but with camelCase (class = className, onclick = onClick)

- JSX Must Return a Single Parent:

Error: 

```jsx
return (
  <h1>Hello</h1>
  <p>World</p>
);
``` 

right: 

```jsx
return (
  <div>
    <h1>Hello</h1>
    <p>World</p>
  </div>
);

```

or use fragment:

```jsx
return (
  <>
    <h1>Hello</h1>
    <p>World</p>
  </>
);
```

- Conditional Rendering in JSX:

```jsx
const isLoggedIn = true;

return (
  <div>
    {isLoggedIn ? <h1>Welcome back!</h1> : <h1>Please log in</h1>}
  </div>
);
```

- Lists in JSX: 

```jsx
const items = ["Apple", "Banana", "Mango"];

return (
  <ul>
    {items.map((item, index) => (
      <li key={index}>{item}</li>
    ))}
  </ul>
);
```

