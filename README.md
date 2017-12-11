# bip38-smart

[![Version](http://img.shields.io/npm/v/bip38-smart.svg)](https://www.npmjs.org/package/bip38-smart)


A JavaScript component that adheres to the [BIP38](https://github.com/bitcoin/bips/blob/master/bip-0038.mediawiki) standard to secure your crypto currency private keys. Fully compliant with Node.js and the browser (via Browserify).


## Why?
BIP38 is a standard process to encrypt Bitcoin, SmartCash and crypto currency private keys that is imprevious to brute force attacks thus protecting the user.


## Package Info
- github: [https://github.com/SmartCash/bip38](https://github.com/SmartCash/bip38)
- issues: [https://github.com/SmartCash/bip38/issues](https://github.com/SmartCash/bip38/issues)
- bip38 bitcoin: [http://cryptocoinjs.com/modules/currency/bip38/](http://cryptocoinjs.com/modules/currency/bip38/)
- license: **MIT**


## Usage

### Installation

    npm install --save bip38-smart


### API
### encrypt(buffer, compressed, passphrase[, progressCallback, scryptParams])

``` javascript
var bip38 = require('bip38-smart')
var wif = require('wif-smart')

var myWifString = 'VNUeptnSW5iY8F8Drn46uKXkrSmet8a7wSTzvWRHhjjbWAaTY5AW'
var decoded = wif.decode(myWifString)

var encryptedKey = bip38.encrypt(decoded.privateKey, decoded.compressed, 'TestingOneTwoThree')
console.log(encryptedKey)
// => '6PYNiZZBhoCLVv67xCWXDzMVfqspgZxX3X6EXMpFpcmiqs4yH7Bw8nKuaT'aT'
```


### decrypt(encryptedKey, passhprase[, progressCallback, scryptParams])

``` javascript
var bip38 = require('bip38-smart')
var wif = require('wif-smart')

var encryptedKey = '6PYNiZZBhoCLVv67xCWXDzMVfqspgZxX3X6EXMpFpcmiqs4yH7Bw8nKuaT'
var decryptedKey = bip38.decrypt(encryptedKey, 'TestingOneTwoThree', function (status) {
  console.log(status.percent) // will print the precent every time current increases by 1000
})

console.log(wif.encode(0xBF, decryptedKey.privateKey, decryptedKey.compressed))
// => 'VNUeptnSW5iY8F8Drn46uKXkrSmet8a7wSTzvWRHhjjbWAaTY5AW'
```


# References
- https://github.com/bitcoin/bips/blob/master/bip-0038.mediawiki
- https://github.com/pointbiz/bitaddress.org/issues/56 (Safari 6.05 issue)
- https://github.com/casascius/Bitcoin-Address-Utility/tree/master/Model
- https://github.com/nomorecoin/python-bip38-testing/blob/master/bip38.py
- https://github.com/pointbiz/bitaddress.org/blob/master/src/ninja.key.js

