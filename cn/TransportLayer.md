

### Transport Layer  
The transport layer is part of a network system that ensures data is sent from one specific application or process on a computer to another specific application or process on a different computer. It provides reliable communication between software programs.

---

### Key Components:  

#### 1. **UDP (User Datagram Protocol):**  
- A fast, lightweight protocol for sending data without checking if it was received.  
- Useful for real-time applications like online gaming and video streaming.

#### 2. **TCP (Transmission Control Protocol):**  
- A reliable protocol that ensures all data is delivered correctly and in order.  
- Used for applications like web browsing, file transfers, and emails.

---

### Congestion Control Algorithms  

1. **Leaky Bucket Algorithm:**  
This method sends data at a steady, fixed speed, like water dripping from a small hole in a bucket. It stops the network from getting too busy by spreading out the data.  

2. **Token Bucket Algorithm:**  
This method allows data to be sent in bursts if there are enough "tokens." Each token is like a ticket to send some data, and new tokens are added over time.

---

### Quality of Service (QoS):  
- A set of rules and techniques to ensure important data (like video calls) gets priority over less critical data (like file downloads).  
- Improves user experience by reducing delays, jitter, and packet loss in a network.
