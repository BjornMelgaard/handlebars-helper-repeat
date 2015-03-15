# handlebars-helper-repeat [![NPM version](https://badge.fury.io/js/handlebars-helper-repeat.svg)](http://badge.fury.io/js/handlebars-helper-repeat)  [![Build Status](https://travis-ci.org/helpers/handlebars-helper-repeat.svg)](https://travis-ci.org/helpers/handlebars-helper-repeat) 

> Handlebars block helper for repeating whatever is inside the block `n` number of times.

If you find a bug or have a feature request, [please create an issue](https://github.com/helpers/handlebars-helper-repeat/issues).

## Install with [npm](npmjs.org)

```bash
npm i handlebars-helper-repeat --save
```

## Usage

```js
var helper = require('handlebars-helper-repeat');
```

## Register with handlebars

```js
var handlebars = require('handlebars');

// 2. register the helper, name it whatever you want
handlebars.registerHelper('repeat', helper);

// 3. register some partials
handlebars.registerPartial('button', '<button>{{text}}</button>');

// 4. use in templates
handlebars.compile('{{repeat 2}}{{> button }}{{/repeat}}')({text: 'Click me!'});
//=> '<button>Click me!</button><button>Click me!</button>'
```

## Usage Examples

**Private variables**

A few private variables are exposed to blocks:

- `count` the total number of blocks being generated
- `index` the index of the current block
- `start` the start number to use instead of zero. Basically `index + start`

Example:

```handlebars
{{#repeat count=2 start=17}}
  {{> button }}<span>{{@index}}</span>
{{else}}
  Nothing :(
{{/repeat}}
```
Results in something like:

```html
<button>Click me!</button><span>17</span>
<button>Click me!</button><span>18</span>
```

**Index**

Output the index of the current block:

```handlebars
{{#repeat '2'}}
<div id="{{@index}}">
  {{> button }}
</div>
{{/repeat}}
```

Results in something like:

```html
<div id="0">
  <button>Click me</button>
</div>
<div id="1">
  <button>Click me</button>
</div>
```

## Related projects
* [template-helpers](https://github.com/jonschlinkert/template-helpers): Generic JavaScript helpers that can be used with any template engine. Handlebars, Lo-Dash, Underscore, or any engine that supports helper functions.
* [handlebars-helpers](https://github.com/assemble/handlebars-helpers): 120+ Handlebars helpers in ~20 categories, for Assemble, YUI, Ghost or any Handlebars project. Includes helpers like {{i18}}, {{markdown}}, {{relative}}, {{extend}}, {{moment}}, and so on.

## Contributing
Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/helpers/handlebars-helper-repeat/issues)

## Running tests
Install dev dependencies.

```bash
npm i -d && npm test
```

## Authors

**Jon Schlinkert**
 
+ [github/jonschlinkert](https://github.com/jonschlinkert)
+ [twitter/jonschlinkert](http://twitter.com/jonschlinkert) 

## License
Copyright (c) 2015 Jon Schlinkert  
Released under the MIT license

***

_This file was generated by [verb-cli](https://github.com/assemble/verb-cli) on March 15, 2015._