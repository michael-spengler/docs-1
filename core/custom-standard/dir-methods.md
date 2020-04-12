---
description: The RmDir object helps you create your own custom unlink method.
---

# Directories Methods

## 📘 Usage

```javascript
path = await dir.rename(path)
await dir.end(path)
```

{% hint style="danger" %}
Unless you know what you’re doing, always end with `dir.end`.
{% endhint %}

## mark \(folderName\)

* **folderName**: `string`

Help to construct a tree of erased directories.

## rename \(folderName\)

* **folderName**: `string`

Rename the directory to a random string of length `12`.

## end \(folderName\)

* **folderName**: `string`

Mandatory to delete folder.

