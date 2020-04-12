---
description: >-
  You have the possibility to create your own standard by chaining differents
  methods. You can even add your own function with then.
---

# Custom Standard

## 📘 Usage

```javascript
const unlink = function (path, cb) {
  const remove = async () => {
    const fileData = await file.init(path)
    await file.random(fileData)
    // other functions
    await file.end(fileData)
  }
  remove().then(_ => cb(null)).catch(cb)
}

const rmdir = function (path, cb) {
  const remove = async () => {
    path = await dir.rename(path)
    // other functions
    await dir.end(path)
  }
  remove().then(_ => cb(null)).catch(cb)
}

const options = {
  standard: {
    unlink,
    rmdir
  }
}

srm.remove('./folder/', options)
  .then(() => console.log('Files successfully deleted !'))
  .catch(console.error)
```

{% page-ref page="file-methods.md" %}

{% page-ref page="dir-methods.md" %}

Another possibility is to add your standard to the `srm.standards` object to retrieve it at any time and add properties:

```javascript
srm.standards.myStandardName = {
  unlink: function (path, cb) {
    const remove = async () => {
      const fileData = await file.init(path)
      await file.random(fileData)
      // other functions
      await file.end(fileData)
    }
    remove().then(_ => cb(null)).catch(cb)
  },
  rmdir: function (path, cb) {
    const remove = async () => {
      path = await dir.rename(path)
      // other functions
      await dir.end(path)
    }
    remove().then(_ => cb(null)).catch(cb)
  }
}
```

