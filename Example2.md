# Send and receive addressable messages #

Those two sketches shows how transmit a addressable message on the format:
`[FROM] [TO] [DATAKIND] [CONTENT]`

The message starts with the follows header:`[FROM] [TO] [DATAKIND]`

FROM - says to receiver who sent the message.

TO - says who receiver is able to get the message.

DATAKIND - is a identifier to receiver knows  what  to do with the message.

CONTENT - is the useful content of message, and can be a String, int, float, long, or byte type.

To send a adressable message we use the radioSend`(String from,String to,String datakind,`**any available type**` value)`,available type are: String,int,float,long,and byte.

And to receive a adressable type we use `radioRcv(String from,String to,String datakind,`**any available type**` *value)`. Note `*` at value field, here we assign value to our variable by reference, so you need write & before write the variable name.
This method assigns the received value directly to the variable.

To make this example we need:

2- Arduino Uno boards (or compatibles);

1- 433Mhz or 315Mhz ASK transmitter;

1- same frequency ASK receiver;

At this example we use arduino pin 11 to transmitter:

<img src='http://1.bp.blogspot.com/-Eap9Kf4TE1A/VMK4tr_1exI/AAAAAAAAAGk/2ATfNYhan2A/s800/ttx+protoboard.png'>

This is the code for transmitter:<br>
<br>
<pre><code>//Example of how to use Radio433 to transmit a message (like a sensor value) from radio1 to radio2;<br>
<br>
<br>
#include &lt;Radio433.h&gt;<br>
String address="radio1";<br>
//variables simulating sensors values<br>
int humidity=15;<br>
float temperature=35;<br>
long pressure=1010;<br>
String windDirection="NE";<br>
byte windIntensity=127;<br>
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
  radioSend(address,"humidity",humidity);<br>
  TXprintln();<br>
  radioSend("radio1","radio2","temperature",temperature);<br>
  TXprintln();<br>
  radioSend(address,"radio2","pressure",pressure);<br>
  TXprintln();<br>
  delay(200);<br>
  radioSend(address,"radio2","windDirection",windDirection);<br>
  <br>
  TXprintln();<br>
  radioSend("radio1","radio2","windIntensity",windIntensity);<br>
  <br>
  delay(1000);<br>
}<br>
</code></pre>


For receiver, pin 10 is used:<br>
<br>
<img src='http://2.bp.blogspot.com/-8TXNoeym1EY/VMK4tQJmMWI/AAAAAAAAAGg/kq-dZSSkR28/s800/rx+protoboard.png'>

<pre><code>//Simple example of how to use Radio433 to receive a message<br>
//with a simple ASK transmitter in a very simple way.<br>
<br>
#include &lt;Radio433.h&gt;<br>
String address="radio2";<br>
//variables to receive simulated sensors values data<br>
int receivedHumidity;<br>
float receivedTemperature;<br>
long receivedPressure;<br>
String receivedWindDirection;<br>
byte receivedwindIntensity;<br>
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
<br>
  radioRcv("radio1","humidity",&amp;receivedHumidity);// radioRcv(from,data indentifier,to assign variable)<br>
  radioRcv("radio1",address,"temperature",&amp;receivedTemperature);//radioRcv(from,to,data_indentifier,to_assign_variable)<br>
  radioRcv("radio1",address,"pressure",&amp;receivedPressure);//don't forget &amp; reference operator<br>
  radioRcv("radio1",address,"windDirection",&amp;receivedWindDirection);<br>
  radioRcv("radio1","radio2","windIntensity",&amp;receivedwindIntensity);<br>
<br>
if(RXget("radio1","humidity")==true)<br>
{<br>
 Serial.print("receivedHumidity = ");<br>
 Serial.println(receivedHumidity);<br>
}<br>
<br>
if(RXget("radio1",address,"temperature")==true)<br>
{<br>
  Serial.print("receivedTemperature = ");<br>
  Serial.println(receivedTemperature);<br>
}<br>
<br>
if(RXget("radio1",address,"pressure")==true)<br>
{<br>
  Serial.print("receivedPressure = ");<br>
  Serial.println(receivedPressure);<br>
}<br>
<br>
if(RXget("radio1",address,"windDirection")==true)<br>
{<br>
  Serial.print("receivedWindDirection = ");<br>
  Serial.println(receivedWindDirection);<br>
}<br>
<br>
if(RXget("radio1",address,"windIntensity")==true)<br>
{<br>
  Serial.print("receivedWindIntensity = ");<br>
  Serial.println(receivedwindIntensity);<br>
}<br>
<br>
<br>
<br>
}<br>
</code></pre>