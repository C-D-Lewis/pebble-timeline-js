# pebble-timeline-js

Simple JS package to allow inserting of personal (user) and shared (topic)
timeline pins from PebbleKit JS directly or a Node.js server.

## Installation

`pebble package install pebble-timeline-js`

If you're using this in a Node.js server (such as one that pushes timeline pins
to users) make sure to install a shim module (such as 
[this one](https://www.npmjs.com/package/xmlhttprequest)) to make 
`XMLHttpRequest` available.


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
