# Advanced

## The `srm` Object

You can import each property individually:

{% tabs %}
{% tab title="ES6" %}
```javascript
import srm, { event, /* ... */, validIDs, Standard } from 'secure-rm'
```
{% endtab %}

{% tab title="CommonJS" %}
```javascript
const srm, { event, /* ... */, validIDs, Standard } = require('secure-rm')
```
{% endtab %}
{% endtabs %}

Or get the properties from `srm`:

```javascript
srm.event
srm.Unlink
srm.validIDs
// ...
```

`srm` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function) : The main function, as described under.

* `event` [\](https://nodejs.org/dist/latest-v12.x/docs/api/events.html) : event object to follow the process. See [Events](events.md);
* `Unlink` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/class) : the class to create and compile unlink standards. See [Unlink Methods](custom-standard/unlink-methods.md);
* `RmDir` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/class) : the class to create and compile rmDir standards. See [RmDir Methods](custom-standard/rmdir-methods.md);
* `Standard` [\](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/class) : the class to create and compile standards. See [Standards](standards.md) and [Custom Standard](custom-standard/);
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

