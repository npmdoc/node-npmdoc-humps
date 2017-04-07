# api documentation for  [humps (v2.0.0)](https://github.com/domchristie/humps)  [![npm package](https://img.shields.io/npm/v/npmdoc-humps.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-humps) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-humps.svg)](https://travis-ci.org/npmdoc/node-npmdoc-humps)
#### Underscore-to-camelCase converter (and vice versa) for strings and object keys in JavaScript.

[![NPM](https://nodei.co/npm/humps.png?downloads=true)](https://www.npmjs.com/package/humps)

[![apidoc](https://npmdoc.github.io/node-npmdoc-humps/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-humps_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-humps/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-humps/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-humps/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Dom Christie"
    },
    "bugs": {
        "url": "https://github.com/domchristie/humps/issues"
    },
    "dependencies": {},
    "description": "Underscore-to-camelCase converter (and vice versa) for strings and object keys in JavaScript.",
    "devDependencies": {
        "mocha": "^2.2.5"
    },
    "directories": {},
    "dist": {
        "shasum": "dd4a423e9784626fe7b9f19fde0baff659b40173",
        "tarball": "https://registry.npmjs.org/humps/-/humps-2.0.0.tgz"
    },
    "gitHead": "050b1fd852cf0847bed9513655b2afbb20d89859",
    "homepage": "https://github.com/domchristie/humps",
    "keywords": [
        "utils",
        "camel",
        "case",
        "underscore",
        "converter",
        "strings",
        "objects"
    ],
    "license": "MIT",
    "main": "humps.js",
    "maintainers": [
        {
            "name": "domchristie",
            "email": "christiedom@gmail.com"
        }
    ],
    "name": "humps",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/domchristie/humps.git"
    },
    "scripts": {
        "test": "mocha"
    },
    "version": "2.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module humps](#apidoc.module.humps)
1.  [function <span class="apidocSignatureSpan">humps.</span>camelize (string)](#apidoc.element.humps.camelize)
1.  [function <span class="apidocSignatureSpan">humps.</span>camelizeKeys (object, options)](#apidoc.element.humps.camelizeKeys)
1.  [function <span class="apidocSignatureSpan">humps.</span>decamelize (string, options)](#apidoc.element.humps.decamelize)
1.  [function <span class="apidocSignatureSpan">humps.</span>decamelizeKeys (object, options)](#apidoc.element.humps.decamelizeKeys)
1.  [function <span class="apidocSignatureSpan">humps.</span>depascalize (string, options)](#apidoc.element.humps.depascalize)
1.  [function <span class="apidocSignatureSpan">humps.</span>depascalizeKeys ()](#apidoc.element.humps.depascalizeKeys)
1.  [function <span class="apidocSignatureSpan">humps.</span>pascalize (string)](#apidoc.element.humps.pascalize)
1.  [function <span class="apidocSignatureSpan">humps.</span>pascalizeKeys (object, options)](#apidoc.element.humps.pascalizeKeys)



# <a name="apidoc.module.humps"></a>[module humps](#apidoc.module.humps)

#### <a name="apidoc.element.humps.camelize"></a>[function <span class="apidocSignatureSpan">humps.</span>camelize (string)](#apidoc.element.humps.camelize)
- description and source-code
```javascript
camelize = function (string) {
  if (_isNumerical(string)) {
    return string;
  }
  string = string.replace(/[\-_\s]+(.)?/g, function(match, chr) {
    return chr ? chr.toUpperCase() : '';
  });
  // Ensure 1st char is always lowercase
  return string.substr(0, 1).toLowerCase() + string.substr(1);
}
```
- example usage
```shell
...
Takes inspiration from [Ember Data](https://github.com/emberjs/data) and copies some utility functions from [Underscore.js](http
://underscorejs.org/).

Usage
-----

### Converting strings

humps.camelize('hello_world') // 'helloWorld'
humps.decamelize('fooBar') // 'foo_bar'
humps.decamelize('fooBarBaz', { separator: '-' }) // 'foo-bar-baz'

### Converting object keys

var object = { attr_one: 'foo', attr_two: 'bar' }
humps.camelizeKeys(object); // { attrOne: 'foo', attrTwo: 'bar' }
...
```

#### <a name="apidoc.element.humps.camelizeKeys"></a>[function <span class="apidocSignatureSpan">humps.</span>camelizeKeys (object, options)](#apidoc.element.humps.camelizeKeys)
- description and source-code
```javascript
camelizeKeys = function (object, options) {
  return _processKeys(_processor(camelize, options), object);
}
```
- example usage
```shell
...
    humps.camelize('hello_world') // 'helloWorld'
    humps.decamelize('fooBar') // 'foo_bar'
    humps.decamelize('fooBarBaz', { separator: '-' }) // 'foo-bar-baz'

### Converting object keys

    var object = { attr_one: 'foo', attr_two: 'bar' }
    humps.camelizeKeys(object); // { attrOne: 'foo', attrTwo: 'bar' }

Arrays of objects are also converted

    var array = [{ attr_one: 'foo' }, { attr_one: 'bar' }]
    humps.camelizeKeys(array); // [{ attrOne: 'foo' }, { attrOne: 'bar' }]

It also accepts a callback which can modify the conversion behavior. For example to prevent conversion of keys containing only uppercase
 letters or numbers:
...
```

#### <a name="apidoc.element.humps.decamelize"></a>[function <span class="apidocSignatureSpan">humps.</span>decamelize (string, options)](#apidoc.element.humps.decamelize)
- description and source-code
```javascript
decamelize = function (string, options) {
  return separateWords(string, options).toLowerCase();
}
```
- example usage
```shell
...

Usage
-----

### Converting strings

humps.camelize('hello_world') // 'helloWorld'
humps.decamelize('fooBar') // 'foo_bar'
humps.decamelize('fooBarBaz', { separator: '-' }) // 'foo-bar-baz'

### Converting object keys

var object = { attr_one: 'foo', attr_two: 'bar' }
humps.camelizeKeys(object); // { attrOne: 'foo', attrTwo: 'bar' }
...
```

#### <a name="apidoc.element.humps.decamelizeKeys"></a>[function <span class="apidocSignatureSpan">humps.</span>decamelizeKeys (object, options)](#apidoc.element.humps.decamelizeKeys)
- description and source-code
```javascript
decamelizeKeys = function (object, options) {
  return _processKeys(_processor(decamelize, options), object, options);
}
```
- example usage
```shell
...
humps.camelizeKeys(array); // [{ attrOne: 'foo' }, { attrOne: 'bar' }]

It also accepts a callback which can modify the conversion behavior. For example to prevent conversion of keys containing only uppercase
 letters or numbers:

humps.camelizeKeys(obj, function (key, convert) {
  return /^[A-Z0-9_]+$/.test(key) ? key : convert(key);
});
humps.decamelizeKeys(obj, function (key, convert, options) {
  return /^[A-Z0-9_]+$/.test(key) ? key : convert(key, options);
});

In order to use the callback with options use the 'process' option:

humps.decamelizeKeys(obj, {
    separator: '-',
...
```

#### <a name="apidoc.element.humps.depascalize"></a>[function <span class="apidocSignatureSpan">humps.</span>depascalize (string, options)](#apidoc.element.humps.depascalize)
- description and source-code
```javascript
depascalize = function (string, options) {
  return separateWords(string, options).toLowerCase();
}
```
- example usage
```shell
...

By default, 'decamelize' will only split words on capital letters (not numbers as in humps pre v1.0). To customize this behaviour
, use the 'split' option. This should be a regular expression which, when passed into 'String.prototype.split', produces an array
 of words (by default the regular expression is: '/(?=[A-Z])/'). For example, to treat numbers as uppercase:

'''javascript
humps.decamelize('helloWorld1', { split: /(?=[A-Z0-9])/ }) // 'hello_world_1'
'''

### 'humps.depascalize(string, options)'

Same as 'humps.decamelize' above.

### 'humps.camelizeKeys(object, options)'

Converts object keys to camelCase. It also converts arrays of objects.
...
```

#### <a name="apidoc.element.humps.depascalizeKeys"></a>[function <span class="apidocSignatureSpan">humps.</span>depascalizeKeys ()](#apidoc.element.humps.depascalizeKeys)
- description and source-code
```javascript
depascalizeKeys = function () {
  return this.decamelizeKeys.apply(this, arguments);
}
```
- example usage
```shell
...

Converts object keys to PascalCase. It also converts arrays of objects.

### 'humps.decamelizeKeys(object, options)'

Separates camelCased object keys with an underscore. It also converts arrays of objects. See 'humps.decamelize' for details of options
.

### 'humps.depascalizeKeys(object, options)'

See 'humps.decamelizeKeys'.

Licence
-------
humps is copyright &copy; 2012+ [Dom Christie](http://domchristie.co.uk) and released under the MIT license.
...
```

#### <a name="apidoc.element.humps.pascalize"></a>[function <span class="apidocSignatureSpan">humps.</span>pascalize (string)](#apidoc.element.humps.pascalize)
- description and source-code
```javascript
pascalize = function (string) {
  var camelized = camelize(string);
  // Ensure 1st char is always uppercase
  return camelized.substr(0, 1).toUpperCase() + camelized.substr(1);
}
```
- example usage
```shell
...

Removes any hypens, underscores, and whitespace characters, and uppercases the first character that follows.

'''javascript
humps.camelize('hello_world-foo bar') // 'helloWorldFooBar'
'''

### 'humps.pascalize(string)'

Similar to 'humps.camelize(string)', but also ensures that the first character is uppercase.

'''javascript
humps.pascalize('hello_world-foo bar') // 'HelloWorldFooBar'
'''
...
```

#### <a name="apidoc.element.humps.pascalizeKeys"></a>[function <span class="apidocSignatureSpan">humps.</span>pascalizeKeys (object, options)](#apidoc.element.humps.pascalizeKeys)
- description and source-code
```javascript
pascalizeKeys = function (object, options) {
  return _processKeys(_processor(pascalize, options), object);
}
```
- example usage
```shell
...

Same as 'humps.decamelize' above.

### 'humps.camelizeKeys(object, options)'

Converts object keys to camelCase. It also converts arrays of objects.

### 'humps.pascalizeKeys(object, options)'

Converts object keys to PascalCase. It also converts arrays of objects.

### 'humps.decamelizeKeys(object, options)'

Separates camelCased object keys with an underscore. It also converts arrays of objects. See 'humps.decamelize' for details of options
.
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
