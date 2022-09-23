![GitHub package.json version](https://img.shields.io/github/package-json/v/avodevelopment/react-native-jssip?label=react-native-jssip)
[![Code Quality: Javascript](https://img.shields.io/github/package-json/v/versatica/JsSip?label=JsSIPVersion)](https://lgtm.com/projects/g/versatica/JsSIP/context:javascript)
[![Dependencies](https://img.shields.io/badge/dependencies-react--native--webrtc-green)](https://www.npmjs.com/package/react-native-webrtc)
![License](https://img.shields.io/apm/l/vim-mode)

## Overview

* Runs on android and ios
* SIP over [WebSocket](https://jssip.net/documentation/misc/sip_websocket/) (use real SIP in your web apps)
* Audio/video calls ([WebRTC](https://jssip.net/documentation/misc/webrtc)) and instant messaging
* Lightweight!
* Easy to use and powerful user API
* Works with OverSIP, Kamailio, Asterisk. Mobicents and repro (reSIProcate) servers ([more info](https://jssip.net/documentation/misc/interoperability))
* Written by the authors of [RFC 7118 "The WebSocket Protocol as a Transport for SIP"](https://tools.ietf.org/html/rfc7118) and [OverSIP](http://oversip.net)


## NOTE

RFC 2833 is not implemented in react-native-webrtc, DTMF working only with INFO package

## Getting Started

The following simple JavaScript code creates a JsSIP User Agent instance and makes a SIP call:

```javascript
// Create our JsSIP instance and run it:

var socket = new JsSIP.WebSocketInterface('wss://sip.myhost.com');
var configuration = {
  sockets  : [ socket ],
  uri      : 'sip:alice@example.com',
  password : 'superpassword'
};

var ua = new JsSIP.UA(configuration);

ua.start();

// Register callbacks to desired call events
var eventHandlers = {
  'progress': function(e) {
    console.log('call is in progress');
  },
  'failed': function(e) {
    console.log('call failed with cause: '+ e.data.cause);
  },
  'ended': function(e) {
    console.log('call ended with cause: '+ e.data.cause);
  },
  'confirmed': function(e) {
    console.log('call confirmed');
  }
};

var options = {
  'eventHandlers'    : eventHandlers,
  'mediaConstraints' : { 'audio': true, 'video': true }
};

var session = ua.call('sip:bob@example.com', options);
```

Want to see more? Check the full documentation at https://jssip.net/documentation/.


## Website and Documentation

* [jssip.net](https://jssip.net/)


## Usage

* Since is not published with npm, use refering this repo in your package.json
```
 "jssip": "git://github.com/avodevelopment/RNJsSIP.git#commit-ish"
```


## Authors

#### React Native Fork

* React Native patch publisher
* Augusto Zanoni <augusto@nta.co.uk> (Github [@augustozanoni](https://github.com/augustozanoni))
* Pier Guinzani <pierguinzani@gmail.com> (Github [@pierguinzani](https://github.com/pierguinzani))

#### José Luis Millán

* Main author. Core Designer and Developer.
* <jmillan@aliax.net> (Github [@jmillan](https://github.com/jmillan))

#### Iñaki Baz Castillo

* Core Designer and Developer.
* <ibc@aliax.net> (Github [@ibc](https://github.com/ibc))

#### Saúl Ibarra Corretgé

* Core Designer.
* <saghul@gmail.com> (Github [@saghul](https://github.com/saghul))


## License

JsSIP is released under the [MIT license](https://jssip.net/license).
