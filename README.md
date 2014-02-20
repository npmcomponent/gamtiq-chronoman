*This repository is a mirror of the [component](http://component.io) module [gamtiq/chronoman](http://github.com/gamtiq/chronoman). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/gamtiq-chronoman`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
# chronoman

Utility class to simplify use of timers created by setTimeout.

[![NPM version](https://badge.fury.io/js/chronoman.png)](http://badge.fury.io/js/chronoman)

## Installation

### Node

    npm install chronoman

### [Component](https://github.com/component/component)

    component install gamtiq/chronoman

### [Jam](http://jamjs.org)

    jam install chronoman

### [Bower](http://bower.io)

    bower install chronoman

### AMD, &lt;script&gt;

Use `dist/chronoman.js` or `dist/chronoman.min.js` (minified version).

## Usage

### Node, Component

```js
var Timer = require("chronoman");
```

### Jam

```js
require(["chronoman"], function(Timer) {
    ...
});
```

### AMD

```js
define(["path/to/dist/chronoman.js"], function(Timer) {
    ...
});
```

### Bower, &lt;script&gt;

```html
<!-- Use bower_components/chronoman/dist/chronoman.js if the library was installed by Bower -->
<script type="text/javascript" src="path/to/dist/chronoman.js"></script>
<script type="text/javascript">
    // сhronoman is available via Chronoman field of window object
    var Timer = Chronoman;
    ...
</script>
```

### Example

```js
var nI = 0;

var tmrOne = new Timer({
    period: 1000,
    action: function(timer) {
        console.log("---> Timer one. ", timer);   // timer is undefined because passToAction is false by default
    }
});

var tmrTwo = new Timer();
tmrTwo.setPeriod(2000)
    .setRecurrent(true)
    .setPassToAction(true)
    .setAction(function(timer) {
        nI++;
        console.log("Timer two. #", nI, timer);
        tmrOne.setActive(! tmrOne.isActive());
        if (nI === 10) {
            timer.stop();
        }
    });

tmrTwo.start();
```

## API

See `doc` folder.

## Inspiration

This module is inspired by [qooxdoo](http://qooxdoo.org)'s `qx.event.Timer` class.

## Licence

MIT
