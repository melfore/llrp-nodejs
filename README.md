llrp-nodejs
==========

Nodejs module to read RFID tags by connecting to a RFID reader through LLRP protocol.

## Status

Do not use for any serious development. This module is only able to read tag ids and doesn't implement the entire LLRP protocol.

### Authors

Billie Dee R. Ang

Jeriel Mari E. Lopez

### Installation

npm install llrp

### Config

You can provide a config object with the following values:

ipaddress - IP of the RFID reader (default 192.168.0.30) 

port - port of the RFID reader (default 5084)

log - log messages in the console (default false)

isReaderConfigSet - is the reader config set (default false)

isStartROSpecSent - has START_ROSPEC message been sent to the reader (default false)

### Example

```

var llrp = require('llrp');

var reader = new llrp({
	ipaddress: '192.168.0.143'
});

reader.connect();

reader.on('timeout', function () {
	console.log('timeout');
});

reader.on('disconnect', function () {
	console.log('disconnect');
});

reader.on('error', function (error) {
	console.log('error: ' + JSON.stringify(error));
});

reader.on('didSeeTag', function (tag) {
	console.log('TAG: ' + tag.tagID);
});

```
