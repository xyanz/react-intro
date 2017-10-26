Fork and clone the following repository: https://github.com/bitmakerlabs/react-film-library

This project was created with `create-react-app`. Once you have the app cloned, you should run `npm install`. You can then run it with `npm run start`.

## Your Mission

Today the plan is to identify the app components, create the overall structure, then split that structure into individual components. We'll pass films as props to each component and ultimately use iteration to render one component for each film.

![](images/film-1.png)

### Tasks

**Importantly**: After each step below, check your application to see how it looks before going to the next one.

Hint: Don't forget any import statements as you add more files.

#### Step 1: Create baseline layout

First, create the layout - a Films column and a Details column.

Make the provided App component render the following code:

```
<div className="film-library">
  <div className="film-list">
    <h1 className="section-title">FILMS</h1>
  </div>

  <div className="film-details">
    <h1 className="section-title">DETAILS</h1>
  </div>
</div>
```

#### Step 2: Create new components

Move the film-list and film-details into their own separate components (in separate files), `FilmListing` and `FilmDetails`, respectively.

Make sure you now call these components in `App.js`. Check your app - if you've done it right, it will look the same.

#### Step 3: Pass props

Pass the films (stored in `TMDB.films`) to each of your new components as props.

Hint: For now, this is just changing the `App.js` file to be sure it imports the film file and have a prop!

If you check your file, it still shouldn't look differently - we're not using the props yet.

#### Step 4: Render a film

In the `FilmListing` component, render 1 film, just the title, as an `<h1>`, below the `section-title`

Does "It" appear on the left side of your browser?

#### Step 5: Create an array of film title elements

Use `.map()` inside of the `FilmListing` to iterate over the collection of films and create an element for each one.

Hint: Each film object in the collection has an `id` property.

Hint: Need help on `map`? This step will look like this:

```js
const filmRows = this.props.films.map((film) => {
  return _____
});
```

Nothing will change in your browser, since you haven't used this yet.

#### Step 6: Render the array of film titles

Render each item in the collection. Make sure that each element that's rendered from the collection has a unique `key` attribute.

Hint: Each film object in the collection has an `id` property.

Now, each film title should be displayed in the left column.


#### Step 7: Flesh out each film row

Make each film row look like the main finished image, using the following markup:

```
<div className="film-row">
  <figure className="film-poster">
    <img src={posterUrl} alt="" />
  </figure>

  <div className="film-summary">
    <h1>TITLE</h1>
    <p>YEAR</p>
  </div>
</div>
```

You'll have to create the `posterUrl` for each film by combining the prefix `https://image.tmdb.org/t/p/w780/` with each film's `poster_path` property.

You'll also have to extract the year from the `release_date` property. To do this, you'll need to figure out how to use the [`getFullYear()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getFullYear) JS method.

Hint for `getFullYear()`: In this single line of new code, you'll use the keywords `new` and `Date`.


#### Step 8: Move film rows to their own component

Each film row is kinda complex now. Let's move that code into its own component called `FilmRow`. Don't forget to pass the individual film prop to the component when creating them!

#### Step 9: Move film poster to their own component

Since the poster requires you to create the URL first, let's move those elements to their own component. This could be reusable later. Again, don't forget to pass the film as a prop to the new `FilmPoster` component.
