# fs-chain

A file I/O tool chain.

[![npm][npm-badge]][npm-url]
[![github][github-badge]][github-url]
![node][node-badge]

[npm-url]: https://www.npmjs.com/package/fs-chain
[npm-badge]: https://img.shields.io/npm/v/fs-chain.svg?style=flat-square&logo=npm
[github-url]: https://github.com/airkro/fs-chain
[github-badge]: https://img.shields.io/npm/l/fs-chain.svg?style=flat-square&colorB=blue&logo=github
[node-badge]: https://img.shields.io/node/v/fs-chain.svg?style=flat-square&colorB=green&logo=node.js

## Installation

```bash
npm install fs-chain --save-dev
```

## Usage

```js
const { Text, Json } = require('fs-chain');

new Text() // create file
  .handle(() => 'text:sample')
  .output('./path/filename');

new Json() // copy file
  .source('./path/old-filename')
  .output('./path/new-filename');

new Text() // edit file
  .source('./path/filename')
  .handle((data) => data.trim())
  .output();

new Json() // transfer file
  .source('./path/old-filename')
  .handle((data) => data.value)
  .output('./path/new-filename');

new Json().source('qss'); // require.resolve

new Text()
  .handle(() => {
    // skip following step
    throw new Error('skip');
  })
  .handle(() => {
    // other step
  });

new Text().exists('./path/old-filename').handle(() => {
  // won't call when not exists
});
```
