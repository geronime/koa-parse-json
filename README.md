# koa-parse-json

Parse json request body, generator style.

It seems that similar modules don't provide sane stack traces,
or simply ignore errors. Because this one is completly generator-based,
it provides proper stacktraces on parse error.

## Install

```
$ npm install koa-parse-json
```

## Usage

```js
var koa = require('koa');
var body = require('koa-parse-json');

var app = koa();

app.use(body());

app.use(function* () {
  this.body = this.request.body;
});
```

## API

### body(opts)

Returns a koa middleware, that can parse JSON request body.
It stops reading after `opts.limit` bytes, and throws 413,
if `Content-Length` doesn't match with request length, 400 is throwed.

Default `opts.limit` is 1MB.

On empty body set parsed body to empty object.

## License

MIT
