# Using Radio433 to chat over RF #

This example shows how to chat through Radio433 using arduino serial monitor to we use our keyboard to write the messages.Prepare 2 computers in your radio range, notebooks are better.

This example needs :

2 - computers with arduino ide installed ( runs with only one PC, but with 2 is more funny).

2 - Arduino Uno boards (or compatibles).

2 - 433Mhz ASK transmitters.

2 - 433Mhz ASK receivers.

Mount each arduino board as diagram:

<img src='http://2.bp.blogspot.com/-DdjqJ1Btd_g/VMJxRrHHVWI/AAAAAAAAAGQ/jGGPTTypnAg/s1600/test%2Bboard.png'>

And upload "Radio433_chat_1.ino" in one Arduino:<br>
<pre><code>//Simple chat implemented with Radio433 library, <br>
<br>
<br>
#include &lt;Radio433.h&gt;<br>
int key[27]={1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27};// key to criptography, needs to have 27 int numbers, between 0 and 126<br>
String myName="radio1";//address from this arduino<br>
String myFriendName="radio2";// address of the other arduino you who chat, to do addressable communication<br>
String SerialBuffer;<br>
int cont=0;<br>
void setup()<br>
{<br>
  radioDeclare(11,10,3,2000);<br>
  cypher(true);// turn on cypher mode<br>
  keyAssign(key);// assign the key to cypher all messages that going to send<br>
  radioRXbegin();// start PLL, needed to receive incoming data<br>
  Serial.begin(9600);<br>
  <br>
  delay(500);<br>
  Serial.println("Chat via Radio433:");<br>
}<br>
<br>
void loop()<br>
{<br>
  radioRXloop();<br>
  //RXprintln();<br>
  if(RXget(myFriendName,myName)==true)<br>
  {Serial.print(myFriendName+" said: ");<br>
   RXprintln(myFriendName,myName);<br>
  }<br>
    <br>
    if (Serial.available() &gt; 0){<br>
    // Lê toda string recebida<br>
    String recebido = leStringSerial();<br>
   // Serial.println(recebido);<br>
   Serial.println("I said: "+recebido);<br>
   radioSend(myName,myFriendName,recebido);<br>
    }<br>
 <br>
  <br>
}<br>
<br>
String leStringSerial(){<br>
  String conteudo = "";<br>
  char caractere;<br>
  <br>
  // Enquanto receber algo pela serial<br>
  while(Serial.available() &gt; 0) {<br>
    // Lê byte da serial<br>
    caractere = Serial.read();<br>
    // Ignora caractere de quebra de linha<br>
    if (caractere != '\n'){<br>
      // Concatena valores<br>
      conteudo.concat(caractere);<br>
    }<br>
    // Aguarda buffer serial ler próximo caractere<br>
    delay(10);<br>
  }<br>
    <br>
  //Serial.print("Recebi: ");<br>
 // Serial.println(conteudo);<br>
    <br>
  return conteudo;<br>
}<br>
</code></pre>

And "Radio433_chat_2.ino" in other:<br>
<br>
<pre><code>#include &lt;Radio433.h&gt;<br>
int key[27]={1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27};// key to criptography, needs to have 27 int numbers, between 0 and 126<br>
String myName="radio2";//address from this arduino<br>
String myFriendName="radio1";// address of the other arduino, to do addressable communication<br>
String SerialBuffer;<br>
int cont=0;<br>
void setup()<br>
{<br>
  radioDeclare(11,10,3,2000);<br>
  cypher(true);// turn on cypher mode<br>
  keyAssign(key);// assign the key to cypher all messages that going to send<br>
  radioRXbegin();// start PLL, needed to receive incoming data<br>
  Serial.begin(9600);<br>
  <br>
  delay(500);<br>
  Serial.println("Chat via Radio433:");<br>
}<br>
<br>
void loop()<br>
{<br>
  radioRXloop();<br>
  if(RXget(myFriendName,myName))<br>
  {Serial.print(myFriendName+" said: ");<br>
   RXprintln(myFriendName,myName);<br>
  }<br>
    <br>
    if (Serial.available() &gt; 0){<br>
    // Lê toda string recebida<br>
    String recebido = leStringSerial();<br>
   // Serial.println(recebido);<br>
   Serial.println("I said: "+recebido);<br>
   radioSend(myName,myFriendName,recebido);<br>
    }<br>
 <br>
  <br>
}<br>
<br>
String leStringSerial(){<br>
  String conteudo = "";<br>
  char caractere;<br>
  <br>
  // Enquanto receber algo pela serial<br>
  while(Serial.available() &gt; 0) {<br>
    // Lê byte da serial<br>
    caractere = Serial.read();<br>
    // Ignora caractere de quebra de linha<br>
    if (caractere != '\n'){<br>
      // Concatena valores<br>
      conteudo.concat(caractere);<br>
    }<br>
    // Aguarda buffer serial ler próximo caractere<br>
    delay(10);<br>
  }<br>
    <br>
  //Serial.print("Recebi: ");<br>
 // Serial.println(conteudo);<br>
    <br>
  return conteudo;<br>
}<br>
</code></pre>

Now open serial monitor, write some stuff and click send.Fun.