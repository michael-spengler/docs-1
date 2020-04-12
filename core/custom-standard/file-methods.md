---
description: The Unlink object helps you create your own custom unlink method.
---

# File Methods

## 📘 Usage

Initialize the process with `file.init`to retrieve file data.

```javascript
const fileData = await file.init(path)
await file.random(fileData)
await file.end(fileData)
```

{% hint style="danger" %}
Unless you know what you’re doing, always end with `file.end`.
{% endhint %}

## init \(fileName\)

* **fileName**: `string`

Mandatory to get file data.

## end \(fileData\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`

Mandatory to delete file.

## mark \(fileData\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`

Help to construct a tree of erased files.

Used in `mark` standard.

## random \(fileData \[, { passes } \]\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`
* **passes**: `number`
  * **default**: `1`
  * the number of times the function is executed.

Write cryptographically strong pseudo-random data.

## zeroes \(fileData \[, { passes } \]\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`
* **passes**: `number`
  * **default**: `1`
  * the number of times the function is executed.

Write zeroes on the whole file.

## ones \(fileData \[, { passes } \]\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`
* **passes**: `number`
  * **default**: `1`
  * the number of times the function is executed.

Write ones on the whole file.

## byte \(fileData \[, { passes, data } \]\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`
* **passes**: `number`
  * **default**: `1`
  * the number of times the function is executed.
* **data**: `number`
  * A byte: must be between `0x00` and `0xFF` \(Hexadecimal\)

Write one byte on the whole file.

```javascript
await file.byte(fileData, { data: 0x55 })
```

## byteArray \(fileData \[, { passes, data } \]\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`
* **passes**: `number`
  * **default**: `1`
  * the number of times the function is executed.
* **dataArray**: `number[]`
  * The array containing the bytes.

Write an array of bytes on the whole file.

```javascript
await file.byteArray(fileData, { data: [0x92, 0x49, 0x24] })
```

## forByte \(fileData \[, { passes, data } \]\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`
* **data**: `Object`
  * **initial**: `number`
    * initialize the counter variable.
  * **condition**: `(i: number) => boolean`
    * An expression to be evaluated before each loop iteration.
  * **increment**: `(i: number) => number`
    * The increment of the counter variable after each loop iteration.

A `for` loop, write the value of the variable at each iteration.

```javascript
await file.forByte(fileData, {
    initial: 0x00,
    condition: i => i < 0xFF,
    increment: i => i + 0x11
})
```

## randomByte \(fileData \[, { passes } \]\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`
* **passes**: `number`
  * **default**: `1`
  * the number of times the function is executed.

Write one cryptographically strong pseudo-random byte on the whole file.

## complementary \(fileData \[, { passes } \]\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`

Write the binary complement of the file.

## rename \(fileData\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`

Rename the file to a random string of length `12`.

## truncate \(fileData \[, { passes } \]\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`

Truncate to between 25% and 75% of the file size.

## resetTimestamps \(fileData\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`

Reset file timestamps to 1970-01-01T00:00:00.000Z.

## changeTimestamps \(fileData\[, { data } \]\)

* **fileData**: `{ fd: number, fileName: string, fileSize: number }`
* **data**: `Object`
  * **date1**: `Date`
    * **default**: `1970-01-01T00:00:00.000Z`.
    * Date will be greater than or equal date1.
  * **date2**: `Date`
    * **default**: `now`.
    * Date will be less than or equal date2.

Randomize file timestamps to a random value between date1 and date2. Setting the same value to date1 and date2 will take away the randomness.

