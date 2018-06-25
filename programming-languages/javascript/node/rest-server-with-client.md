# REST server with client

## Example:

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
// npm install express
// run Server with:
//     node server.js
// client example:
//     curl http://localhost:3000/v1/hello/mark
//     curl http://localhost:3000/v1/rep/books
//     curl http://localhost:3000/v1/rep/books/It

var express = require('express');
var app = express();

app.get('/v1/hello/:name', function(req, res){
  res.send('hello ' + req.params.name);
});

app.get('/v1/rep/books', function(req, res){
    o = [
        {title: "book1"},
        {title: "book2"},
        {title: "book3"}
    ]; 
    res.send(o);
});

app.get('/v1/rep/books/:id', function(req, res){
    o = {
        title: req.params.id,
        author: "bob"
    };
      res.send(o);
});

app.listen(3000);
console.log('Listening on port 3000');
```
{% endcode-tabs-item %}
{% endcode-tabs %}





