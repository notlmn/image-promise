# image-promise

> Load an image and return a promise in the browser, in 0.4KB, no dependencies

[![gzipped size](https://badges.herokuapp.com/size/github/bfred-it/image-promise/master/dist/image-promise.browser.js?gzip=true&label=gzipped%20size)](#readme) [![Travis build status](https://api.travis-ci.org/bfred-it/image-promise.svg?branch=master)](https://travis-ci.org/bfred-it/image-promise) [![gzipped size](https://img.shields.io/npm/v/image-promise.svg)](https://www.npmjs.com/package/image-promise) 

## Install

```sh
npm install --save image-promise
```
```js
import loadImage, {unload as unloadImage} from 'image-promise';
```

If you don't use node/babel, include this:

```html
<script src="dist/image-promise.browser.js"></script>
```

It uses the ES2015 `window.Promise`, so if you need to support older browsers you need a polyfill.

## Usage

You can load a single image from its URL:

```js
loadImage('img.jpg').then(function (img) {
	console.log('Image loaded!', img);
}).catch(function () {
	console.error('Image failed to load :(');
});
```

`image-promise` also caches the generated `<img>` tags so successive calls with the same exact `src` string will return the same `<img>` tag and be resolve at the same time as the first one.

Because are `<img>` are cached internally, if you want to uncache and [unload them from memory](http://www.fngtps.com/2010/mobile-safari-image-resource-limit-workaround/), call the `unload` method on the same `src`:

```js
loadImage.unload('img.jpg');

// or, if you use ES2015:
unloadImage('img.jpg')
```

## Dependencies

None! But you might need to polyfill `window.Promise`

## License

MIT © [Federico Brigante](http://twitter.com/bfred_it)