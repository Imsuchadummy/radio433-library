# Send and receive a message example #

To start we need:

2- Arduino Uno boards (or compatibles);

1- 433Mhz or 315Mhz ASK transmitter;

1- same frequency ASK receiver;

At this example we use arduino pin 11 to transmitter:

<img src='http://1.bp.blogspot.com/-Eap9Kf4TE1A/VMK4tr_1exI/AAAAAAAAAGk/2ATfNYhan2A/s800/ttx+protoboard.png'>

This is the code for transmitter:<br>
<br>
<pre><code><br>
//Simple example of how to use Radio433 to transmit a message<br>
//with a simple ASK transmitter in a very simple way.<br>
<br>
#include &lt;Radio433.h&gt;<br>
<br>
void setup()<br>
{<br>
  radioDeclare(11,10,3,2000);//define TX pin, RX pin, TX enable pin, and transmission rate in bps<br>
  Serial.begin(9600);//start Serial<br>
}<br>
<br>
void loop()<br>
{<br>
  TXprintln();//to print the message on serial, must be called before each message<br>
  radioSend("Hello World!");//send String <br>
  delay(1000);<br>
}<br>
<br>
<br>
<br>
</code></pre>


For receiver, pin 10 is used:<br>
<br>
<img src='http://2.bp.blogspot.com/-8TXNoeym1EY/VMK4tQJmMWI/AAAAAAAAAGg/kq-dZSSkR28/s800/rx+protoboard.png'>

<pre><code><br>
//Simple example of how to use Radio433 to receive a message<br>
//with a simple ASK transmitter in a very simple way.<br>
<br>
#include &lt;Radio433.h&gt;<br>
<br>
void setup()<br>
{<br>
  radioDeclare(11,10,3,2000);//define TX pin, RX pin, TX enable pin, and transmission rate in bps<br>
  radioRXbegin();<br>
  Serial.begin(9600);//start Serial<br>
}<br>
<br>
void loop()<br>
{<br>
  radioRXloop();//must be first in the void loop <br>
  RXprintln();//to print the last received message on serial<br>
  <br>
}<br>
<br>
</code></pre>