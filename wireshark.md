***Lucky Beulla Muhoza***

***CS 338***

***Prof. Jeff Ondich***

## Getting started with Wireshark ##
**DAYTIME** 

1. Identify the parts of the TCP 3-way handshake by listing the frame summaries of the relevant frames. 
* <img width="1207" alt="Screenshot 2024-09-19 at 9 09 14 PM" src="https://github.com/user-attachments/assets/2c586518-20a2-4646-a8d5-538b8fbd9f91">

2. What port number does the client (i.e. nc on your Kali computer) use for this interaction?

* The client uses port _46430_, observed from the info column where the connection is being initiated from nc to the NIST time server at port 13

4. Why does the client need a port?

* To establish a unique connection for communication with the server. This allows the system to distinguish between multiple simultaneous connections and direct incoming traffic to their correct destination.
   
5. What frame contains the actual date and time? 

* Frame 4 with protocal as DAYTIME
  <img width="940" alt="Screenshot 2024-09-19 at 9 22 12 PM" src="https://github.com/user-attachments/assets/47641de4-3558-467f-888d-847830a0e027">


6. What do [SYN] and [ACK] mean?

* Synchronize [SYN]: initiates a TCP connection. Tells the receiving server (in this case NIST time server) that the sender (nc on kali) wants to establish a connection

* Acknowledgement [ACK]: acknowledges the receipt of a connection (SYN), thus ensuring that both the client and server agree on the connection state

7. Which entity (the nc client or the daytime server) initiated the closing of the TCP connection? How can you tell?
* <img width="1171" alt="Screenshot 2024-09-19 at 9 28 45 PM" src="https://github.com/user-attachments/assets/75b6d52a-e3a0-43a4-a089-5d0d284f9454">
  The NIST time server client initiated the closing TCP connection [FIN]. In frame 5, the connection is going out from port 13 to 46430 (or the nc IP address to the NIST time IP address).


**HTTP**

1. How many TCP connections were opened? How can you tell?
2. Can you tell where my homepage (index.html) was requested? (If not, why not? If so, include frame summaries and/or other info that supports your answer.)
3. Can you tell where my photograph (jeff-square-colorado.jpg) was requested? (If not, why not? If so, include frame summaries and/or other info that supports your answer.)

