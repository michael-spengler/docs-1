---
description: >-
  You have the possibility to create your own standard by chaining differents
  methods. You can even add your own function with then.
---

# Custom Standard

## 📘 Usage

```javascript
const unlinkStandard = new srm.Unlink()
  .log()
  .random()
  .then(function (file, fileSize) {
    return new Promise((resolve, reject) => {
      if (file === 'test.js')
        reject(new Error())
      else
        resolve({ file, fileSize })
    })
  })
  .ones()
  .unlink()

const rmdirStandard = new srm.rmDir()
  .log()
  .rmDir()

const options = {
  customStandard: new srm.Standard({
    unlinkStandard,
    rmdirStandard
  })
}

srm('./*', options, (err, fileTree) => {
  if (err) throw err
  console.log(`Successfully removed ${fileTree} !`)
})
```

Use the classes `Unlink` and `rmDir` to construct your standard. Browse all the functions here:

{% page-ref page="unlink-methods.md" %}

{% page-ref page="rmdir-methods.md" %}

Another possibility is to add your standard to the `srm.standards` object to retrieve it at any time and add properties:

```javascript
srm.standards.myStandardName = new Standard({
  name: 'My Standard Name',
  passes: 3,
  description: 'My standard description!',
  unlinkStandard: new Unlink()
    .log()
    .random()
    .rename()
    .ones()
    .unlink(),
  rmdirStandard: new RmDir()
    .log()
    .rmDir()
})
```

