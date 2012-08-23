[![build status](https://secure.travis-ci.org/yawnt/bees.png)](http://travis-ci.org/yawnt/bees)
bees (in Italian ```API``` means ```bees```)
====


Let the code write your docs D:

## Installation:

```
$ npm install bees
```

## Example: 

See ```test/file```

## Plugin:

You can extend Bees and add new keywords with a tiny plugin system (see ```lib/plugins```)

```javascript
var bees = require('bees');
bees.use('plugin', function(cmd, json) {
  json.plugin = cmd[1];
});
console.log(
  bees.parse(
    require('fs').readFileSync('./app.js','utf-8')
  )
);
```

Now you can use it

```javascript
/**
 * GET /:id
 * 
 * @param id id of the user
 * @return user infos
 * @plugin hai lol
*/
```

```
$ node plugin.js
[
  {
    method: 'GET',
    path: '/:id',
    params: { id: 'id of the user' },
    return: 'user infos',
    plugin: 'hai lol'
  }
]
```

## Reporters:

Reporters are a way to return formatted objects.

If we got this in eyes-reporter.js:

```javascript
var inspector = require('eyes').inspector({stream: null});

module.exports = function(doc) {
  return inspector(doc);
};
```

And we call bees just like this:

```
bees -R eyes-reporter <file>
```

We will get:

![eyes](http://i.imgur.com/F9p5M.png)

Cool eh?

## To Do:

- Generate HTML from JSON

## Tests:

```
$ npm test
```

Tests are written with Vows

## License:

__MIT__
