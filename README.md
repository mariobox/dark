We will implement a dark theme selector for our site that visitors can activate by clicking on an icon. We will discuss what we have to do to the HTML, CSS and JavaScript files that make up our site to make that happen.

## The HTML

For this example, we will create three simple HTML pages: `index.html`, `about.html` and `contact.html`. The code above is the <code>index.html</code> page. At the top of each page, we will include a simple navigation menu next to which we will place a moon-shaped icon that users can click to turn on dark mode. Once in dark mode, the moon icon will switch to a sun icon, indicating that by clicking it the visitor can go back to the default light mode. Both the moon and the sun icons can be found in [Fontawesome](https://fontawesome.com).

## The CSS

We will define some variables for the colors we want to use in our dark and light themes. To keep it simple, we will just focus on the background, the font and the link colors. We will define our variables in the `html` element and we'll then reference them in the `body` and `link` elements. We will also create a `dark` class for the `html` element that we will activate via JavaScript once a visitor clicks on the moon icon.

## The JavaScript

Here's where the real magic happens. Since ours is a static site, we can't rely on the server to store our mode preferences. We need to do it in the visitor's browser, and for that we will make use of the `localStorage` DOM property.

Since the default mode is light, you'll get the site in light mode on your first visit. As soon as the page loads, an event listener on the `DOMContentLoaded` event triggers a callback function that checks the browser's `localStorage` property for any record of the site's mode. In our first visit there will be nothing stored there so the page will load in light mode.

Upon clicking in the moon icon, the value of the `THEME` const will change to `dark` and the key value pair will be stored in `localStorage` via the `localStorage.setItem(THEME, ...)` method. At the same time, the class of our `html` element will be set to `dark` and the `innerHTML` of the `span` containing the moon icon html code will change to display a sun icon instead. Clicking on the sun icon will take the visitor back to light mode by following the same process. The changes between light and dark mode are implemented via the  `applyTheme()` function.

Since the values stored in `localStorage` are presistent, as long as the visitor uses the same browser it will remember the chosen mode next time the site is visited. You can test this by navigating to the different pages of the site, or even closing and opening your browser. Here is a [demo](https://mariobox.github.io/dark) where you can see this dark mode implementation in action.

