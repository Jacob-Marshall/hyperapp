# Hyperapp [![npm](https://img.shields.io/npm/v/hyperapp.svg?label=&color=0366d6)](https://github.com/jorgebucaran/hyperapp/releases/latest)

> The tiny framework for building hypertext applications.

- **Do more with less**—We have minimized the concepts you need to learn to get stuff done. Views, actions, effects, and subscriptions are all pretty easy to get to grips with and work together seamlessly.
- **Write what, not how**—With a declarative syntax that's easy to read and fun to write, Hyperapp is the finest way to create purely functional, feature-rich, browser-based apps in JavaScript.
- **1 kB**—Smaller than a favicon. Hyperapp is an ultra-lightweight Virtual DOM, highly-optimized diff algorithm, and state management library obsessed with minimalism. Get inspired, have fun and unleash your creativity!

Here's the first example to get you started: a mini todo app. You can [try it online](https://codesandbox.io/s/hyperapp-playground-fwjlo).

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <script type="module">
      import { h, text, app } from "https://unpkg.com/hyperapp"

      const Add = (state) => ({
        ...state,
        todos: state.todos.concat(state.value),
      })

      const FieldUpdated = (state, event) => ({
        ...state,
        value: event.target.value,
      })

      app({
        init: { todos: [], value: "" },
        view: ({ todos, value }) =>
          h("main", {}, [
            h("h1", {}, text("My Todos")),
            h("input", { type: "text", oninput: FieldUpdated, value }),
            button({ onclick: Add }, text("Add Todo")),
            h("ul", {},
              todos.map((todo) => h("li", {}, text(todo)))
            ),
          ]),
        node: document.getElementById("app"),
      })
    </script>
  </head>
  <body>
    <main id="app"></main>
  </body>
</html>
```

The app starts off with `init` to set the initial state, but we don't explicitly maintain it. Instead, we define actions to transform it and a `view` function to "visualize" it. The view returns a plain object representation of how we would like the DOM to look (the virtual DOM) and Hyperapp takes care of modifying the real DOM to match this specification whenever the state changes. That's really all there is to it.

Now it's your turn! Spend some time thinking about how the view reacts to changes in the state. Can you add a button that resets the counter back to zero? How about multiple counters?

## Installation

Install Hyperapp with npm or Yarn:

```console
npm i hyperapp
```

Then with a module bundler like [Rollup](https://rollupjs.org) or [Webpack](https://webpack.js.org) import it in your application and get right down to business.

```js
import { h, text, app } from "hyperapp"
```

Don't want to set up a build step? Import Hyperapp in a `<script>` tag as a module. Don't worry; modules are supported in all evergreen, self-updating desktop, and mobile browsers.

```html
<script type="module">
  import { h, text, app } from "https://unpkg.com/hyperapp"
</script>
```

To learn more, [work through the tutorial](docs/tutorial.md) or visit the [API reference](/docs/reference.md).

## Help, I'm stuck!

We love to talk JavaScript and Hyperapp. If you've hit a stumbling block, hop on the [Hyperapp Slack](https://hyperappjs.herokuapp.com) for to get help, and if you don't receive an answer, or if you remain stuck, please file an issue, and we'll figure it out together.

Is anything wrong, unclear, missing? Help us [improve this page](https://github.com/jorgebucaran/hyperapp/fork).

## Stay in the loop

- [Twitter](https://twitter.com/hyperappjs)
- [Awesome](https://github.com/jorgebucaran/hyperawesome)
- [/r/hyperapp](https://www.reddit.com/r/hyperapp)

## License

[MIT](LICENSE.md)
