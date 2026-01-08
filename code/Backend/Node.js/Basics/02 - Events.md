Every action on a computer is an event. Like when a connection is made or a file is opened.

Objects in Node.js can fire events, like the `readStream` object fires events when opening and closing a file:
```javascript
var fs = require('fs');  
var rs = fs.createReadStream('./demofile.txt');  
rs.on('open', function () {  
  console.log('The file is open');  
});
```

You can assign event handlers to your own events with the EventEmitter object.

In the example below we have created a function that will be executed when a "scream" event is fired.

To fire an event, use the `emit()` method.
```javascript
var events = require('events');  
var eventEmitter = new events.EventEmitter();  
  
//Create an event handler:  
var myEventHandler = function () {  
  console.log('I hear a scream!');  
}  
  
//Assign the event handler to an event:  
eventEmitter.on('scream', myEventHandler);  
  
//Fire the 'scream' event:  
eventEmitter.emit('scream');
```
