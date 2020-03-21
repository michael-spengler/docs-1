# Installation

## 📦 Installation

[Node.js](https://nodejs.org/) and [npm](https://www.npmjs.com/) required.

```bash
npm install secure-rm
```

Looking for a **command-line interface**? [Click here.](https://www.npmjs.com/package/secure-rm-cli)

## 🚀 Getting started

If you want your application to delete specific files with a pass of cryptographically strong pseudo-random data, use one of these code snippets:

{% tabs %}
{% tab title="ES6" %}
```javascript
import srm from 'secure-rm'
```
{% endtab %}

{% tab title="CommonJS" %}
```javascript
const srm = require('secure-rm')
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Promise" %}
```javascript
srm('./folder/*.js')
  .then(() => console.log('Files successfully deleted !'))
  .catch((err) => {throw err})
```
{% endtab %}

{% tab title="Callback" %}
```javascript
const srm = require('secure-rm')

srm('./folder/*.js', (err) => {
  if (err) throw err
  console.log('Files successfully deleted !')
})
```
{% endtab %}
{% endtabs %}

## Examples:

{% tabs %}
{% tab title="Promise" %}
```javascript
const options = {
  standard: 'gutmann',
  maxBusyTries: 5,
  disableGlob: true
}

srm('./data/*.js', options)
  .then(() => console.log('Files successfully deleted !'))
  .catch((err) => {throw err})

srm('./trash/dir/', { standard: 'preview' })
  .then((fileTree) => console.log('Files that would be deleted:' + fileTree))
  .catch((err) => {throw err})
```
{% endtab %}

{% tab title="Callback" %}
```javascript
const options = {
  standard: 'gutmann',
  maxBusyTries: 5,
  disableGlob: true
}

srm('./data/*.js', options, (err) => {
  if (err) throw err
  console.log('Files successfully deleted !')
})

srm('./trash/dir/', { standard: 'preview' }, (err, fileTree) => {
  if (err) throw err
  console.log('Files that would be deleted:' + fileTree)
})
```
{% endtab %}
{% endtabs %}

## The `srm` Object

When you import the library, you can do this in two different ways:

```javascript
const srm = require('secure-rm')
```

And then get the properties:

```javascript
srm.event
srm.Unlink
srm.validIDs
// ...
```

Or you can import each property:

{% tabs %}
{% tab title="ES6" %}
```javascript
import srm, { event, /* ... */, validIDs, Standard } from 'secure-rm'
```
{% endtab %}

{% tab title="CommonJS" %}
```javascript
const { event, /* ... */, validIDs, Standard } = require('secure-rm')
```
{% endtab %}
{% endtabs %}

`srm` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function) : The main function, as described [under]().

* `event` [\](https://nodejs.org/dist/latest-v12.x/docs/api/events.html) : event object to follow the process, See \[\[Events\]\];
* `Unlink` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/class) : the class to create and compile unlink standards. See \[\[Unlink Methods\]\];
* `RmDir` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/class) : the class to create and compile rmDir standards. See \[\[RmDir Methods\]\];
* `Standard` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/class) : the class to create and compile standards. See \[\[Standards\]\] and \[\[Custom Standard\]\];
* `validIDs` [Array\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#String_type) : array containing valid text IDs of standards;
* `standards` [\Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) : the object containing default standards.

## The `srm` Function

**`rm(path[, options] [, callback])`**

* `path` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#String_type) :
  * an absolute path \(e.g. `D:\data`, `/d/data`\);
  * a relative path \(e.g. `./data/file.js`, `../../data`\);
  * a [glob pattern](https://www.npmjs.com/package/glob#glob-primer) \(e.g. `./*.js`, `./**/*`, `@(pattern|pat*|pat?erN)`\).
* `options` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) \(optional\) :
  * `standard` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#String_type) : ID of the standard \(default: 'secure'\);
  * `customStandard` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function) : your own standard to remove a file \(if specified, priority over `standard`\);
  * `maxBusyTries` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#Number_type) : number of retries if an error occur;
  * `disableGlob` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#Boolean_type) : allow or not file globbing \(default: true\).
* `callback` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function) \(if missing, return a promise\):
  * returns `err` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error) when finished.

## 📜 Changelog / History

See the [changelog](https://github.com/secure-rm/core/blob/master/CHANGELOG.md) or [releases](https://github.com/secure-rm/core/releases).

## 🏗 Contributing

 [![Dependencies](https://img.shields.io/librariesio/release/npm/secure-rm?style=flat-square&logo=npm)](https://libraries.io/npm/secure-rm) ![Contributors](https://img.shields.io/github/contributors/secure-rm/core?style=flat-square) ![Last commit](https://img.shields.io/github/last-commit/secure-rm/core/develop?style=flat-square) ![npm collaborators](https://img.shields.io/npm/collaborators/secure-rm?style=flat-square)

 [![Tested with Jest](https://img.shields.io/badge/-jest-99424f?style=flat-square&logo=jest)](https://jestjs.io) [![Node version](https://img.shields.io/badge/-node-gray?style=flat-square&logo=node.js)](https://nodejs.org) [![language](https://img.shields.io/badge/-typescript-blue?style=flat-square&logo=typescript)](https://www.typescriptlang.org/)

See [contributing guidelines](https://github.com/secure-rm/core/blob/master/CONTRIBUTING.md)

### Licensing

This project is under [MIT License](https://github.com/secure-rm/core/blob/master/LICENSE).

