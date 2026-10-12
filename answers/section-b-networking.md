# Section B — Networking Fundamentals

## Q4. What Is Networking? (5 Marks)

### 1. Definition of a Computer Network

A computer network is a collection of two or more computing devices connected through wired or wireless communication links to exchange data and share resources and services. These devices communicate using agreed rules called network protocols.

### 2. Why Do Organizations Use Networks?

Organizations use computer networks for the following purposes:

- **Resource sharing:** Employees can share printers, files, storage, and other resources.
- **Communication:** Users can communicate through email, messaging, and video conferencing.
- **Data sharing:** Authorized users can access shared information and databases.
- **Centralized management:** Administrators can manage users, devices, and security policies more efficiently.
- **Internet access:** Multiple devices can access internet services through a shared network connection.
- **Cost efficiency:** Sharing resources can reduce the need for separate equipment and services.

### 3. Types of Networks

#### A. Personal Area Network (PAN)

A PAN is a small network that connects personal devices over a short distance, usually around one person.

**Example:** A smartphone connected to wireless earbuds through Bluetooth.

#### B. Local Area Network (LAN)

A LAN connects devices within a limited geographical area, such as a home, office, computer laboratory, or college building.

**Example:** Computers in a university computer laboratory connected to a common network.

#### C. Metropolitan Area Network (MAN)

A MAN connects multiple LANs across a city or metropolitan area. It generally covers a larger area than a LAN but a smaller area than a WAN.

**Example:** A city-wide network connecting the branches of an organization across the same city.

#### D. Wide Area Network (WAN)

A WAN connects networks across large geographical areas, such as different cities, countries, or continents.

**Example:** A company connecting its offices in Ahmedabad, Mumbai, and Delhi through a wide-area network.

### 4. Comparison of Network Types

| Network Type | Typical Coverage | Example |
|---|---|---|
| PAN | Around an individual | Phone connected to Bluetooth earbuds |
| LAN | Home, office, or building | College computer laboratory |
| MAN | City or metropolitan area | Organization's city-wide network |
| WAN | Large geographical areas | Company network connecting offices in different cities |

### Conclusion

Computer networking enables devices to communicate and share resources efficiently. PAN, LAN, MAN, and WAN differ mainly in their geographical coverage and the networks or devices they connect.



## Q5. Network Devices (5 Marks)

### 1. Hub

A hub is a basic networking device that connects multiple devices in a LAN. When it receives data on one port it repeats that data to all its other ports without identifying the intended destination.

**Example:** In a small network, a hub connects several computers, but it sends incoming data to all connected devices.

**Limitation:** Hubs do not filter traffic based on destination addresses and can create unnecessary network traffic.

### 2. Switch

A switch connects devices within a LAN and forwards Ethernet frames to the appropriate port using the destination MAC address. It learns MAC addresses to help deliver frames to the correct devices.

**Example:** A college laboratory uses a switch to connect computers, printers, and servers on the same local network.

### 3. Router

A router connects different IP networks and forwards packets between them using IP addresses and routing information. A home or office router commonly connects the local network to the internet.

**Example:** A router forwards traffic from an office LAN toward the internet service provider's network.

### 4. Firewall

A firewall monitors and controls network traffic according to configured security rules. Depending on its capabilities and configuration, it can allow or block traffic based on factors such as IP addresses, ports, protocols, and connection state.

**Example:** A company firewall blocks unauthorized incoming connections to internal computers while permitting approved web traffic.

### 5. Wireless Access Point (AP)

A wireless access point allows Wi-Fi-enabled devices to connect to a network. It bridges wireless devices to the network's wired infrastructure.

**Example:** A college access point allows students' laptops and smartphones to connect to the campus network through Wi-Fi.

### Major Difference Between a Switch and a Router

A **switch primarily forwards frames within a LAN using MAC addresses**, whereas a **router forwards packets between different IP networks using IP addresses and routing information**.

For example, a switch can connect computers within a college laboratory, while a router can forward their traffic from the laboratory's network toward the internet.

### Conclusion

Hubs repeat data to connected ports, switches forward frames within a LAN, routers connect IP networks, firewalls enforce traffic-control rules, and access points provide wireless network connectivity. Each device has a distinct role in building and managing a network.



## Q6. How the Internet Works (10 Marks)

### Step-by-Step Explanation

**Step 1: User enters the domain name**

The user enters `https://example.com` into the browser's address bar. The browser identifies the domain name and prepares to connect to the website using HTTPS.

**Step 2: DNS resolves the domain name**

Computers communicate over IP networks using IP addresses rather than relying directly on human-readable domain names. The browser or operating system may first check its cache. If a suitable record is not cached, a DNS resolver helps find the IP address associated with `example.com`.

DNS stands for **Domain Name System**. It translates domain names into IP addresses, allowing the browser to locate the destination server.

**Step 3: The device determines where to send the traffic**

The computer uses its IP configuration and routing table to determine how to reach the destination IP address. If the destination is outside the local network, the computer normally sends the traffic to its default gateway.

**Step 4: The router forwards the traffic**

The default gateway is commonly a router on the local network. It forwards packets toward the destination through the appropriate network route, potentially passing through several routers before reaching the destination network.

**Step 5: TCP/IP supports communication**

The TCP/IP protocol suite provides the rules used for communication across networks. IP handles packet addressing and forwarding, while TCP can provide reliable, ordered delivery for applications that use it.

For a typical HTTPS connection using TCP, the client establishes a TCP connection to the server. HTTPS then uses TLS to help secure the communication. Some modern browsers and servers can instead use HTTP/3, which runs over QUIC and UDP.

**Step 6: The browser sends an HTTP request**

After the required connection and security setup, the browser sends an HTTP request asking the web server for the requested resource.

**Step 7: The web server responds**

The web server processes the request and returns an HTTP response containing the requested webpage or other content. The response travels back through the network to the user's device.

**Step 8: The browser displays the webpage**

The browser processes the returned HTML, CSS, JavaScript, and other resources as needed, then renders the webpage for the user.

### Flow Diagram

The complete flow diagram is available here:

[How the Internet Works](../diagrams/how-internet-works.md)

### Conclusion

Accessing a website involves more than entering a domain name. DNS helps locate the destination server, IP and routers carry packets across networks, transport and security protocols support communication, and HTTP allows the browser and web server to exchange web content.