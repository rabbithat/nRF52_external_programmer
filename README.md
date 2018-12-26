# nRF52_external_programmer
Allows an nRF52840-DK to upload Forth code to the serial pins on an external nRF52 node

Implements an additional UART on UARTE1, allowing pins P0.03 and P0.04 of an nRF52840-DK to act as serial pins (TXD and RXD, respectively) for the purpose of uploading FORTH code files to an external nRF52.

Example Using one nRF52840-DK to upload Forth code to another nRF52840-DK:  
1. Use 3 dupont wires to make the following connections: GND <--> GND, P0.03 <--> P0.08, and P0.04 <--> P0.06, where pins P0.03 and P0.04 are on the source nRF52840-DK, and pins P0.06 and P0.08 are on the target nRF52840-DK.
2. On the source node, type 'ul' to upload the Forth source code to a buffer.
3. Type 'prog' to transfer the source code to the target.  The upload speed will be regulated so as not to overrun the target.
