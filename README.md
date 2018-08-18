<br>

<p align='center'><img src='docs/images/remount.png' width='500'></p>

<p align='center'>
<a href='https://codepen.io/rstacruz/pen/EpBZRv?editors=1010'>Demo</a> ⚡ <a href='https://github.com/rstacruz/remount#remount'>Docs</a>
<br>
1kb gzip'd &nbsp;&middot;&nbsp; No dependencies &nbsp;&middot;&nbsp; IE9 support
</p>

<br>

# Remount

> 🔌 Mount React components to the DOM using custom elements

_Experimental_ - Remount lets you use your React components anywhere in the page as a web component (custom element).

[![Status](https://travis-ci.org/rstacruz/remount.svg?branch=master)](https://travis-ci.org/rstacruz/remount 'See test builds')

## Installation

Remount is available through the [npm package repository](https://yarnpkg.com/en/package/remount).

- Via yarn: `yarn add remount`
- or npm: `npm install remount`

Be sure to use the [recommended polyfills](#polyfills) below as well!

## Usage

Given any React component, such as this:

```js
const Greeter = ({ name }) => {
  return <div>Hello, {name}!</div>
}
```

You can use _define()_ to define custom elements. Let's define `<x-greeter>` like so:

```js
import { define } from 'remount'

define({
  'x-greeter': Greeter
})
```

You can then use it in your HTML, or even in your other React components!

```html
<x-greeter props-json='{"name":"John"}'></x-greeter>
```

➡️ More at **[API documentation](docs/api.md)**

## Use cases

Some ideas on why you might want to consider Remount for your project:

|                                                    |                                                                                                                                                                                                            |
| -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img src='http://source.unsplash.com/350x250?sea'> | ✨ **Adding React to non-SPA apps** <br> You can use React components on any page of a "regular" HTML site. Great for adding React to apps built on Rails or Phoenix.                                      |
|                                                    |                                                                                                                                                                                                            |
| <img src='http://source.unsplash.com/350x250?sun'> | 💞 **Interop with other frameworks** <br> Remount lets you use your React components just like any other HTML element. This means you can use React with Vue, Angular, or any other DOM library/framework. |
|                                                    |                                                                                                                                                                                                            |

## Custom properties

> `<x-greeter name="John"></x-greeter>`

Only the `props-json` attribute is supported by default. To support custom properties like above, pass the names of attributes you want Remount to use.

```js
import { define } from 'remount'

define({
  'x-greeter': {
    component: Greeter,
    attributes: ['name']
  }
})
```

## Limitations

Remount relies on the [Custom Elements](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements) HTML API, so all limitations of the Custom Elements API apply. Keep these in mind:

- Custom components names require a hyphen, and are case insensitive.
- Attributes are case insensitive.

## Browser support

Remount supports all browsers [supported by React](https://reactjs.org/docs/react-dom.html#browser-support). Use the polyfills below to ensure the best compatibility.

## Polyfills

We recommend these two polyfills provided by the [@webcomponents/webcomponentsjs][@webcomponents/webcomponentsjs] package. Load it via JavaScript in your app's entry point:

```js
// Add the package via: yarn add @webcomponents/webcomponentsjs
import '@webcomponents/webcomponentsjs/custom-elements-es5-adapter.js'
import '@webcomponents/webcomponentsjs/webcomponents-loader.js'
```

Or you can load it via CDN:

```html
<script crossorigin src='https://cdn.jsdelivr.net/npm/@webcomponents/webcomponentsjs@2.0.4/custom-elements-es5-adapter.js'></script>
<script crossorigin src='https://cdn.jsdelivr.net/npm/@webcomponents/webcomponentsjs@2.0.4/webcomponents-loader.js'></script>
```

[@webcomponents/webcomponentsjs]: https://yarn.pm/@webcomponents/webcomponentsjs

More info at the [Polyfills documentation](./docs/polyfills.md).

## More info

- [Builds](./docs/builds.md) &mdash; ES2015+ and ES Module builds are also provided.
- [API documentation](./docs/api.md)
- [Frequently-asked questions](./docs/faq.md)
- [Comparison with alternatives](./docs/comparison.md)
- [Polyfills](./docs/polyfills.md)

## Thanks

**remount** © 2018, Rico Sta. Cruz. Released under the [MIT] License.<br>
Authored and maintained by Rico Sta. Cruz with help from contributors ([list][contributors]).

> [ricostacruz.com](http://ricostacruz.com) &nbsp;&middot;&nbsp;
> GitHub [@rstacruz](https://github.com/rstacruz) &nbsp;&middot;&nbsp;
> Twitter [@rstacruz](https://twitter.com/rstacruz)

[mit]: http://mit-license.org/
[contributors]: http://github.com/rstacruz/remount/contributors

<br>

[![](https://img.shields.io/github/followers/rstacruz.svg?style=social&label=@rstacruz)](https://github.com/rstacruz) &nbsp;
[![](https://img.shields.io/twitter/follow/rstacruz.svg?style=social&label=@rstacruz)](https://twitter.com/rstacruz) <br>
