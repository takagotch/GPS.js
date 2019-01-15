### Gps.js
---
https://github.com/infusion/GPS.js/

```js
var gps = new GPS;
gps.on('data', function(parsed){
  console.log(parsed);
});
gps.update("$GPGGA,xxxxx, xxxxxxxx,xxx");

gps.on('data', function(){
  console.log(gps.state);
});

var obs = require('octalbonescript');
obs.serial.enable('/dev/ttyS1', function(){
  console.log('serial device activated');
});

var SerialPort = require('serialport');
var port = new SerialPort.SerialPort('/dev/tty.usbserial', {
  baudrate: 4800,
  parser: SerialPort.parsers.readline('\r\n')
});
var GPS = require('gps');
var gps = new GPS;
gps.on('data', function(data){
  console.log(data, gps.state);
});
port.on('data', function(data){
  gps.updatePartial(data);
});

var angles = require('angles');
console.log(angles.compass(GPS.Heading(50, 10, 51, 9)));
```

```
npm install gps

node server
node confluence
node set-date
node test
```

```
<script src="gps.js"></script>
<script>
  var gps = new GPS;
  gps.update('...');
</script>
```


