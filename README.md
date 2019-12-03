# A Stimulus Controller to setup the Shopify App Bridge

## Warning

This is in no way production ready, please help make it so ;)


## Getting started

This assumes that you have [Stimulus](https://stimulusjs.org/handbook/installing) already installed.

In your project just add the `stimulus-shopify-app-bridge` package.

```bash
$ yarn add stimulus-shopify-app-bridge
```

or

```bash
$ npm i stimulus-shopify-app-bridge
```


### Define your html

Make sure to include

```html
<div data-controller="home">
    ...page content here
</div>
```

Somewhere on every page, also include:

```html
<div id="shopify-app-init" data-api-key="<YOUR-SHOPIFY-API-KEY>" data-shop-origin="<SOMESHOP.MYSHOPIFY.COM>"></div>
```

### Define your page controllers by extending `stimulus-shopify-app-bridge`

```js
// ./controllers/home_controller.js
import AppBridgeController from "stimulus-shopify-app-bridge";
import { Button } from '@shopify/app-bridge/actions'

// create a parent controller by extending stimulus-conductor controller
export default class extends AppBridgeController {
  initialize() {
    super.initialize();
    // if you overwrite initialize you must call super first!!!!
    // const app = this.appBridge
    // const flashButton = Button.create(app, { label: 'Show flash' })
    // const titleBarOptions = {
    //   title: 'Show',
    //   buttons: {
    //     primary: [flashButton]
    //   }
    // }
    // flashButton.subscribe(Button.Action.CLICK, data => {
    //   this.flashNotice('Hello World!')
    // })
    // this.appTitleBar = this.createAppTitleBar(app, titleBarOptions)
  }

  connect() {
    super.connect();
    // if you overwrite connect you must call super!!!!
    // this.appBridge is availble here
  }

  disconnect() {
    super.disconnect();
    // if you overwrite disconnect you must call super!!!!
    // this.appBridge is availble here
  }
}
```

### Conventions

The app bridge controller creates the app and sets up the following helpers:

> - `this.appBridge` This is the actual app instance, which can be passed to actions etc.
> - `this.appHistory`
> - `this.appRedirect`
> - `this.appLoading`
> - `this.createAppTitleBar(this.appBridge, titleBarOptions)`
> - `this.flashNotice(message)`
> - `this.flashError(message)`


## Limitations

Currently it only works with inherited controllers, and Turbolinks events are not handled for loading indicators.

## Contributing

Bug reports and pull requests are welcome.

**To contribute:**

Fork the project.

Install dependencies

`$ yarn install`


You can test locally also the results with the playground project (`yarn start`)

**Then :**

👍 Write some tests

💪 Add your feature

🚀 Send a PR

## License

This package is available as open source under the terms of the MIT License.
