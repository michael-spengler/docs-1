---
description: The Unlink object helps you create your own custom unlink method.
---

# Unlink Methods

## b📘 Usage

Invoke it and chain the methods:

```javascript
new srm.Unlink()
  .random()
  .unlink()
```

{% hint style="danger" %}
Unless you know what you’re doing, always end with `.unlink()`.
{% endhint %}

## log\(\)

* No arguments

Help to construct the tree of erased files.

Used in `preview` standard.

## then\(fun\)

* **fun**: `(file: string, fileSize: number, uuid: string) => Promise<{ file: string, fileSize: number }>`

Your custom function to apply on the file.

```javascript
new srm.Unlink()
  .then(function (file, fileSize) {
    return new Promise((resolve, reject) => {
      if (file === 'test.js')
        reject(new Error())
      else
        resolve({ file, fileSize })
    })
  })
  .unlink()
```

## random\(passes\)

* **passes**: `number`
  * **default**: `1`
  * the number of times the function is executed.

Write cryptographically strong pseudo-random data.

## zeroes\(passes\)

* **passes**: `number`
  * **default**: `1`
  * the number of times the function is executed.

Write zeroes on the whole file.

## ones\(passes\)

* **passes**: `number`
  * **default**: `1`
  * the number of times the function is executed.

Write ones on the whole file.

## byte\(data, passes\)

* **data**: `number`
  * A byte: must be between `0x00` and `0xFF` \(Hexadecimal\)
* **passes**: `number`
  * **default**: `1`
  * the number of times the function is executed.

Write one byte on the whole file.

```javascript
new Unlink()
  .byte(0x55)
  .unlink()
```

## byteArray\(dataArray, passes\)

* **dataArray**: `number[]`
  * The array containing the bytes.
* **passes**: `number`
  * **default**: `1`
  * the number of times the function is executed.

Write an array of bytes on the whole file.

```javascript
new Unlink()
  .byteArray([0x92, 0x49, 0x24])
  .unlink()
```

## forByte\(options\)

* * **options**: `Object`
  * **init**: `number`
    * initialize the counter variable.
  * **condition**: `(i: number) => boolean`
    * An expression to be evaluated before each loop iteration.
  * **increment**: `(i: number) => number`
    * The increment of the counter variable after each loop iteration.

A `for` loop, write the value of the variable at each iteration.

```javascript
new Unlink()
  .forByte({
    init: 0x00,
    condition: i => i < 0xFF,
    increment: i => i + 0x11
  })
  .unlink()
```

## random\(passes\)

* **passes**: `number`
  * **default**: `1`
  * the number of times the function is executed.

Write one cryptographically strong pseudo-random byte on the whole file.

## complementary\(\)

* No arguments.

Write the binary complement of the file.

## rename\(\)

* No arguments.

Rename the file to a random string of length `12`.

## truncate\(\)

* No arguments.

Truncate to between 25% and 75% of the file size.

## unlink\(\)

* No arguments.

The last function to be executed: unlink the file pointer.

Required, invalid standard if omitted.

## compile

Use this to compile the standard without unlink.

Useful for preview and testing uses.

Used in `unlink()`.

```javascript
new Unlink()
  .log()
  .compile
```

