## Hi there 👋

# yhwh-script

There is nothing so complicated that it can't be made simple. yhwh-script is an advanced, yet minimalistic WebComponents framework featuring most of the functionality of popular JavaScript frameworks, but in a fraction of their complexity and therefore minimizing the effort of refactoring your code. It is written in vanilla JavaScript and you can freely customize it to fit your needs.

yhwh-script is solely built on <a title="Vite" href="https://vitejs.dev"><img height="20" alt="Vitejs-logo" src="https://vitejs.dev/logo.svg"></a> and an optional <a title="SQLite" href="https://sqlite.org/wasm"><img height="20" alt="SQLite-logo" src="https://sqlite.org/images/sqlite370_banner.gif"></a> database.

[The Unclicense](https://choosealicense.com/licenses/unlicense/)

## Features

- written in vanilla JavaScript
- support for (nesting) SingleFile WebComponents (SFCs) in dedicated .html files
- direct access to shadowDocument in each component's script
- following W3C standards and MDN-recommended best practices with just a few hacks to accomplish things where people claim: *"This is impossible with WebComponents"*
- built for SinglePageApplications (SPAs)
- full reactivity support via bubbling events (up) and observers (down)
- support for reactive state changes via state attribute
- support for dynamic imports of JavaScript modules
- offline capabilities
- pluggable navigation module using history-driven Component Router ( in examples sub-project )
- SQLite WebAssembly (WASM) for global state management
- use of OriginPrivateFileSystem (OPFS) for domain-private storage
- support for containerized Vite with basicSsl plugin (contact me)
- basic functionality in under <100LOC

## Installation

### Prerequisites

Besides <a title="git" href="https://git-scm.com"><img height="20" alt="GIT-logo" src="https://git-scm.com/images/logo@2x.png"></a> You need to have <a title="NodeJS" href="https://nodejs.org"><img height="20" alt="NodeJS-logo" src="https://www.vectorlogo.zone/logos/nodejs/nodejs-ar21.svg"></a> installed. I recommend using <a title="VSCodium" href="https://vscodium.com"><img height="20" alt="VSCodium-logo" src="https://vscodium.com/img/codium_cnl.svg"></a> for development and <a title="chromium" href="https://www.chromium.org/getting-involved/dev-channel/"><img height="20" alt="Chromium-logo" src="https://www.chromium.org/_assets/icon-chromium-96.png"></a> for testing. However, You can use any editor and browser of choice.

### Running 

Running yhwh-script is as easy as cloning a repository.

```bash
  git clone https://github.com/yhwh-script/sqlite-examples
  cd sqlite-examples
  npm install
```

OR you can use

```bash
  npx @yhwh-script/create-app {your_project}
  cd {your_project}
  npm install
```

and then

```bash
  npm run dev
```

to quickly setup a yhwh-script project. (There is no Vite template support yet, but hopefully they will reach out to me.)

You can then access the app via https://localhost:3443 in your browser.

## Creating

Have you ever thought about creating standards-conforming WebComponents in dedicated HTML-files? Now it's possible to use ```script```, ```style``` and ```template``` fragments and load them dynamically.

![Preview](https://raw.githubusercontent.com/yhwh-script/elements/main/docs/SFC.png)

That's basically everything. **Happy coding!**

[Examples](https://github.com/yhwh-script/examples/tree/main/) without and [with SQLite support](https://github.com/yhwh-script/sqlite-examples/tree/main/) can be found in the corresponding sub-project. It is recommended to use SQLite examples for demonstration purposes and if you need local-persistent state!

## API description and restrictions

Here are some further features You can use in a .html file

- use dynamic ```await import``` to include your own modules
- ```shadowDocument``` is the private scope DOM of the SFC to access inner-component elements. You can use most methods that are also available on the default ```document``` DOM, for instance ```shadowDocument.getElementById(...)``` or  ```shadowDocument.querySelector(...)```. (Yes, you can also add syntactic sugar and define your own shorthand versions of access methods like

```
const $ = (query) => shadowDocument.querySelector(query);
const $$ = (query) => shadowDocument.querySelectorAll(query);
```

but by default they are now removed from the latest release.

## Component Lifecycle

In case you want some deeper insights you should learn and understand how the ![WebComponents lifecycle](https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_custom_elements#custom_element_lifecycle_callbacks) is working.

![Preview](https://raw.githubusercontent.com/yhwh-script/yhwh-script/main/docs/components-lifecycle.png)

1. prefetch html components in [index.html](https://github.com/ProphetsAI/jsonly/blob/main/index.html)
2. declare your custom elements in the [./elements/index.js](https://github.com/yhwh-scrip/yhwh-script/blob/main/elements/index.js) (this happens automatically when you run ```npm run dev```)
3. After having created your custom elements you can instantiate them programmatically or by tag-name like in the [animals-view.html](https://github.com/yhwh-script/examples/blob/main/elements/animals/animals-view.html) (Check out [the other examples](https://github.com/yhwh-script/examples/blob/main/elements/) to see variations.)
4. changing the state of a component is possible via the event bubbling from inside or by changing the attribute ```data-state``` of the host element.

## Adding a navigation 

Adding a navigation is very easy. You can have [an entire navigation in one single html file](https://github.com/yhwh-script/sqlite-examples/blob/main/elements/home/home-navigation.html) defined as just another component. After having it integrated into your app

![nav integration](https://raw.githubusercontent.com/yhwh-script/examples/main/docs/nav-component.png)

it could look like this:

![Navigation example](https://raw.githubusercontent.com/yhwh-script/yhwh-script/main/docs/nav.png)

Of course you are completely free to customize the themes and make them awesome!

## Feedback

If you still have questions please let me know. Your opinion is valuable to me and sharing what you think is higly appreciated.  If you have any feedback and want to share your suggestions and improvements with me, please reach out to @jahro_me 
