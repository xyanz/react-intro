# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Nested Components


## Learning Objectives
*After this lesson, students will be able to:*

- Diagram nested components
- Render components within another component
- Pass props to a nested component

## We Do: Nested Components

In your blog, part of your `App.jsx` renders this:

```html
<h3>Comments:</h3>
<p>{props.comments[0]}</p>
```

While you can certainly display more comments with `<p>{props.comments[1]}</p>`, `<p>{props.comments[2]}</p>`, etc, do you think this is the best way?

It would be a pain to have to explicitly define every comment when rendering `<Post />`, especially if each comment had multiple properties.

This problem is a telltale sign that our separation of concerns is being stretched, and it's time to break things into a new component.

To solve this problem, in the following slides we will **nest** `Comment` components within a `Post` component.

We can create these comments the same way we created posts: By defining a `Comment` functional component that renders some property.

Next, we'll put comments inside an individual post component. To do this, we can reference a comment using `<Comment />` inside of `Post`..

* Starting from the blog post code, let's create a new file for a `Comment` component, `src/Comment.jsx`:

```jsx
import React from 'react';

function Comment(props) {
  return (
    <div>
      <p>{props.body}</p>
    </div>
  );
}

export default Comment;
```

What have we done?

* We've defined our component, which names the `props` parameter.
* We're exporting this `Comment` function by default for anything importing this file.
* We are returning JSX that contains a paragraph displaying a `body` prop (which will be passed in).

Now, in `src/App.jsx`, we need to import our `Comment` component so it's available from the `Post` component class.
* Change the top of `App.jsx` to include the new class:

```js
import React from 'react';
import './App.css';

// Load in Comment component
import Comment from './Comment.jsx';
```
With this setup, we can render one or more comments inside the `Post` component. Currently,
`<p>{props.comments[0]}</p>` is rendering one comment in the `Post` component from `App.jsx`. Now, instead of this line, we'll want to render a `Comment` component (which renders a paragraph with the comments, so it will look the same!).

* Edit that line to render a comment instead of directly rendering a paragraph.  Make sure you send through the `body` prop that the `Comment` component class needs:

```js
<Comment body={props.comments[0]} />
```

Let's reflect on what just happened. We rendered a component _inside another component_. Technically, we just **nested** components. Very much like how we imported `Post` from `App.jsx` into `index.jsx` and rendered a post inside `index.jsx`, we've imported `Comment` from `Comment.jsx` into `App.jsx` and rendered a comment. Inside `App.jsx`, we're using some of the props to render a post and simply passing the `comments` prop on to be rendered with the `Comment` component class. So the flow of the props looks like this:


![nested components chart](./images/nested_components_chart.jpg)


## To get a little more advanced...

That's nested components! What we're about to look into is just the idea of calling an object during the `return` statement - and that object can have component calls in it.

### What we did:

`<Comment body={props.comments[0]} />` passed just the first object in the `comments` array

### What we can do:

We can also simply pass a variable as a parameter. For example, we could pass the whole `comments` array with `<Comment body={comments} />`. We can also just write a JavaScript expression if we put it inside brackets. For example, if I had an object inside my `App.jsx`, each row of the object could individually call the `Comment` component.

* Following along here is optional! This is to demonstrate a shorthand way of writing what your code already does.

```js
import 'Comment' from './Comment';

export default function Post(props) {
  const allComments = [
    <Comment body={props.comments[0]} />,
    <Comment body={props.comments[1]} />,
    <Comment body={props.comments[2]} />
  ];

  return (
    <div>
      <h1>{props.title}</h1>
      <p>by {props.author}</p>
      <div>
        <p>{props.body}</p>
      </div>
      <h3>Comments:</h3>
      {allComments}
    </div>
  );
}
```

 * _Note: We could have put all of our code in one file, but it's a good practice to break components out into different files to help practice separation of concerns. The only downside is that we have to be extra conscious of remembering to **export / import** each component to the file where it's rendered._
