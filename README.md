bees (in Italian ```API``` means ```bees```)
====


Let the code write your docs D:

## Installation:

```
$ npm install bees
```

## Example: 

__app.js__
```javascript
var app = require('express').createServer();


/**
 * GET /
 * 
 * @return Main page
*/
app.get('/', function(req, res){
    res.send('Hello World');
});

/**
 * GET /:id
 * 
 * @param id id of the user
 * @return user infos
*/
app.get('/:id', function(req, res){
    res.send('Hello World');
});


app.listen(3000);
```

```
$ bees app.js
[
  {
    "method":"GET",
    "path":"/",
    "return":"Main page"
  },
  {
    "method":"GET",
    "path":"/:id",
    "params":{
      "id":"id of the user"
    },
    "return":"user infos"
  }
]

```

## To Do:

- Generate HTML from JSON

## Tests:

```
$ npm test
```

Tests are written with Vows

## License:

[WTFPL 2](http://sam.zoy.org/wtfpl/)
