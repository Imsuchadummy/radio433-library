# How to use cipher text mode #

Cipher text mode is used to encrypt and decrypt messages, and is not a safe algorithm, actually is very simple and is just to mask the content of messages.

In Radio433 each message only have a maximum of 27 characters (bigger messages are send per packets, each packet also have a maximum lentgh of 27 characters). As so, the key array to encrypt each message (or packet) have 27 integers numbers.
When cypher() is true, each message character  is increased by correspondent position int number of key array.To decrypt, the receiver (must to have the same key array) decrease the received character by correspondent position int number of key array:
```
int key [27]={1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27};

String message="hello world!";
// to encrypt , "char+int"

for(int i=0;i<message.length;i++)
{message [i]=char( message[i]+key[i] );
}

//to decrypt we do inverted

for(int k=0;k<message.length;k++)
{message [k]=char( message[k]-key[k] );
}


```

See this cipher text mode running in "Radio433\_cypher\_demo.ino" sketch, only needs a arduino board attached on computer:

```
//Cypher.pde
#include <Radio433.h>



void setup()
{
  radioDeclare(11,10,3,2000);
  int key[27]={1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27};
  cypher(true);
  keyAssign(key);
  Serial.begin(9600);
  Serial.println("This sketch shows how to send a encrypted text.");
  delay(500);
  Serial.println("This algorithm is only to mask your data, it is not sophisticated enough to ensure a secure communication.");
  delay(500);
  Serial.println("First,a message without cypher appears as:");
  delay(500);
  cypher(false);
  TXprintln();
  radioSend("A simple text to test");
  Serial.println("Now, we go to apply cypher code, and the text appears as:");
  cypher(true);
  TXprintln();
  radioSend("A simple text to test");
  Serial.println("If you want to know if ""cypher"" is activated, you can use boolean cypher() function:");
  Serial.println("Cypher status is:"+String(cypher()));
  cypher(false);
  Serial.println("Now, cypher status was changed to:"+String(cypher()));
  Serial.println("To receive a encrypted message, you only need use the same key in both, and activate cypher mode with cypher(true) statement.");
  
  
}

void loop()
{}

```