is-ipfs
====

[![](https://img.shields.io/github/release/ipfs/is-ipfs.svg)](https://github.com/ipfs/is-ipfs/releases/latest)
[![](https://img.shields.io/badge/freenode-%23ipfs-blue.svg?style=flat-square)](https://webchat.freenode.net/?channels=%23ipfs)

> A set of utilities to help identify [IPFS](https://ipfs.io/) resources

## Lead Maintainer

[Marcin Rataj](https://github.com/lidel)

## Install

### In Node.js through npm

```bash
$ npm install --save is-ipfs
```

### Browser: Browserify, Webpack, other bundlers

The code published to npm that gets loaded on require is in fact an ES5 transpiled version with the right shims added. This means that you can require it and use with your favorite bundler without having to adjust asset management process.

```js
var is-ipfs = require('is-ipfs')
```


### In the Browser through `<script>` tag

Loading this module through a script tag will make the ```IsIpfs``` obj available in the global namespace.

```
<script src="https://unpkg.com/is-ipfs/dist/index.min.js"></script>
<!-- OR -->
<script src="https://unpkg.com/is-ipfs/dist/index.js"></script>
```

## Usage
```javascript
const isIPFS = require('is-ipfs')

isIPFS.multihash('QmYjtig7VJQ6XsnUjqqJvj7QaMcCAwtrgNdahSiFofrE7o') // true
isIPFS.multihash('noop') // false

isIPFS.cid('QmYjtig7VJQ6XsnUjqqJvj7QaMcCAwtrgNdahSiFofrE7o') // true (CIDv0)
isIPFS.cid('zdj7WWeQ43G6JJvLWQWZpyHuAMq6uYWRjkBXFad11vE2LHhQ7') // true (CIDv1)
isIPFS.cid('noop') // false

isIPFS.url('https://ipfs.io/ipfs/QmYjtig7VJQ6XsnUjqqJvj7QaMcCAwtrgNdahSiFofrE7o') // true
isIPFS.url('https://ipfs.io/ipns/github.com') // true
isIPFS.url('https://github.com/ipfs/js-ipfs/blob/master/README.md') // false
isIPFS.url('https://google.com') // false

isIPFS.path('/ipfs/QmYjtig7VJQ6XsnUjqqJvj7QaMcCAwtrgNdahSiFofrE7o') // true
isIPFS.path('/ipns/github.com') // true
isIPFS.path('/ipfs/js-ipfs/blob/master/README.md') // false

isIPFS.urlOrPath('https://ipfs.io/ipfs/QmYjtig7VJQ6XsnUjqqJvj7QaMcCAwtrgNdahSiFofrE7o') // true
isIPFS.urlOrPath('https://ipfs.io/ipns/github.com') // true
isIPFS.urlOrPath('/ipfs/QmYjtig7VJQ6XsnUjqqJvj7QaMcCAwtrgNdahSiFofrE7o') // true
isIPFS.urlOrPath('/ipns/github.com') // true
isIPFS.urlOrPath('https://google.com') // false

isIPFS.ipfsUrl('https://ipfs.io/ipfs/QmYjtig7VJQ6XsnUjqqJvj7QaMcCAwtrgNdahSiFofrE7o') // true
isIPFS.ipfsUrl('https://ipfs.io/ipfs/invalid-hash') // false

isIPFS.ipnsUrl('https://ipfs.io/ipfs/QmYjtig7VJQ6XsnUjqqJvj7QaMcCAwtrgNdahSiFofrE7o') // false
isIPFS.ipnsUrl('https://ipfs.io/ipns/github.com') // true

isIPFS.ipfsPath('/ipfs/QmYjtig7VJQ6XsnUjqqJvj7QaMcCAwtrgNdahSiFofrE7o') // true
isIPFS.ipfsPath('/ipfs/invalid-hash') // false

isIPFS.ipnsPath('/ipfs/QmYjtig7VJQ6XsnUjqqJvj7QaMcCAwtrgNdahSiFofrE7o') // false
isIPFS.ipnsPath('/ipns/github.com') // true
```

## API

### `isIPFS.multihash(hash)`

Returns `true` if the provided string is a valid `multihash` or `false` otherwise.

### `isIPFS.cid(hash)`

Returns `true` if the provided string is a valid `CID` or `false` otherwise.

### `isIPFS.url(url)`

Returns `true` if the provided string is a valid IPFS or IPNS url or `false` otherwise.

### `isIPFS.path(path)`

Returns `true` if the provided string is a valid IPFS or IPNS path or `false` otherwise.

### `isIPFS.urlOrPath(path)`

Returns `true` if the provided string is a valid IPFS or IPNS url or path or `false` otherwise.

### `isIPFS.ipfsUrl(url)`

Returns `true` if the provided string is a valid IPFS url or `false` otherwise.

### `isIPFS.ipnsUrl(url)`

Returns `true` if the provided string is a valid IPNS url or `false` otherwise.

### `isIPFS.ipfsPath(path)`

Returns `true` if the provided string is a valid IPFS path or `false` otherwise.

### `isIPFS.ipnsPath(path)`

Returns `true` if the provided string is a valid IPNS path or `false` otherwise.


**Note:** the regex used for these checks is also exported as `isIPFS.urlPattern`

## License


MIT
