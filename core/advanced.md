# Advanced

## The `srm` Object

You can import each property individually:

{% tabs %}
{% tab title="ES6" %}
```javascript
import srm, { remove, /* ... */, standards, fileMethods } from 'secure-rm'
```
{% endtab %}

{% tab title="CommonJS" %}
```javascript
const { remove, /* ... */, standards, fileMethods } = require('secure-rm')
```
{% endtab %}
{% endtabs %}

Or get the properties from `srm`:

```javascript
srm.remove
srm.standards
srm.fileMethods
// ...
```

`srm` : The remove function by default with ES6.

* `remove`: The remove function.
* `eventEmitter`: event object to follow the process. See [Events](events.md).
* `standards`: the object containing default standards.
* `fileMethods`: file methods used to create standards.
* `dirMethods`: directory methods used to create standards.

## The `remove` Function

**`remove(path[, options, callback])`**

* `path`:
  * an absolute path \(e.g. `D:\data`, `/d/data`\);
  * a relative path \(e.g. `./data/file.js`, `../../data`\);
* `options`\(optional\) :
  * `standard`: ID of the standard \(default: 'secure'\);
  * `customStandard`: your own standard to remove a file \(if specified, priority over `standard`\);
  * `maxBusyTries`: number of retries if an error occur;
* `callback` \(if missing, return a promise\):
  * return `err` when finished.

