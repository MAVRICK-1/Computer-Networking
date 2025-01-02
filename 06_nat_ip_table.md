**Network Address Translation (NAT)** is a method used to share a single public IP address among multiple devices in a private network. It works by modifying the IP address in data packets as they pass through a router, allowing devices in the private network to communicate with the internet while hiding their private IP addresses.
---

### **IP Masquerading:**  
IP masquerading is a type of NAT where all devices in a private network appear to have the same public IP address to the outside world. It's like a family sharing one phone number; when someone calls back, the router makes sure the right person (device) gets the call.

---

### **IPTables:**  
IPTables is a tool in Linux used to manage the rules for how data packets are handled in a network. It can be used for tasks like:  
- Allowing or blocking specific types of traffic (firewall).  
- Redirecting traffic (port forwarding).  
- Applying NAT for address translation.  

Think of it as a set of rules that controls which traffic is allowed in, out, or through your system.
