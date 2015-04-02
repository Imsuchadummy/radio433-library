Here you can see the Radio433 library reference, to learn how to use this library.

# Radio433.h File Reference #

**`#include "Radio433.h"`**

# Functions #

**`radioDeclare(int TXpin, int RXpin, int PTTpin, int rate);`**

This function set the digital IO pins to be for transmit and receive data. Those pins will only be accessed if the transmitter or receiver is enabled,also set pin to enable transmitter,and speed in bits per second.Must call radioRXbegin() before you will get any messages.


_**`TXpin`**_ The Arduino pin number for transmitting data.

_**`RXpin`**_ The Arduino pin number for receiving data.

_**`PTTpin`**_ The Arduino pin number to enable the transmitter.

_**`rate`**_   Desired speed in bits per second.


&lt;hr&gt;



**`RXinverted(boolean inverted);`**

By default the RX pin is expected to be low when idle, and to pulse high for each data pulse. This flag forces it to be inverted. This may be necessary if your transport medium inverts the logic of your signal, such as happens with some types of A/V tramsmitter.

_**`inverted`**_ True to invert sense of receiver input.


&lt;hr&gt;



**`PTTinverted(boolean inverted);`**

By default the PTT pin goes high when the transmitter is enabled. This flag forces it low when the transmitter is enabled.

_**`inverted`**_ True to invert PTT.


&lt;hr&gt;



**`radioRXbegin();`**

Start the Phase Locked Loop listening to the receiver. Must do this before you can receive any messages.


&lt;hr&gt;


**`radioRXend();`**

Stop the Phase Locked Loop listening to the receiver No messages will be received until radioRXbegin() is called again.


&lt;hr&gt;


**`radioRXwait();`**

Block until a message is available then returns.


&lt;hr&gt;


**`radioRXwait(long millis);`**

Block until a message is available or for a max time.

_**`millis`**_ Maximum time to wait in milliseconds.


&lt;hr&gt;



**`radioRXloop();`**

This function must be called to receive any message.It gets message and it puts the message in internal buffer. Must be called first in the void loop to works fine.


&lt;hr&gt;



**`boolean RXevent();`**

Returns true if any message arrived.


&lt;hr&gt;



**`radioSend(String STRING);`**

Sends a String type message.

_**`STRING`**_  Message to send.


&lt;hr&gt;



**`radioSend(int INT);`**

Sends a int type number.

_**`INT`**_ Message to send.


&lt;hr&gt;



**`radioSend(long LONG);`**

Sends a long type number.

_**`LONG`**_ Message to send.


&lt;hr&gt;



**`radioSend(float FLOAT);`**

Sends a float type number.

_**`FLOAT`**_ Message to send.


&lt;hr&gt;



**`radioSend(byte BYTE);`**

Sends a byte type message.

_**`BYTE`**_ Message to send.


&lt;hr&gt;



**`radioSend(String from,String datakind,int INT);`**

Sends a addressable message at the format: address+datakind+String(INT).

_**`from`**_ Identify who sent the message .

_**`datakind`**_ Type of data that it will transmit,like this the receiver can know what was transmitted  by this "address" and manipulate the data more easily.

_**`INT`**_ data to send is a integer number.


&lt;hr&gt;



**`radioSend(String from,String to,String datakind,int INT);`**

Sends a point to point addressable message, with header "from+to+datakind" and the content as integer number.

_**`from`**_ Identify who sent the message .

_**`to`**_ Identify who will receive the message .

_**`datakind`**_ Type of data that it will transmit,like this the receiver can know what was transmitted  by this "address" and manipulate the data more easily.

_**`INT`**_ data to send is a integer number.


&lt;hr&gt;



**`radioSend(String from,String datakind,int FLOAT);`**

Sends a addressable message at the format: address+datakind+String(FLOAT).

_**`from`**_ Identify who sent the message .

_**`datakind`**_ Type of data that it will transmit,like this the receiver can know what was transmitted  by this "address" and manipulate the data more easily.

_**`FLOAT`**_ data to send is a float number.


&lt;hr&gt;



**`radioSend(String from,String to,String datakind,int FLOAT);`**

Sends a point to point addressable message, with header "from+to+datakind" and the content as float number.

_**`from`**_ Identify who sent the message .

_**`to`**_ Identify who will receive the message .

_**`datakind`**_ Type of data that it will transmit,like this the receiver can know what was transmitted  by this "address" and manipulate the data more easily.

_**`FLOAT`**_ data to send is a float number.


&lt;hr&gt;




**`radioSend(String from,String datakind,int LONG);`**

Sends a addressable message at the format: address+datakind+String(LONG).

_**`from`**_ Identify who sent the message .

_**`datakind`**_ Type of data that it will transmit,like this the receiver can know what was transmitted  by this "address" and manipulate the data more easily.

_**`LONG`**_ data to send is a long number.


&lt;hr&gt;



**`radioSend(String from,String to,String datakind,int LONG);`**

A point to point addressable message, with header "from+to+datakind" and the content as long number.

_**`from`**_ Identify who sent the message .

_**`to`**_ Identify who will receive the message .

_**`datakind`**_ Type of data that it will transmit,like this the receiver can know what was transmitted  by this "address" and manipulate the data more easily.

_**`LONG`**_ data to send is a long number.


&lt;hr&gt;



**`radioSend(String from,String datakind,int BYTE);`**

Sends a addressable message at the format: address+datakind+String(BYTE).

_**`from`**_ Identify who sent the message .

_**`datakind`**_ Type of data that it will transmit,like this the receiver can know what was transmitted  by this "address" and manipulate the data more easily.

_**`BYTE`**_ data to send is a byte.


&lt;hr&gt;



**`radioSend(String from,String to,String datakind,int BYTE);`**

A point to point addressable message, with header "from+to+datakind" and the content as byte.

_**`from`**_ Identify who sent the message .

_**`to`**_ Identify who will receive the message .

_**`datakind`**_ Type of data that it will transmit,like this the receiver can know what was transmitted  by this "address" and manipulate the data more easily.

_**`BYTE`**_ data to send is a byte.


&lt;hr&gt;



**`radioSend(String from,String to,String STRING);`**

A point to point addressable message, with header "from+to" and the content as String.

_**`from`**_ Identify who sent the message .

_**`to`**_ Identify who will receive the message .

_**`STRING`**_ data to send is a String.


&lt;hr&gt;



**`radioSend(String from,String to,String datakind,int STRING);`**

A point to point addressable message, with header "from+to+datakind" and the content as String.

_**`from`**_ Identify who sent the message .

_**`to`**_ Identify who will receive the message .

_**`datakind`**_ Type of data that it will transmit,like this the receiver can know what was transmitted  by this "address" and manipulate the data more easily.

_**`STRING`**_ data to send is a String.


&lt;hr&gt;



**`TXprint();`**

**TXprint()** says to next **radioSend()** function call prints the message on the serial when it send the message. **TXprint()** must be called before of RadioSend().


&lt;hr&gt;



**`TXprintln();`**

It says to next **radioSend()** function call prints the message on the serial with line carriage when it send the message. **TXprintln()** must be called before of **radioSend()**.


&lt;hr&gt;



**`radioRcv(String *STRING);`**

Assign the received message to a referecend String type variable.

_**`STRING`**_ A String variable to assume value of received message.


&lt;hr&gt;



**`radioRcv(String *INT);`**

Assign the received message to a referenced int type variable.

_**`INT`**_ A int variable to assume value of received message content.


&lt;hr&gt;



**`radioRcv(String *LONG);`**

Assign the received message to a referenced long type variable.

_**`LONG`**_ A long variable to assume value of received message content.


&lt;hr&gt;



**`radioRcv(String *FLOAT);`**

Assign the received message to a referenced float type variable.

_**`FLOAT`**_ A float variable to assume value of received message content.


&lt;hr&gt;



**`radioRcv(String *BYTE);`**

Assign the received message to a referenced byte type variable.

_**`BYTE`**_ A byte variable to assume value of received message content.


&lt;hr&gt;



**`radioRcv(String from,String datakind,int *value);`**

If the received message starts with the "from+datakind" header, meaning the message was send by "from",and its kind of data is "datakind", the function assigns the rest of received message  to a int type referenced variable.

_**`from`**_ Address to compare with received message header.

_**`datakind`**_ Type of data that transmitter has to send to this function to assign the correct value to the variable defined in the next field.

_**`*value`**_ A int variable to assume value of received message content.


&lt;hr&gt;



**`radioRcv(String from,String datakind,float *value);`**

If the received message starts with the "from+datakind" header, meaning the message was send by "from",and its kind of data is "datakind", the function assigns the rest of received message  to a float type referenced variable.

_**`from`**_ Address to compare with received message header.

_**`datakind`**_ Type of data that transmitter has to send to this function to assign the correct value to the variable defined in the next field.

_**`*value`**_ A float variable to assume value of received message content.


&lt;hr&gt;



**`radioRcv(String from,String datakind,long *value);`**

If the received message starts with the "from+datakind" header, meaning the message was send by "from",and its kind of data is "datakind", the function assigns the rest of received message  to a long type referenced variable.

_**`from`**_ Address to compare with received message header.

_**`datakind`**_ Type of data that transmitter has to send to this function to assign the correct value to the variable defined in the next field.

_**`*value`**_ A long variable to assume value of received message content.


&lt;hr&gt;



**`radioRcv(String from,String datakind,byte *value);`**

If the received message starts with the "from+datakind" header, meaning the message was send by "from",and its kind of data is "datakind", the function assigns the rest of received message  to a byte type referenced variable.

_**`from`**_ Address to compare with received message header.

_**`datakind`**_ Type of data that transmitter has to send to this function to assign the correct value to the variable defined in the next field.

_**`*value`**_ A byte variable to assume value of received message content.


&lt;hr&gt;




**`radioRcv(String from,String to,String datakind,int *value);`**

If the received message starts with the "from+to+datakind" header, meaning the message was send by "from" to "to",and its kind of data is "datakind", the function assigns the rest of received message  to a int type referenced variable.

_**`from`**_ Address to compare with received message header.

_**`to`**_ your address, to verify if the message was for you.

_**`datakind`**_ Type of data that transmitter has to send to this function to assign the correct value to the variable defined in the next field.

_**`*value`**_ A int variable to assume value of received message content.


&lt;hr&gt;



**`radioRcv(String from,String to,String datakind,float *value);`**

If the received message starts with the "from+to+datakind" header, meaning the message was send by "from" to "to",and its kind of data is "datakind", the function assigns the rest of received message  to a float type referenced variable.

_**`from`**_ Address to compare with received message header.

_**`to`**_ your address, to verify if the message was for you.

_**`datakind`**_ Type of data that transmitter has to send to this function to assign the correct value to the variable defined in the next field.

_**`*value`**_ A float variable to assume value of received message content.


&lt;hr&gt;



**`radioRcv(String from,String to,String datakind,long *value);`**

If the received message starts with the "from+to+datakind" header, meaning the message was send by "from" to "to",and its kind of data is "datakind", the function assigns the rest of received message  to a long type referenced variable.

_**`from`**_ Address to compare with received message header.

_**`to`**_ your address, to verify if the message was for you.

_**`datakind`**_ Type of data that transmitter has to send to this function to assign the correct value to the variable defined in the next field.

_**`*value`**_ A long variable to assume value of received message content.


&lt;hr&gt;



**`radioRcv(String from,String to,String datakind,byte *value);`**

If the received message starts with the "from+to+datakind" header, meaning the message was send by "from" to "to",and its kind of data is "datakind", the function assigns the rest of received message  to a byte type referenced variable.

_**`from`**_ Address to compare with received message header.

_**`to`**_ your address, to verify if the message was for you.

_**`datakind`**_ Type of data that transmitter has to send to this function to assign the correct value to the variable defined in the next field.

_**`*value`**_ A byte variable to assume value of received message content.


&lt;hr&gt;



**`radioRcv(String from,String to,String datakind,String *value);`**

If the received message starts with the "from+to+datakind" header, meaning the message was send by "from" to "to",and its kind of data is "datakind", the function assigns the rest of received message to a String type referenced variable.

_**`from`**_ Address to compare with received message header.

_**`to`**_ your address, to verify if the message was for you.

_**`datakind`**_ Type of data that transmitter has to send to this function to assign the correct value to the variable defined in the next field.

_**`*value`**_ A String variable to assume value of received message content.


&lt;hr&gt;



**`radioRcv(String from,String to,String *value);`**

If the received message starts with the "from+to" header, meaning the message was send by "from" to "to", the function assigns the rest of received message to a String type referenced variable.

_**`from`**_ Address to compare with received message header.

_**`to`**_ your address, to verify if the message was for you.

_**`*value`**_ A String variable to assume value of received message content.


&lt;hr&gt;



**`RXprint();`**

Prints the last received message on the serial.


&lt;hr&gt;



**`RXprintln();`**

Prints the last received message on the serial, with line carriage.


&lt;hr&gt;



**`RXprint(String from,String to);`**

If the last received message was adressable and with right "from+to" header, prints its content on the serial.

_**`from`**_ Address to compare with received message header.

_**`to`**_ your address, to verify if the message was for you.


&lt;hr&gt;



**`RXprintln(String from,String to);`**

If the last received message was adressable and with right "from+to" header, prints its content on the serial,with line carriage.

_**`from`**_ Address to compare with received message header.

_**`to`**_ your address, to verify if the message was for you.


&lt;hr&gt;



**`boolean RXget(String STRING);`**

Returns true if when a message arrive it is equals to the argument.


&lt;hr&gt;



**`boolean RXget(String from,String to);`**

Returns true when a message arrive and it starts with the argurment "from+to",useful to manipulate addressable data.

_**`from`**_ Address to compare with received message header.

_**`to`**_ your address, to verify if the message was for you.


&lt;hr&gt;



**`boolean RXget(String from,String to,String datakind);`**

Returns true when a message arrive and it starts with the argurment "from+to+datakind",useful to manipulate specific received value type.

_**`from`**_ Address to compare with received message header.

_**`to`**_ your address, to verify if the message was for you.

_**`datakind`**_ Type of data that you wait transmitter sent.


&lt;hr&gt;



**`cypher(boolean active);`**

Enable or disable cypher text mode;

_**`active`**_ If true Radio433 will work in cypher text mode ( encrypting and decrypting messages),else won't.


&lt;hr&gt;



**`boolean cypher();`**

Returns status of cypher mode,  if activated true, else false;

**`keyAssign(int key [27]);`**

To assign a key to cypher text mode can encrypt and decrypt messages.If key is not valid it will print on the serial : "key is not valid".


&lt;hr&gt;



_**`key [27]`**_  A array with length equals 27, with integers number between 0 and 50.


&lt;hr&gt;



**`String RXbuf();`**

Returns a String with the last received message on buffer.
