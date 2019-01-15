![Logo](https://raw.githubusercontent.com/stockulus/pouchdb-react-native/master/static/pouchdb-react-native.png)

[![npm Package](https://img.shields.io/npm/dm/pouchdb-react-native.svg)](https://www.npmjs.com/package/pouchdb-react-native) [![npm Package](https://img.shields.io/npm/v/pouchdb-react-native.svg)](https://www.npmjs.com/package/pouchdb-react-native) [![travis-ci.org](https://travis-ci.org/stockulus/pouchdb-react-native.svg)](https://travis-ci.org/stockulus/pouchdb-react-native) [![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](http://standardjs.com/) [![license](https://img.shields.io/npm/l/pouchdb-react-native.svg?maxAge=2592000)](https://opensource.org/licenses/MIT)

pouchdb-react-native
======

PouchDB, the ReactNative-only edition. A preset representing the PouchDB code that runs in ReactNative.

The `pouchdb-react-native` preset contains the version of PouchDB that is designed for ReactNative. In particular, it ships with the AsyncStorage adapters as its default adapters. It also contains the replication, HTTP, and map/reduce plugins.

### What is New
This fork contains the solution to pouchdb-react-native error: "can't find variable buffer", when you try to run it.
The modified library `pouchdb-binary-utils` was added to the packages.
You can as well download pouchdb-binary-utils from [![npm Package](https://travis-ci.org/stockulus/pouchdb-react-native.svg)
https://github.com/emexrevolarter/react-native/tree/master/pouchdb-binary-utils

Then, follow the steps listed in the readme.md. This commit solved this problem by simply replacing the old buffer plugin with the newer buffer plugin.

### Usage

```bash
npm install pouchdb-react-native --save
```
npm >= 3 / node >= 6 works best, there are some known issues with npm 2

### PouchDB 7.0

```bash
npm install pouchdb-react-native@next --save
```


```js
import PouchDB from 'pouchdb-react-native'
const db = new PouchDB('mydb')

// use PouchDB
db.get('4711')
  .then(doc => console.log(doc))

```
For full API documentation and guides on PouchDB, see [PouchDB.com](http://pouchdb.com/).

### Sample App
there is a small example app:
https://github.com/stockulus/pouchdb-react-native/tree/master/example

pouchdb-adapter-asyncstorage
======

PouchDB adapter using AsyncStorage as its data store. Designed to run in ReactNative. Its adapter name is `'asyncstorage'`.

### Usage

```bash
npm install pouchdb-adapter-asyncstorage --save
```

```js
import PouchDB from 'pouchdb-core'
PouchDB.plugin(require('pouchdb-adapter-asyncstorage').default)
const db = new PouchDB('mydb', {adapter: 'asyncstorage'})

// use PouchDB
db.get('4711')
  .then(doc => console.log(doc))

```

### Android limit

On Android asyncstorage has a limitation of 6 MB per default, you might want to increase it

```java
// MainApplication.getPackages()
long size = 50L * 1024L * 1024L; // 50 MB
com.facebook.react.modules.storage.ReactDatabaseSupplier.getInstance(getApplicationContext()).setMaximumSize(size);
```

### known issues

There are still Problems with Attachments, but currently there is work on it. See
(https://github.com/stockulus/pouchdb-react-native/issues/68)

development
======
```bash
git clone https://github.com/stockulus/pouchdb-react-native.git
cd pouchdb-react-native
git submodule init
git submodule update
npm install
npm test
cd example
npm run ios

```

---
[![Twitter URL](https://img.shields.io/twitter/url/http/shields.io.svg?style=social&maxAge=2592000)](https://twitter.com/stockulus) [![GitHub stars](https://img.shields.io/github/stars/stockulus/pouchdb-react-native.svg?style=social&label=Star)](https://github.com/stockulus/pouchdb-react-native)
