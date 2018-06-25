# Node with Browserify

## Installation

```bash
call npm install -g browserify exorcist babel-cli
```

## Built-in to Browserify:

```text
events, stream, url, path, and querystring are particularly useful
    in a browser environment.

Additionally, if browserify detects the use of
    Buffer, process, global, __filename, or __dirname,
    it will include a browser-appropriate definition.

Also built-in:
assert
buffer
console
constants
crypto
domain
events
http
https
os
path
punycode
querystring
stream
string_decoder
timers
tty
url
util
vm
zlib
```

## Buffer

{% tabs %}
{% tab title="main.js" %}
```javascript
// Build with:
//     browserify main.js --debug | exorcist bundle.map.js >bundle.js 
var buf = Buffer('YmVlcCBib29w', 'base64');
var hex = buf.toString('hex');
console.log(hex);
```
{% endtab %}

{% tab title="index.html" %}
```markup
<!DOCTYPE html>
<html>
  <body>
    <script src="bundle.js"></script>
  </body>
</html>
```
{% endtab %}
{% endtabs %}

## Process

{% tabs %}
{% tab title="main.js" %}
```javascript
// Build with:
//     browserify main.js --debug | exorcist bundle.map.js >bundle.js

setTimeout(function () {
        console.log('third');
}, 0);

process.nextTick(function () {
        console.log('second');
});

console.log('first');
```
{% endtab %}

{% tab title="index.html" %}
```markup
<!DOCTYPE html>
<html>
  <body>
    <script src="bundle.js"></script>
  </body>
</html>
```
{% endtab %}
{% endtabs %}

