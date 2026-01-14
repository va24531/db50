# db50
DB50 Radio

9600 baud half duplex. Pin 1 Gnd / Pin 8 Data


# Keypad  ---- XXXXX Response
1 - AL~K1[0D][OA]
2 - AL~K2[0D][OA]
3 - AL~K3[0D][OA]
4 - AL~K4[0D][OA]
5 - AL~K5[0D][OA]
6 - AL~K6[0D][OA]
7 - AL~K7[0D][OA]
8 - AL~K8[0D][OA]
9 - AL~K9[0D][OA]
... other keys, A-D, #, /, * can be changed
... in accordance with this payload format.





// ------- Arduino D1 Mini ---------------
// Sends '1' over and over again. Just as
// Proof of concept.

void sendByteWithPause(byte b) {
  Serial.write(b);
  //delay(1000); // 1 second pause between bytes
}

void setup() {
  Serial.begin(9600);
}

void loop() {
  // Send the specified hex bytes one by one
  sendByteWithPause(0x41); // 'A'
  sendByteWithPause(0x4C); // 'L'
  sendByteWithPause(0x7E); // '~'
  sendByteWithPause(0x4B); // 'K'
  sendByteWithPause(0x31); // '1'
  sendByteWithPause(0x0B); // binary 10110000
  sendByteWithPause(0x05); // binary 01010000

  // Wait before repeating to avoid watchdog timeout
  delay(2000); // 2 seconds delay before repeating
}
