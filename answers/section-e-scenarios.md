# Section E — Scenario-Based Questions

## Q12. Scenario — Company Network (10 Marks)

### 1. Understanding the Requirements

The company has:

- 45 employees
- 5 servers
- 10 network devices

The company needs a reliable and secure network that allows employees to communicate, access shared resources, use internal servers, and connect to the internet.

### 2. Type of Network Required

The company should use a **Local Area Network (LAN)** to connect employees' computers, servers, printers, and other devices within its office.

If the company has offices in different cities, those separate LANs could be connected using a Wide Area Network (WAN) or other suitable inter-site connectivity.

### 3. Required Network Devices

| Device | Purpose |
|---|---|
| Router | Connects the company's LAN to the internet and forwards packets between IP networks. |
| Network switch(es) | Connect employees' computers, servers, access points, and other wired devices within the LAN. |
| Firewall | Applies security rules to control permitted and blocked network traffic. |
| Wireless access point(s) | Provide Wi-Fi connectivity for authorized wireless devices. |
| Modem or ONT, if required | Provides the connection to the internet service provider, depending on the type of internet connection. |
| Servers | Provide services such as file sharing, authentication, internal applications, or database access. |
| End-user devices | Employees' computers, laptops, and other devices used to access network services. |
| Ethernet cables | Provide wired connections between devices and the network infrastructure. |

The company should choose the number and capacity of switches, access points, and other devices based on the actual equipment count, port requirements, expected traffic, and future growth.

### 4. Proposed Network Design

The company's logical network design is shown in the separate diagram file:

[View the Company Network Design](../diagrams/company-network-design.md)

### 5. Roles of the Router, Switch, and Firewall

**Router:** The router forwards packets between different IP networks. It commonly acts as the default gateway for devices on the company's LAN and forwards internet-bound traffic toward the ISP.

**Switch:** The switch connects devices within the LAN and forwards Ethernet frames using MAC addresses. It allows employees' computers and servers to communicate within the local network.

**Firewall:** The firewall enforces security rules to control network traffic. It can restrict unauthorized connections, permit approved services, and help protect internal systems from unwanted traffic.

**Wireless access point:** The access point provides Wi-Fi connectivity and bridges authorized wireless devices to the company's network.

### 6. How an Employee's Request Reaches a Website

When an employee enters a website address in a browser, the following steps occur:

1. **DNS resolution:** The employee's device uses DNS to resolve the website's domain name to an IP address, unless a suitable result is already cached.
2. **Destination check:** The device checks whether the destination belongs to its local subnet. For an external website, it normally sends traffic to its default gateway.
3. **Router forwarding:** The router forwards the packets toward the ISP and the destination network.
4. **Firewall inspection:** The firewall applies its configured security rules to the traffic at the point where the traffic passes through it.
5. **Internet communication:** Packets travel through networks and routers toward the website's server using IP routing.
6. **Web request and response:** The browser establishes the required connection and sends an HTTP request, usually protected by HTTPS. The web server returns an HTTP response.
7. **Display:** The response reaches the employee's device, and the browser processes and displays the webpage.

### 7. Security and Reliability Recommendations

- Use strong authentication and restrict access to authorized users.
- Keep operating systems, applications, and network devices updated.
- Separate employee, server, and guest Wi-Fi traffic using appropriate VLANs and firewall rules where supported.
- Back up important server data regularly and test recovery procedures.
- Monitor network activity and maintain logs to help detect suspicious behavior.
- Use suitable network capacity and maintain an inventory of connected devices.

### Conclusion

A well-designed company LAN uses switches to connect internal devices, a router to forward traffic between networks, and a firewall to enforce security policies. Wireless access points and servers provide additional connectivity and services. Proper access controls, updates, backups, and monitoring help make the network secure and reliable.



## Q13. Network Troubleshooting Scenario (10 Marks)

**Scenario:** A user has the IP address `192.168.1.25/24`. The user can communicate with devices on the local network but cannot access external websites.

### 1. Check the IP Configuration

First, verify that the computer has the correct IP address, subnet mask, default gateway, and DNS server.

On Windows, run:

```text
ipconfig /all
```

Expected configuration includes:

- **IP address:** `192.168.1.25`
- **Subnet mask:** `255.255.255.0`
- **Default gateway:** The actual IP address of the local router, commonly `192.168.1.1`
- **DNS server:** The IP address of the configured DNS resolver

If the gateway or DNS settings are missing or incorrect, correct the configuration or contact the network administrator. Also check for duplicate IP addresses and incorrect static IP settings.

### 2. Test the Default Gateway

Use the following command, replacing the example gateway with the actual gateway shown in the IP configuration:

```text
ping 192.168.1.1
```

**Purpose:** This tests whether the computer can reach its local router.

- If the gateway responds, local connectivity to the router is likely working.
- If it does not respond, check the Wi-Fi or Ethernet connection, network adapter, switch port, VLAN configuration, and gateway settings.

A failed ping does not always prove the gateway is unreachable because a firewall may block ICMP traffic.

### 3. Test External Network Connectivity

Try reaching a known public IP address:

```text
ping 8.8.8.8
```

You can also use the following command on Windows to inspect the route:

```text
tracert 8.8.8.8
```

**Purpose:** These tests help determine whether traffic can travel beyond the local network.

- If the gateway responds but external connectivity fails, investigate the router's WAN connection, routing, firewall rules, and the ISP connection.
- If the public IP responds but a website name does not work, DNS may be the problem.

Ping and traceroute results are clues rather than absolute proof because some networks block or limit ICMP traffic.

### 4. Test DNS Resolution

Run:

```text
nslookup example.com
```

**Purpose:** This checks whether the configured DNS resolver can translate the domain name `example.com` into an IP address.

- If an IP address is returned, DNS resolution is working for that query.
- If the lookup fails, check the configured DNS server, DNS service availability, and network or firewall rules affecting DNS traffic.

If necessary, clear the local DNS cache on Windows:

```text
ipconfig /flushdns
```

Then retry the website. Use only DNS resolvers approved by the organization.

### 5. Check the Router and Internet Connection

If local communication works but external connectivity does not, the network administrator should check:

- Whether the router has a working WAN connection.
- Whether the router has a valid default route.
- Whether IPv4 NAT is configured where required for private IPv4 addresses to access the public internet.
- Whether firewall rules are blocking outbound traffic.
- Whether the ISP is experiencing an outage.
- Whether other users on the same network have the same problem.

If other devices also cannot access external websites, the issue may be with the router, firewall, or ISP rather than the user's computer.

### 6. Troubleshooting Summary

| Test | What it checks | Possible conclusion if it fails |
|---|---|---|
| `ipconfig /all` | IP, gateway, and DNS settings | Incorrect or missing configuration |
| `ping` to the gateway | Local path to the router | Local link, VLAN, gateway, or ICMP filtering issue |
| `ping` to a public IP | Basic external IP connectivity | Routing, firewall, WAN, or ISP issue |
| `nslookup example.com` | DNS resolution | DNS configuration or resolver issue |
| `tracert 8.8.8.8` | Network path toward a public IP | Helps identify where the path may stop |

### Conclusion

The user can communicate locally, so the local network is at least partly functioning. However, this does not prove that the default gateway, internet route, or DNS service is working. Troubleshooting should proceed from IP configuration to gateway reachability, external IP connectivity, DNS resolution, and finally router, firewall, and ISP checks. Testing each layer in order helps identify the likely cause without making unnecessary configuration changes.