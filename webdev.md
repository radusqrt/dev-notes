# React

## History

1. Each interaction with a site sends a _request_ to the _server_ => the server sends _JS/HTML/CSS_ back.
   1. **Problem**: make JS work for all browsers.
2. Each interaction with a site sends a _request_ to the _server_ using _jQuery_, which handles different browsers => the server sends _JS/HTML/CSS_ back.
   1. **Problem**: apps became bigger and so the JS files, and so the requests and responses.
3. **Single Page Applications (SPA)** meant the site became an app which didn't need to communicate with the server, but instead the focus was on _JS_ modifying the _HTML/DOM_ (with _AJAX_).
   1. 2010 - **AngularJS** from Google took over. It brought the concept of **components** and patterns such as **MVC**.
   2. **Problem**: Data is now flowing everywhere, the complexity is _huge_. It's hard to code.
   3. 2013 - **React** from Facebook.
   4. 2014 - **AngularJS** moved to **Angular**, so a lot of people moved to React.

## React concepts

1. > Don't touch the DOM. I'll do it for you.
   1. **DOM** = the tree representation of the page.
   2. **Imperative** programming = you change the DOM (e.g. if user is logged in => show this and that and so on)
   3. **Declarative** programming
      1. _React_ will modify the DOM just by showing it a **state**
      2. You tell it **this is the state** and it will _react_ to it.
2. Build websites like lego blocks.
3. Unidirectional data flow.
   1. React takes the _state_ and the _components_ and creates a **VirtualDOM** (can be seen by using [React Developer Tools - React Tab](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)).
   2. **Unidirectional** = if you want to change something, you have to change the _state_ => React _reacts_ to the new state.
      1. Data can **never move up** in the _VirtualDOM_.
      2. Advantage over _AngularJS_.
4. > I'm just the UI. The rest is up to you.
   1. It's a library for the UI, not a framework for _everything_.
   2. You can mix it up with anything.

### State

```javascript
let state = {
  user: "Radu Stochitoiu",
  isLoggedIn: True,
  friends: ["A", "B", "C"],
};
```

### VirtualDOM

![](figs/1-virtual-dom.png "VirtualDOM")

## How to be a great React Dev

1. Decide on _components_.
2. Decide the _state_ and _where_ it lives.
3. _What_ changes when state changes.

## NPM vs. YARN

- install dependencies from `package.json`: `npm install` == `yarn`
- install a package and add to `package.json`: `npm install package --save` == `yarn add package`
- install a dev-dependency to `package.json`: `npm install package --save-dev` == `yarn add package --dev`
- remove a dependency from `package.json`: `npm uninstall package --save` == `yarn remove package`
- upgrade a package to its latest version: `npm update --save` == `yarn upgrade`
  - if you want to upgrade to the latest packages, use `^16.13.1` in `package.json` which means any package greater than `16.13.1` will be installed by running `yarn install && yarn upgrade`
- install a package globally: `npm install package -g` == `yarn global add package`

## React Basics

### Set up a project

1. Install [nvm](https://github.com/nvm-sh/nvm).
2. Go on [NodeJS website](https://nodejs.org) and see the latest version.
3. Install the latest version: `nvm install 12.16.2`.
4. Use the latest version: `nvm use 12.16.2`.
5. Create react app: `npx create-react-app <app-name>`.

### Scripts meaning

- **start**: `yarn start` - opens a localhost version of the app.
- **build**: `yarn build` - turn everything in `src/` in something ready for any browser in `build/`. The code is minified and optimized.
- **test**
- **eject**: don't eject!

### Components

- functions don't use inner _states_.
- classes can use inner _states_.
  - you can change state members.
- **JSX** lets us turn `{this.state.something}` into its _HTML value_.
- information is passed by _props_.
- **setState** is _async_, you can't see the results immediately.
  - you can pass a _callback_ as a second parameter to **setState**.
- arrow functions **bind** automatically to the place (context) where they are defined.
  - Rule of thumb: use arrow functions on any class methods you define and **aren't** part of React.

### JSX

- uses specific attributes different from HTML ones:
  - _className_ instead of _class_;
  - _onClick_ instead of _onclick_ etc.
- turns `{something}` into the JS value of `something` in the VirtualDOM.
- every child element needs to have a **key** attribute, so if you change one element, React will render only what you changed, not all the elements.
  - if only one element in a list of 1000 elements changes, it only has to re-render that one.
- attributes:
  - **className**
  - **onChange**

### Lifecycle methods

- **componentDidMount** - exactly when the component is mounted in the VirtualDOM (at the beginning).
- **render** - every time the _state_ changes.

### Directory architecture

```
src
└───components
    ├───component1
    |   ├───component1.component.jsx
    |   └───component1.styles.css
    └───component2
        ├───component2.component.jsx
        └───component2.styles.css
```

### Snippets

- `rafc` &rarr; Creates a React Arrow Function Component with ES7 module system.

### Deploying on Github

1. `yarn add gh-pages`
2. In `package.lock` add:
   1. `"homepage": "https://radusqrt.github.io/monsters-rolodex",`
3. In `package.lock`, in **scripts** add:
   1. `"predeploy": "yarn build",`
   2. `"deploy": "gh-pages -d build"`
4. `yarn deploy`

# Glossary

- **HTML** = Hypertext Markup Language
- **DOM** = Document Object Model
- **SPA** = Single Page Application
- **JS** = Javascript
- **CSS** = Cascading Style Sheet
- **MVC** = Model View Controller
- **JSX** = JavaScript XML
