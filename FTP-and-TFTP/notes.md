# FTP and TFTP Notes

- FTP data connections use TCP port 20.  
- FTP control connections use TCP port 21.  
- In FTP passive mode, the client initiates the data connection.  
- In FTP active mode, the server initiates the data connection.  
- TFTP servers listen on UDP port 69.  
- TFTP uses 'lock-step' communication, in which the client and server alternately send messages.  
- The disk file system type is used for storage devices such as flash memory.  
- The NVRAM file system type is used for the device's internal NVRAM.  
- The network file system type represents external file systems, for example FTP/TFTP servers.  
- The opaque file system type represents logical systems used for internal functions.  

---

## FTP and TFTP Q&A

**Q: Does FTP use authentication?**  
A: Yes (username/PW)

**Q: Does FTP use encryption?**  
A: No (FTPS does)

**Q: Does TFTP use authentication?**  
A: No (no username/PW)

**Q: Does TFTP use encryption?**  
A: No

**Q: The random ports used in TFTP are also called:**  
A: TIDs (Transfer IDs)

**Q: What are the three phases of a TFTP file transfer?**  
1: Connection  
2: Data transfer  
3: Connection termination

**Q: What does FTP stand for?**  
A: File Transfer Protocol

**Q: What does TFTP stand for?**  
A: Trivial File Transfer Protocol

**Q: What does the TFTP 'TID' stand for?**  
A: Transfer ID

**Q: What two kinds of connection are used in FTP?**  
1: Control  
2: Data

**Q: Which protocol is more lightweight and simple, FTP or TFTP?**  
A: TFTP

**Q: Which protocol provides more functionality, FTP or TFTP?**  
A: FTP
