---
description: >-
  Secure-rm has a comprehensive list of standards to irreversibly delete your
  files. Find the one that meets your needs.
---

# Standards

## 📘Usage

```javascript
const options = {
  standard: 'gutmann'
}

srm('./data/*.js', options, (err) => {
  if (err) throw err
  console.log('Files successfully deleted !')
})
```

## Preview

Returns targeted files without deleting them.

| ID | Passes |
| :--- | ---: |
| `preview` | `1` |

```javascript
{
  unlinkStandard: new Unlink()
    .log()
    .compile,
  rmdirStandard: new RmDir()
    .log()
    .compile
}
```

### Pseudorandom data

Also kwown as "Australian Information Security Manual Standard ISM 6.2.92" and "New Zealand Information and Communications Technology Standard NZSIT 402". Your data is overwritten with cryptographically strong pseudo-random data. \(The data is indistinguishable from random noise.\)

| ID | Passes |
| :--- | ---: |
| `randomData` | `1` |

```javascript
{
  unlinkStandard: new Unlink()
    .random()
    .unlink()
}
```

### Pseudorandom byte

Overwriting with a random byte.

| ID | Passes |
| :--- | ---: |
| `randomByte` | `1` |

```javascript
{
  unlinkStandard: new Unlink()
    .randomByte()
    .unlink()
}
```

### Zeroes

Overwriting with zeroes.

| ID | Passes |
| :--- | ---: |
| `zeroes` | `1` |

```javascript
{
  unlinkStandard: new Unlink()
    .zeroes()
    .unlink()
}
```

### Ones

Overwriting with ones.

| ID | Passes |
| :--- | ---: |
| `ones` | `1` |

```javascript
{
  unlinkStandard: new Unlink()
    .ones()
    .unlink()
}
```

### **Secure-rm standard**

Pass 1: Overwriting with random data;

Pass 2: Renaming the file with random data;

Pass 3: Truncating between 25% and 75% of the file.

| ID | Passes |
| :--- | ---: |
| `secure` | `3` |

```javascript
{
  unlinkStandard: new Unlink()
    .random()
    .rename()
    .truncate()
    .unlink()
}
```

### Russian State Standard GOST R50739-95

Pass 1: Overwriting with zeroes;

Pass 2: Overwriting with random data.

| ID | Passes |
| :--- | ---: |
| `GOST_R50739-95` | `2` |

```javascript
{
  unlinkStandard: new Unlink()
    .zeroes()
    .random()
    .unlink()
}
```

### British HMG Infosec Standard 5

Also known as "Air Force System Security Instructions AFSSI-5020", "Standard of the American Department of Defense \(DoD 5220.22 M\)" "National Computer Security Center NCSC-TG-025 Standard" and "Navy Staff Office Publication NAVSO P-5239-26"

Pass 1: Overwriting with zeroes;

Pass 2: Overwriting with ones;

Pass 3: Overwriting with random data as well as verifying the writing of this data.

| ID | Passes |
| :--- | ---: |
| `HMG_IS5` | `3` |

```javascript
{
  unlinkStandard: new Unlink()
    .zeroes()
    .ones()
    .random()
    .unlink()
}
```

### US Army AR380-19

Pass 1: Overwriting with random data;

Pass 2: Overwriting with a random byte;

Pass 3: Overwriting with the complement of the 2nd pass, and verifying the writing.

| ID | Passes |
| :--- | ---: |
| `AR380-19` | `3` |

```javascript
{
  unlinkStandard: new Unlink()
    .random()
    .randomByte()
    .complementary()
    .unlink()
}
```

### Standard of the Federal Office for Information Security \(BSI-VSITR\)

Also known as "Royal Canadian Mounted Police TSSIT OPS-II"

Pass 1: Overwriting with zeroes;

Pass 2: Overwriting with ones;

Pass 3-6: Same as 1-2;

Pass 7: Overwriting with a random data as well as review the writing of this character.

| ID | Passes |
| :--- | ---: |
| `VSITR` | `7` |

```javascript
{
  unlinkStandard: new Unlink()
    .zeroes()
    .ones()
    .zeroes()
    .ones()
    .zeroes()
    .ones()
    .random()
    .unlink()
}
```

### Bruce Schneier Algorithm

Pass 1: Overwriting with zeros;

Pass 2: Overwriting with ones;

Pass 3-7: Overwriting with random data.

| ID | Passes |
| :--- | ---: |
| `randomByte` | `7` |

```javascript
{
  unlinkStandard: new Unlink()
    .zeroes()
    .ones()
    .random(5)
    .unlink()
}
```

### Pfitzner Method

Pass 1-33: Overwriting with random data.

| ID | Passes |
| :--- | ---: |
| `pfitzner` | `33` |

```javascript
{
  unlinkStandard: new Unlink()
    .random(33)
    .unlink()
}
```

### Peter Gutmann Algorithm

Pass 1-4: Overwriting with random data;

Pass 5: Overwriting with 0x55;

Pass 6: Overwriting with 0xAA;

Pass 7-9: Overwriting with 0x92 0x49 0x24, then cycling through the bytes;

Pass 10-25: Overwriting with 0x00, incremented by 1 at each pass, until 0xFF;

Pass 26-28: Same as 7-9;

Pass 29-31: Overwriting with 0x6D 0xB6 0xDB, then cycling through the bytes;

Pass 32-35: Overwriting with random data.

| ID | Passes |
| :--- | ---: |
| `gutmann` | `35` |

```javascript
{
  unlinkStandard: new Unlink()
    .random(4)
    .byte(0x55)
    .byte(0xAA)
    .byteArray([0x92, 0x49, 0x24])
    .byteArray([0x49, 0x24, 0x92])
    .byteArray([0x24, 0x92, 0x49])
    .forByte({ init: 0x00, condition: i => i < 0xFF, increment: i => i + 0x11 })
    .byteArray([0x92, 0x49, 0x24])
    .byteArray([0x49, 0x24, 0x92])
    .byteArray([0x24, 0x92, 0x49])
    .byteArray([0x6D, 0xB6, 0xDB])
    .byteArray([0xB6, 0xDB, 0x6D])
    .byteArray([0xDB, 0x6D, 0xB6])
    .random(4)
    .unlink()
}
```

