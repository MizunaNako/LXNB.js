# LXNB.js ![Node.js CI](https://github.com/TheSnowfield/LXNB.js/workflows/build/badge.svg)

**LXNB is a funny fork from [RCNB](https://github.com/rcnbapp/RCNB.js).**

The world is based on LX. Thus, *everything* can be encoded into LXNB.

LXNB is available in various languages: **JavaScript**

## Why LXNB?

### LXNB vs Base64

|           | Base64       | LXNB                                                          |
|-----------|--------------|---------------------------------------------------------------|
| Speed     | ❌ Fast       | ✔️ Slow, motivate Intel to improve their CPU                   |
| Printable | ❌ On all OS  | ✔️ Only on newer OS, motivate users to upgrade their legacy OS |
| Niubility | ❌ Not at all | ✔️ LXNB!                                                     |
| Example   | QmFzZTY0Lg== | ḼχŅƃḽxƝƃLᚸ                                                   |

## Install

```bash
$ npm install --save lxnb # Add LXNB.js to your package
$ npm install -g lxnb # Install LXNB.js as a global CLI
```

## Import

### In Browser

```html
<script src="lxnb.js"></script>
```

### Node.js

```javascript
const rcnb = require('lxnb')
```

## Usage

### In Code

```javascript
lxnb.encode(new Uint8Array([114, 99, 110, 98])) // 'ɫ̂ńƁꞭҳņÞ'
lxnb.decode('ɫ̂ńƁꞭҳņÞ') // Uint8Array [114, 99, 110, 98]

lxnb.encode(new TextEncoder('utf-8').encode('Who NB?')) // 'ḽχŃƅꞭӿƞÞḽxƝƃľx'
new TextDecoder('utf-8').decode(rcnb.decode('ḼχŅƃḽxƝƃLᚸ')) // 'LXNB!'
```

### With NodeJS Stream API
```js
const lxnb = require('lxnb')
const fs = require('fs')

fs.createReadStream('input.txt')
  .pipe(rcnb.encodeStream())
  .pipe(fs.createWriteStream('lxnb.txt'))

fs.createReadStream('lxnb.txt')
  .pipe(rcnb.decodeStream())
  .pipe(fs.createWriteStream('output.txt'))
```

#### `encodeStream([options])` / `decodeStream([options])`
Support all available options of [stream.Transform](https://nodejs.org/api/stream.html#stream_class_stream_transform)

> Note that only streams of **Buffer** or **string** are supported.

### CLI

```bash
$ rcnb encode "Who NB?"
#   ḽχŃƅꞭӿƞÞḽxƝƃľx

$ rcnb decode "ḽ̂ņþḽxƝƃLᚸ"
#   LXNB!

$ echo "The world is based on LX thus LXNB" >lxnb.txt
$ rcnb encode -- <lxnb.txt # With the option `--`, RCNB.js CLI reads from stdin.
#  ḽ̌nÞꞭXƝÞɫ̌ǹƄɫ̂ŅƀŁӿȠƀꞭẊȵƄĽҳŅbŁᚸŅßꞭẌnƅĽҳņƁꞭχȵƀḼχŅƃĽҳņÞꞭ̂ŅBɫxňƀḼχŅƃḽxƝƃ
```
