# Getting Started

## 📦 Installation

This is a Node.js library, so you must have [Node.js](https://nodejs.org/) and [npm](https://www.npmjs.com/) / [yarn](https://yarnpkg.com/) installed on your system.

```bash
$ yarn add secure-rm
# or
$ npm install secure-rm
```

## 🚀 Quick Start

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

If you want your application to delete specific files with a pass of cryptographically strong pseudo-random data, use one of these code snippets:

{% tabs %}
{% tab title="Promise" %}
```javascript
srm.remove('./folder/file.js')
  .then(() => console.log('Files successfully deleted !'))
  .catch(console.error)
```
{% endtab %}

{% tab title="Callback" %}
```javascript
srm.remove('./folder/file.js', (err) => {
  if (err) throw err
  console.log('Files successfully deleted !')
})
```
{% endtab %}
{% endtabs %}

Path can be a directory or a file.

## ⚙️Using options

You can set options in the `srm.remove` function:

{% tabs %}
{% tab title="Promise" %}
```javascript
const options = { /*...*/ }

srm.remove('./data/file.js', options)
  .then(() => console.log('Files successfully deleted !'))
  .catch(console.error)
```
{% endtab %}

{% tab title="Callback" %}
```javascript
const options = { /*...*/ }

srm.remove('./data/file.js', options, (err) => {
  if (err) throw err
  console.log('Files successfully deleted !')
})
```
{% endtab %}
{% endtabs %}

### Standards

{% tabs %}
{% tab title="Promise" %}
```javascript
const standard = srm.standards.gutmann

srm.remove('./data/file.js', { standard })
  .then(() => console.log('Files successfully deleted !'))
  .catch(console.error)

srm.remove('./trash/dir/', { standard: srm.standards.schneier })
  .then(() => console.log('Files successfully deleted !'))
  .catch(console.error)
```
{% endtab %}

{% tab title="Callback" %}
```javascript
const standard = srm.standards.gutmann

srm.remove('./data/file.js', { standard }, (err) => {
  if (err) throw err
  console.log('Files successfully deleted !')
})

srm.remove('./trash/dir/', { standard: srm.standards.schneier }, (err, fileTree) => {
  if (err) throw err
  console.log('Files that would be deleted:' + fileTree)
})
```
{% endtab %}
{% endtabs %}

{% page-ref page="standards.md" %}

### Miscellaneous 

{% tabs %}
{% tab title="Promise" %}
```javascript
const options = {
  maxBusyTries: 5
}

srm.remove('./data/file.js', options)
  .then(() => console.log('Files successfully deleted !'))
  .catch(console.error)
```
{% endtab %}

{% tab title="Callback" %}
```javascript
const options = {
  maxBusyTries: 5
}

srm.remove('./data/file.js', options, (err) => {
  if (err) throw err
  console.log('Files successfully deleted !')
})
```
{% endtab %}
{% endtabs %}

**maxBusyTries**

If an `EBUSY`, `ENOTEMPTY`, or `EPERM` error code is encountered on Windows systems, then secure-rm will retry with a linear backoff wait of 100ms longer on each try. The default maxBusyTries is 3.

{% page-ref page="custom-standard/" %}

## 📜 [Changelog](https://github.com/secure-rm/core/blob/master/CHANGELOG.md) / [Releases](https://github.com/secure-rm/core/releases)

## 🏗️ Contributing

 [![Dependencies](https://img.shields.io/librariesio/release/npm/secure-rm?style=flat-square&logo=npm)](https://libraries.io/npm/secure-rm) ![Contributors](https://img.shields.io/github/contributors/secure-rm/core?style=flat-square) ![Last commit](https://img.shields.io/github/last-commit/secure-rm/core/develop?style=flat-square) ![npm collaborators](https://img.shields.io/npm/collaborators/secure-rm?style=flat-square)

 [![Tested with Jest](https://img.shields.io/badge/-jest-99424f?style=flat-square&logo=jest)](https://jestjs.io) [![Node version](https://img.shields.io/badge/-node-gray?style=flat-square&logo=node.js)](https://nodejs.org) [![language](https://img.shields.io/badge/-typescript-blue?style=flat-square&logo=typescript)](https://www.typescriptlang.org/)

See [contributing guidelines](https://github.com/secure-rm/core/blob/master/CONTRIBUTING.md).

