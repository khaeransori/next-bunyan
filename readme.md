# Next.js + Bunyan

Use [node-bunyan](https://github.com/trentm/node-bunyan) on server side and [browser-bunyan](https://github.com/philmander/browser-bunyan) on client side in Next.js project 

## Installation

```bash
npm install --save bunyan browser-bunyan next-bunyan
```

or 

```bash
yarn add bunyan browser-bunyan next-bunyan
```

## Usage

Create a `next.config.js` in your project

```js
// next.config.js
const withBunyan = require("next-bunyan");
module.exports = withBunyan();
```

Create a logger file `utils/logger/JsonLogger.js`

```js
import bunyan from "bunyan";

export default bunyan.createLogger({
  name: "foo"
  // other bunyan config
});
```

Then you could use it on another file, for example

```js
import JsonLogger from "utils/logger/JsonLogger.js";

JsonLogger.info("foo bar");
```

### Configuring Next.js

Optionally you can add your custom Next.js configuration as parameter

```js
// next.config.js
const withBunyan = require("next-bunyan");
module.exports = withBunyan({
  webpack(config, options) {
    return config;
  }
});
```