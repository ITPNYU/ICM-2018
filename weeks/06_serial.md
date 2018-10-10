# Getting Started with Serial and p5.js

1.  Download the [P5 Serial Control](https://github.com/vanevery/p5.serialcontrol/releases) application.  This application serves as a bridge between your arduino and your p5 sketch.  For it to run you'll on a mac you either need to have "allow apps downloaded from anywhere" enabled or cntrl-click to open. [More info on apple's help pages](https://support.apple.com/kb/PH21769?locale=en_US).

2. Open the following example, connect your Arduino, and get it running.  (You can "duplicate" it in the p5 editor to save it into your account.)   (NOTE:  Right now using this with the p5.js Editor requires Chrome)
   * [p5.js code for reading analog value](http://alpha.editor.p5js.org/shawn/sketches/Sk3xpl26).  Works with AnalogReadSerial Arduino sketch, found in the Arduino IDE, File menu, Examples-> Basics —> AnalogReadSerial. Turn a potentiometer from 0 - 1023, the ball moves from 0-255 on the screen.

The examples use the p5.serialport library.  You can read [documentation](http://vanevery.github.io/p5.serialport/docs/classes/p5.serialport.html) and find [more examples](https://github.com/vanevery/p5.serialport/tree/master/examples).

You might notice the above examples use a new concept called a "callback."  This is a concept we will examine in detail next week in ICM while looking at "DOM manipulation."  A quick explanation for how this relates to serial communication is as follows:

There is an "event" each time your p5 sketch receives data from the serial port.  You get to decide what function is executed for that event.  In the case of the examples, that function is `serialEvent()`.

```javascript
// When there is data, run serialEvent  
serial.on('data', serialEvent);
```

The above line of code then requires you write a function called `serialEvent()` to handle the data.

```javascript
function serialEvent() {
  // Your code for reading the data goes here.
}
```

If you start a new sketch or are adapting a previous sketch made in the p5 editor, you'll need to upload [p5.serialport.js](https://raw.githubusercontent.com/vanevery/p5.serialport/master/lib/p5.serialport.js) to your sketch.

As well as add the following line to the `index.html` file.

```html
<script src="p5.serialport.js"></script>
```

The [Pcomp site](https://itp.nyu.edu/physcomp/itp/syllabus/) has much more in-depth serial information complete with a [video](https://vimeo.com/237203208) for a similar example!
