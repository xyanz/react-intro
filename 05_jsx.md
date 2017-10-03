
### Wait - What's that HTML doing in my Javascript?

This is currently the contents of our `src/App.js` file:

```js
// bring in React and Component from React

import React, {Component} from 'react';

// define our Hello component
class Hello extends Component {
  // what should the component render?
  render () {
    // make sure to return some UI
    return (
      <h1>Hello World!</h1>
    )
  }
}

export default Hello
```

Let's talk about the value that the render method returns. It looks an awful lot like an HTML heading, but it's not. We often write out React components in **JSX**.

Wait, what's that? Try it yourself alongside [this video](https://generalassembly.wistia.com/medias/dcps4dqziy) in [this codepen](https://codepen.io/susir/pen/wJPoBw) (note: right click  both links to open in a new tab!)

So, JSX allows us to write code that strongly resembles HTML. It is eventually compiled to lightweight JavaScript objects.

Your `Hello` component's `render` method:
- Currently returns JSX, not HTML.
- The JSX creates a heading with `'Hello World!'`.
- Your component reads this and renders a "Hello World!" heading.

> React can be written without JSX. We won't be doing this, but if you want to learn more, [check out this blog post](http://jamesknelson.com/learn-raw-react-no-jsx-flux-es6-webpack/) (note: open in new tab!).

### Challenge: Greet the day!

- Change your `Hello` component to return multiple lines.
  - Add a line below the "Hello World!" heading that will display `"It is time for tea."` in an `h3`.

> Hint: Remember, the return statement in `render` can only return one DOM element. You can, however, place multiple elements within a parent `div` element.*
