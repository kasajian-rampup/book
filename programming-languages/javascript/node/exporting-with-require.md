# Exporting with Require

## Using require:

{% code-tabs %}
{% code-tabs-item title="nums.js" %}
```javascript
// Run with:
//    node nums.js 
var uniq = require('uniq');
var nums = [ 5, 2, 1, 3, 2, 5, 4, 2, 0, 1 ];
console.log(uniq(nums));
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Export function:

{% tabs %}
{% tab title="main.js" %}
```javascript
// Run with:
//     node main.js 
var foo = require('./foo.js');
console.log(foo(5));
```
{% endtab %}

{% tab title="foo.js" %}
```javascript
module.exports = function(n) {
    return n * 111;
};
```
{% endtab %}
{% endtabs %}

## Export value:

{% tabs %}
{% tab title="main.js" %}
```javascript
// Run with:
//     node main.js
var foo = require('./foo.js');
console.log(foo);
```
{% endtab %}

{% tab title="foo.js" %}
```javascript
module.exports = 555;
```
{% endtab %}
{% endtabs %}

## Export multiple items

{% tabs %}
{% tab title="main.js" %}
```javascript
// Run with
//     node main.js 
var foo = require('./foo.js');
console.log(foo.beep(3));
console.log(foo.boop);
```
{% endtab %}

{% tab title="foo.js" %}
```javascript
exports.beep = function(n) { return n * 1000; };
exports.boop = 555;
```
{% endtab %}
{% endtabs %}

