# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Props


## Learning Objectives
*After this lesson, students will be able to:*

- [ ] Describe the role props plays in our applications
- [ ] Create a component that renders props

## Component Data with Props

The React framework was built to handle data that changes over time.

So far, we have defined a `Hello` component in `App.jsx`. The component returns a `div` with a few headings, written in JSX.

In `index.jsx`, we are importing this component, appending what the `Hello` component's `render` method returns to the virtual DOM, and rendering that.

This is great, but it doesn't involve any data yet, let alone data that changes over time! 

Let's make it more interesting.

Rather than simply displaying "Hello world", let's display a greeting to the user. We'll make the greeting change dynamically based on the user's name.

The question is, how do we add a name to our `Hello` component without hardcoding it?

Find out! Try it yourself alongside [this video](https://generalassembly.wistia.com/medias/gchiu63slo) in [this codepen](https://codepen.io/susir/pen/vxWypq) _(note: right click both for new tab!)_




## Hello World exercise - You do!
### Code along: Adding props to our component

Let's use **props** to make our "Hello World" app more flexible.

##### First, a single prop

We want to make a greeting that's reusable for many different users, so we'll have a `name` prop for the name of the user.

In your `src/index.jsx`, we'll change the line that renders the `Hello` component to include this `name` prop. The new line will be:

`<Hello name={"Nick"} />`

> We pass in data wherever we are rendering our component. In rendering the `Hello` component above, we pass in a prop called "name" with a value of "Nick".

Your `index.js` should now look like this:

```js
import React from 'react';
import ReactDOM from 'react-dom';
import Hello from './App.js';

ReactDOM.render(
  <Hello name={"Nick"} />,
  document.getElementById('root')
)
```

Now, every time we render our component, we will pass in data.
- When the `Hello` component renders, we pass the `Hello` component a prop called `name` with a value of `Nick`.

If you check your application now, nothing has changed. We're passing the `name` prop into the component, but the component isn't _using_ it yet.

In our component definition, we will make a few changes:

1. Change the function signature to include a named parameter: `function Hello(props) {}`.
2. Change the `<h1>Hello World!</h1>` to `<h1>Hello {props.name}!</h1>`. The portion `{props.name}` deserves a closer look:
  - `props` will collect all the props for this component instance
  - `props.name` pulls out the name property from `this.props`.

> The `{}` syntax in JSX renders the result of any expression inside it. It works even without props. If you wrote `{2+2}` in your JSX, `4` would be rendered.

In `App.jsx`, your `Hello` class should now look like this:

```js
import 'React' from react;

export default function Hello(props) {
  return (
    <div>
      <h1>Hello {props.name}!</h1>
      <h3>It is time for tea.</h3>
    </div>
  );
};
```

In the above example, we replaced "world" with `{props.name}`.

> Check it out! You should be able to browse to http://localhost:3000 to view this change!
