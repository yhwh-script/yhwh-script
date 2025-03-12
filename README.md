## Hi there 👋

# yhwh-script

With YHWH-Script ( pronounced: /jɑːhwe/-script) your web app can become whatever you want it to become. There is nothing so complicated that it can't be made simple. yhwh-script is an advanced, yet minimalistic WebComponents framework featuring most of the functionality of popular JavaScript frameworks, but in a fraction of their complexity and therefore minimizing the effort of refactoring your code. It is written in vanilla JavaScript and you can freely customize it to fit your needs.

yhwh-script is solely built on <a title="Vite" href="https://vitejs.dev"><img height="20" alt="Vitejs-logo" src="https://vitejs.dev/logo.svg"></a> and has an optional <a title="SQLite" href="https://sqlite.org/wasm"><img height="20" alt="SQLite-logo" src="https://sqlite.org/images/sqlite370_banner.gif"></a> support within the [Origin Private Filesystem (OPFS)](https://developer.mozilla.org/en-US/docs/Web/API/File_System_API/Origin_private_file_system).

[The Unclicense](https://choosealicense.com/licenses/unlicense/)

## Features

- written in vanilla JavaScript
- support for custom elements in dedicated .html files (SinglePageApplications SPAs and SingleFile WebComponents SFCs), create or use your own library of custom-elements
- following [W3C standards and MDN-recommended best practices](https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_custom_elements#custom_element_lifecycle_callbacks) with just a few hacks to accomplish things where people claim: *"This is impossible with WebComponents"*
- direct access to ShadowDOM in each component's script (via `shadowDocument`)
- full reactivity support in vanilla JavaScript (via bubbling events/observers)
- SQLite WebAssembly (WASM) for global state management with OriginPrivateFileSystem (OPFS), your data stays private
- dedicated workers for database pooling
- [Responding to attribute changes](https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_custom_elements#responding_to_attribute_changes)
- access to modules API (via window object)
- offline capabilities
- pluggable [navigation module](https://github.com/yhwh-script/examples/blob/main/public/elements/home/home-navigation.html) using history-driven Component Router
- support for containerized builds
- https support out of the box ([@vitejs/plugin-basic-ssl](https://github.com/vitejs/vite-plugin-basic-ssl))
- basic functionality in under <100LOC

## Installation

### Prerequisites

You need to have <a title="NodeJS" href="https://nodejs.org"><img height="20" alt="NodeJS-logo" src="https://www.vectorlogo.zone/logos/nodejs/nodejs-ar21.svg"></a> installed.

### Running 

Running yhwh-script is as easy as cloning one of the repositories below.
```bash
  git clone https://github.com/yhwh-script/sqlite-examples.git
  cd sqlite-examples
  npm install
```
OR you can use npx, which is the recommended way
```bash
  npx @yhwh-script/create-app {your_project}
  cd {your_project}
  npm install
```
and then simply 
```bash
  npm run dev
```
to quickly setup a yhwh-script project. You can then access the app via https://localhost:3443 in your browser.

## Creating

Have you ever thought about creating standards-conforming WebComponents in dedicated HTML-files? Just create your custom elements inside the `public/elements` folder. You just have to stick to (custom elements naming conventions)[https://html.spec.whatwg.org/multipage/custom-elements.html#valid-custom-element-name]. They will work out of the box as HTML, (S)CSS and JavaScript custom elements with ```script```, ```style``` and ```template``` fragments à la Vue or Svelte.

That's basically everything. **Happy coding!**

[Examples](https://github.com/yhwh-script/examples) without and [with SQLite support](https://github.com/yhwh-script/sqlite-examples) can be found in the corresponding sub-projects. It is recommended to use SQLite examples for demonstration purposes and if you need local-persistent state!

## API description and restrictions

Here are some further features You can use in a .html file

- You can use dynamic imports (```await import```) to include modules on demand
- Use the ```state``` constant to access ```data-state``` to propagate data into the element or use publicAPIs
- ```shadowDocument``` is the private scope DOM of the element. You can use most methods that are also available on the ```document```, for instance ```shadowDocument.getElementById(...)``` or  ```shadowDocument.querySelector(...)```.
- You can also add syntactic sugar and define your own shorthand versions of access methods like
```
const $ = (query) => shadowDocument.querySelector(query);
const $$ = (query) => shadowDocument.querySelectorAll(query);
```

## Component Lifecycle

In case you want some deeper insights you should learn and understand how the [WebComponents lifecycle](https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_custom_elements#custom_element_lifecycle_callbacks) is working.

![Preview](https://raw.githubusercontent.com/yhwh-script/yhwh-script/refs/heads/main/docs/excalidraw_customElements-lifecycle.png)

1. Put your custom elements in the [./public/elements/](https://github.com/yhwh-script/sqlite-examples/public/elements) folder (/src/elements/index.js is automagically generated when you run ```npm run dev```)
2. After having created your custom elements you can instantiate them programmatically or by tag-name like in the [animals-view.html](https://github.com/yhwh-script/examples/public/elements/animals/animals-view.html) (Check out [the other examples](https://github.com/yhwh-script/examples/public/elements/) to see variations.)
3. changing the state of a component is possible via bubbling events from inside or by changing the ```data-state``` attribute of the host element.

## Adding a navigation 

Adding a navigation is very easy. [As the example shows](https://github.com/yhwh-script/sqlite-examples/public/elements/home/home-navigation.html) You can have an entire navigation in one single html file defined as just another custom element. After having it integrated into your app with a single tag (``<home-navigation></home-navigation>), you can have routing support and all the things you would expect.

Of course you are completely free to customize the themes and make them awesome!

# Preview

![Preview](https://raw.githubusercontent.com/yhwh-script/yhwh-script/refs/heads/main/docs/animals_li.png)

## Feedback

If you still have questions please let me know. Your opinion is valuable to me and sharing what you think is higly appreciated! If you have any feedback and want to share your suggestions please consider the contribution guidelines and reach out to @jahro_me
