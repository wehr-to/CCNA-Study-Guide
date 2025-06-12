# TCP and UDP Notes

## TCP three-way handshake order of messages (establishing a connection):
SYN ->  
<- SYN-ACK  
ACK ->

## TCP four-way handshake order of messages (terminating a connection):
FIN ->  
<- ACK  
<- FIN  
ACK ->

TCP: Forward Acknowledgement is used to indicate the sequence number of the next segment the host expects to receive.  
TCP: A ‘Sliding Window’ is used to dynamically adjust how large the window size is.

Layer 4 ephemeral port range (according to IANA): 49152 - 65535  
Layer 4 registered port range (according to IANA): 1024 - 49151  
Layer 4 well-known port range (according to IANA): 0 - 1023

For applications like real-time voice and video, UDP is preferred.  
For applications that require reliable communications, TCP is preferred.

The Layer 4 source port number is randomly selected by the host that initiates the data exchange.  
The Layer 4 destination port number indicates the Application Layer protocol.

The TCP header window size field is used for flow control.

---

## Q&A

**Q: What are Layer 4 addresses?**  
Port Numbers

**Q: What does TCP stand for?**  
Transmission Control Protocol

**Q: What does UDP stand for?**  
User Datagram Protocol

---

## UDP

UDP has less overhead.  
UDP is connectionless.

---

## TCP

TCP is connection-oriented.  
TCP provides data sequencing.  
TCP provides error recovery.  
TCP provides flow control.  
TCP provides reliable data transfer.
