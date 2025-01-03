### Domain and Subdomain, Address Resolution Overview

#### **Domain and Subdomain**
- **Domain**: A domain is the primary address of a website, such as `example.com`. It serves as a user-friendly identifier for accessing web resources.
- **Subdomain**: A subdomain is a subdivision of a domain, used to organize or navigate sections of a website. For example, `blog.example.com` is a subdomain of `example.com`.

#### **Address Resolution**
Address resolution is the process of mapping a human-readable domain name (like `example.com`) to an IP address (like `192.168.1.1`) that computers use to locate resources on the internet.

---

### **Steps in Address Resolution**
1. **Domain Name System (DNS) Query**:
   - The browser sends a request to a DNS resolver to find the IP address corresponding to the domain name.
   
2. **Cache Lookup**:
   - The resolver first checks its cache for the IP address.
   - If not found, it queries other DNS servers.

3. **Recursive or Iterative Resolution**:
   - Recursive: The resolver takes responsibility for querying all necessary DNS servers.
   - Iterative: The resolver queries each server one at a time until it finds the IP address.

4. **Contacting Authoritative Nameserver**:
   - The query is sent to the authoritative nameserver for the domain, which provides the IP address.

5. **Response to Client**:
   - The resolver returns the IP address to the browser, enabling the connection to the web server.

---

### **Key Components**
1. **Root Nameservers**: Direct queries to the appropriate top-level domain (TLD) server (e.g., `.com`, `.org`).
2. **TLD Nameservers**: Direct queries to the authoritative nameserver for the domain.
3. **Authoritative Nameservers**: Provide the IP address for the domain or subdomain.

---

Would you like to dive deeper into specific aspects, such as configuring subdomains or troubleshooting DNS issues?
