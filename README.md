# nRF52_external_programmer
Allows an nRF52840-DK to upload Forth code to the serial pins on an external nRF52 node

Implements an additional UART on UARTE1, allowing pins P0.03 and P0.04 of an nRF52840-DK to act as serial pins (TXD and RXD, respectively) for the purpose of uploading FORTH code files to an external nRF52.

Example Using one nRF52840-DK to upload Forth code to another nRF52840-DK:  
1. Use 3 dupont wires to make the following connections: GND <--> GND, P0.03 <--> P0.08, and P0.04 <--> P0.06, where pins P0.03 and P0.04 are on the source nRF52840-DK, and pins P0.06 and P0.08 are on the target nRF52840-DK.
2. On the source node, type 'ul' to upload the Forth source code to a buffer.
3. Type 'prog' to transfer the source code in the buffer to the target.  The upload speed will be regulated so as not to overrun the target. The behavior mimics what would occur if you were to manually type in the code to the REPL on the target.

Note: At present the program does not check for errors.  So, for example, if there were a syntax error in the code being uploaded, the target REPL would flag it, but the source node will blindly continue with the upload anyway.  This known limitation may be addressed in a future release.  However, since the main purpose of this code is just to install uploader code onto the target, which can then use that uploader for all future uploads, this known limitation isn't all that significant.
