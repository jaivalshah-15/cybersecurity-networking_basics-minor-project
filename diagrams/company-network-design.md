# Company Network Design

## Scenario

The company has 45 employees, 5 servers, and 10 network devices. The proposed design uses a LAN for internal communication and a router and firewall to provide controlled internet connectivity.

## Logical Network Diagram

```text
                       INTERNET
                           |
                    +--------------+
                    | ISP Modem/ONT|
                    | (if required)|
                    +------+-------+
                           |
                    +------+-------+
                    |    ROUTER    |
                    | Default      |
                    | Gateway      |
                    +------+-------+
                           |
                    +------+-------+
                    |   FIREWALL   |
                    | Security     |
                    | Rules        |
                    +------+-------+
                           |
                    +------+-------+
                    | CORE SWITCH  |
                    +------+-------+
                           |
             +-------------+--------------+
             |             |              |
      +------+-----+ +-----+------+ +-----+------+
      | Employee   | | Server     | | Wireless   |
      | Computers  | | Network    | | Access     |
      | and Printers| | 5 Servers  | | Points     |
      +------------+ +------------+ +------------+
```

## Device Roles

- **Router:** Forwards packets between the company's LAN and external IP networks.
- **Firewall:** Enforces security rules for permitted and blocked traffic.
- **Switch:** Connects employee computers, servers, and other wired devices within the LAN.
- **Wireless access points:** Allow authorized wireless devices to connect to the network.
- **Servers:** Provide services such as file sharing, authentication, databases, and internal applications.

## Design Considerations

- Use separate VLANs and appropriate firewall rules to isolate employee, server, and guest traffic where supported.
- Restrict administrative access to authorized personnel.
- Keep network devices and servers updated.
- Back up important data and monitor network activity.

**Note:** This is a logical diagram, not a physical installation plan. The actual layout and number of switches or access points should be chosen according to device counts, port requirements, coverage, and future growth.