# pebble-timeline-js

Simple JS package to allow inserting of personal (user) and shared (topic)
timeline pins from PebbleKit JS directly or a Node.js server.

## Installation

`pebble package install pebble-timeline-js`


## Methods

`insertUserPin(pin, callback)` - insert a timeline pin for the user running the app.

`deleteUserPin(pin, callback)` - delete a pin previously pushed. The `id` must match.


## Example Usage

In `src/pkjs/index.js`:

```js
var timelinejs = require('pebble-timeline-js');

var pin = {
  id: 'example-pin-generic-d2sd3d5bdsd',
  time: new Date().toISOString(),
  layout: {
    type: 'genericPin',
    title: 'timelinejs pin test',
    tinyIcon: 'system://images/NOTIFICATION_FLAG'
  }
};


Pebble.addEventListener('ready', function() {
  console.log('Ready! Inserting user pin ' + JSON.stringify(pin));

  timelinejs.insertUserPin(pin, function(responseText) {
    console.log('Result: ' + responseText);
  });
});

```


## TODO

Add methods for wrapping the 
[AppGlance REST API](https://developer.pebble.com/guides/user-interfaces/appglance-rest).
