# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) The Virtual DOM


## Learning Objectives
*After this lesson, students will be able to:*

- [ ] Describe the Virtual DOM versus the standard DOM
- [ ] Diagram how components are called, assembled and placed on the real DOM
- [ ] Use .jsx file extentions for files containing JSX


## Before we begin!

We've been shoving JSX and JS into files named `*.js`. As good practice and to follow AirBnb's style suggestions, we should name any file containing JSX `*.jsx`

 - [AirBnb Style Guide](https://github.com/airbnb/javascript/tree/master/react#naming)


## Review and Refactor

`Hello` in `src/App.jsx`  is our component class. It returns the JSX for our "Hello World!" and heading tags. Keeping components separate and organized is a best practice, so we created that in its own file.

To show up on the page, though, that component still needs to actually be called from somewhere.  The main "hub" of our React app is `src/index.js`.  We'll investigate how `src/index.js` is currently loading and rendering the component, and we'll improve the code by making it more explicit and readable.

Look at your `src/index.js` file, and contrast it with the code below.


```js
import React    from 'react';
import ReactDOM from 'react-dom';
import Hello    from './App';

ReactDOM.render(
  <Hello />,
  document.getElementById('root')
);
```

The first (and smallest) difference is that we've dropped the CSS file import. We just aren't using it.

The next difference is that `import App from './App';` has turned into `import Hello from './App'`.

>  This line imports the `Hello` component from the `src/App.js` file. Remember, the `default` part of `export default Hello` in `src/App.js` means that importing other names - like `App` - actually _already_ brings in the `Hello` component! As a best practice, though, we're going to explicitly import the `Hello` component.


The last difference is that `ReactDOM.render(
  <App />,` has turned into `ReactDOM.render(
    <Hello />,`.

> This changes the `ReactDOM.render()` call to explicitly say "Render whatever the component `Hello` returns."


## Hello World exercise - You do!
### Code along: Calling our `Hello` component explicitly

Update your `index.js` file to have the three changes listed above:
- Delete the CSS import.
- Change the component name that's imported to be your `Hello` component.
- Change the component name that's used inside `ReactDOM.render` to be your `Hello` component.

> Check it out! You should be able to browse to http://localhost:3000 and see that nothing has changed.


## Virtual DOM Intro

You should be familiar with the DOM. You may have noticed that our `src/index.js` code mentions `ReactDOM`. `ReactDOM` doesn't refer to the same DOM we know. Instead, it refers to a **Virtual DOM**. The Virtual DOM is a key piece of how React works.

So, how is this different? Watch [this video](https://generalassembly.wistia.com/medias/v5qyqsir0s) to find out. _(note: right click for new tab!)_

In React, the virtual DOM is a staging area for changes that will eventually be implemented.

![Virtual DOM Diagram](https://docs.google.com/drawings/d/11ugBTwDkqn6p2n5Fkps1p3Elp8ZToIRzXzvM4LJMYaU/pub?w=543&h=229)

  > If you're interested in learning more about the Virtual DOM, [check this video out](https://www.youtube.com/watch?v=-DX3vJiqxm4). _(note: right click for new tab!)_

You know every component eventually produces **JSX**. The `ReactDOM.render()` method generates a Virtual DOM node to be added to the actual DOM, *mounting* it to an element already in the DOM.

The `ReactDOM.render()` function takes two arguments:

```js
ReactDOM.render(
  <Hello />,
  document.getElementById('root')
)
```

- `<Hello />` uses **the name of the component to render**. In our `App.js` file, the `Hello` component returns the content to render:  a div with "Hello World!" and heading tags (written in JSX). As a reminder, this is the `Hello` component:

```js
  export default function Hello() {
      // make sure to return some UI
      return (
        <div>
          <h1>Hello World!</h1>
          <h3>It is time for tea.</h3>
        </div>
      )
    }
  };
```

- The second argument of the `ReactDOM.render()` function is `document.getElementById('root')`; this finds **the DOM element to append that content to**. This argument can be any element on the page. Here, we're simply appending it to an element with the id `root`.  (Look through the `index.html` file if you're curious about the HTML structure from `create-react-app`.)

When our `index.js` is processed, React compares the virtual DOM to the regular DOM and only updates the `root` element on the page. 


> Side note: What is `<Hello />` written in? JSX! Whenever you use a
self-closing tag in JSX, you **MUST** end it with a `/`, like `<Hello />` in the
above example. If you don't use a self-closing tag, JSX will look for a closing tag and never find it!
