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
srm('./folder/*.js')
  .then(() => console.log('Files successfully deleted !'))
  .catch((err) => {throw err})
```
{% endtab %}

{% tab title="Callback" %}
```javascript
srm('./folder/*.js', (err) => {
  if (err) throw err
  console.log('Files successfully deleted !')
})
```
{% endtab %}
{% endtabs %}

## ⚙️Using options

You can set options in the `srm` function:

{% tabs %}
{% tab title="Promise" %}
```javascript
const options = { /*...*/ }

srm('./data/*.js', options)
  .then(() => console.log('Files successfully deleted !'))
  .catch((err) => {throw err})
```
{% endtab %}

{% tab title="Callback" %}
```javascript
const options = { /*...*/ }

srm('./data/*.js', options, (err) => {
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
const options = {
  standard: 'gutmann'
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
  standard: 'gutmann'
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

{% page-ref page="standards.md" %}

### Miscellaneous 

{% tabs %}
{% tab title="Promise" %}
```javascript
const options = {
  maxBusyTries: 5,
  disableGlob: true,
  customStandard: new srm.Standard(/*...*/)
}

srm('./data/*.js', options)
  .then(() => console.log('Files successfully deleted !'))
  .catch((err) => {throw err})
```
{% endtab %}

{% tab title="Callback" %}
```javascript
const options = {
  maxBusyTries: 5,
  disableGlob: true
}

srm('./data/*.js', options, (err) => {
  if (err) throw err
  console.log('Files successfully deleted !')
})
```
{% endtab %}
{% endtabs %}

#### **emfileWait**

If an `EBUSY`, `ENOTEMPTY`, or `EPERM` error code is encountered on Windows systems, then secure-rm will retry with a linear backoff wait of 100ms longer on each try. The default maxBusyTries is 3.

#### **disableGlob**

Set to any non-falsey value to disable globbing entirely.

#### **customStandard**

Create your own standard using the different methods provided or even your own.

{% page-ref page="custom-standard/" %}

## 📜 [Changelog](https://github.com/secure-rm/core/blob/master/CHANGELOG.md) / [Releases](https://github.com/secure-rm/core/releases)

## 🏗️ Contributing

 [![Dependencies](https://img.shields.io/librariesio/release/npm/secure-rm?style=flat-square&logo=npm)](https://libraries.io/npm/secure-rm) ![Contributors](https://img.shields.io/github/contributors/secure-rm/core?style=flat-square) ![Last commit](https://img.shields.io/github/last-commit/secure-rm/core/develop?style=flat-square) ![npm collaborators](https://img.shields.io/npm/collaborators/secure-rm?style=flat-square)

 [![Tested with Jest](https://img.shields.io/badge/-jest-99424f?style=flat-square&logo=jest)](https://jestjs.io) [![Node version](https://img.shields.io/badge/-node-gray?style=flat-square&logo=node.js)](https://nodejs.org) [![language](https://img.shields.io/badge/-typescript-blue?style=flat-square&logo=typescript)](https://www.typescriptlang.org/)

See [contributing guidelines](https://github.com/secure-rm/core/blob/master/CONTRIBUTING.md).

