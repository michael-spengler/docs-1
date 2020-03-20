# RmDir Methods

The `RmDir` object helps you create your own custom unlink method.

## Usage

Invoke it and chain the methods:

```javascript
new srm.RmDir()
  .random()
  .rmDir()
```

::: warning Unless you know what you’re doing, always end with `.rmDir()`. :::

## log\(\)

* No arguments

Help to construct the tree of erased directories.

## then\(fun\)

* **fun**: `(p: string, uuid: string) => Promise<string>`

Your custom function to apply on the directory.

```javascript
new srm.RmDir()
  .then(function (p) {
    return new Promise((resolve, reject) => {
      if (p === '/d/code/')
        reject(new Error())
      else
        resolve(p)
    })
  })
  .rmdir()
```

## rename\(\)

* No arguments.

Rename the directory to a random string of length `12`.

## rmdir\(\)

* No arguments.

The last function to be executed: remove the directory.

Required, invalid standard if omitted.

## compile

Use this to compile the standard without rmDir.

Useful for preview and testing uses.

Used in `rmdir()`.

```javascript
new RmDir()
  .log()
  .compile
```

