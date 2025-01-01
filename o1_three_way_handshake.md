Three-way handshaking is a process used in the **TCP (Transmission Control Protocol)** to establish a reliable connection between a client and a server before data is transmitted. It ensures that both parties are ready to communicate and can handle the transmission. Here's how it works:

### Steps in the Three-Way Handshake:
1. **SYN (Synchronize):**
   - The client initiates the connection by sending a **SYN** packet to the server.
   - This packet includes a **sequence number**, which serves as the starting point for data transmission from the client.

2. **SYN-ACK (Synchronize-Acknowledge):**
   - The server acknowledges the client's request by responding with a **SYN-ACK** packet.
   - The SYN-ACK packet contains:
     - The server's own sequence number (indicating its readiness to communicate).
     - An acknowledgment number, which is the client's sequence number incremented by 1 (to confirm receipt of the SYN packet).

3. **ACK (Acknowledge):**
   - The client responds to the server's SYN-ACK by sending an **ACK** packet.
   - This packet contains:
     - The acknowledgment number, which is the server's sequence number incremented by 1.
   - After this step, the connection is established, and data transmission can begin.

### Visualization:

```plaintext
Client                Server
  |    SYN (Seq=100)   |
  |------------------->|
  |                    |
  |  SYN-ACK (Seq=300, Ack=101) |
  |<-------------------|
  |                    |
  |    ACK (Ack=301)    |
  |------------------->|
Connection Established
```

### Key Points:
- The handshake ensures both parties are synchronized with initial sequence numbers.
- It establishes a reliable communication channel by confirming the receipt of packets.
- If any step fails (e.g., due to a timeout), the process restarts or the connection is aborted.

This handshake mechanism is critical for ensuring data integrity and reliability in TCP communication.
