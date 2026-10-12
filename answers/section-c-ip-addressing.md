# Section C — IP Addressing

## Q7. IPv4 & IPv6 (5 Marks)

### 1. What Is an IP Address?

An Internet Protocol (IP) address is a logical address used to identify a network interface and help deliver data packets across IP networks. IPv4 and IPv6 are two versions of the Internet Protocol.

### 2. Difference Between IPv4 and IPv6

| Feature | IPv4 | IPv6 |
|---|---|---|
| Address length | 32 bits | 128 bits |
| Address format | Four decimal numbers separated by dots | Eight groups of hexadecimal digits separated by colons |
| Example | `192.168.1.10` | `2001:db8::1` |
| Address capacity | About 4.3 billion possible addresses | \(2^{128}\) possible addresses |
| Address notation | Dotted-decimal notation | Colon-separated hexadecimal notation |
| Address configuration | Can be configured manually or automatically, such as through DHCP | Supports manual and automatic configuration, including SLAAC and DHCPv6 |
| NAT usage | Commonly used in IPv4 networks to conserve public IPv4 addresses | Generally reduces the need for address-conservation NAT because of its very large address space |

### 3. Why Was IPv6 Introduced?

IPv6 was introduced primarily because the supply of available IPv4 addresses was becoming insufficient for the growing number of internet-connected devices.

IPv6 provides a much larger address space with 128-bit addresses compared with IPv4's 32-bit addresses. It also supports features such as stateless address autoconfiguration (SLAAC), efficient address allocation, and standardized support for IP-layer security through IPsec.

IPv6 helps support the continued growth of the internet, including smartphones, computers, servers, and Internet of Things (IoT) devices.

### 4. Address Examples

- **IPv4:** `192.168.1.10` — a private IPv4 address commonly used in a local network.
- **IPv6:** `2001:db8::1` — an example address from the IPv6 documentation prefix reserved for illustrative use.

### Conclusion

IPv4 uses 32-bit addresses, while IPv6 uses 128-bit addresses. IPv6 was introduced mainly to overcome IPv4 address-space limitations and support the continued growth of internet-connected devices.



## Q8. IP Classification (5 Marks)

IPv4 addresses were traditionally divided into five classes (A, B, C, D, and E) based on the value of the first octet. Classes A, B, and C were used for ordinary unicast addressing, while Class D is used for multicast and Class E is reserved for experimental purposes.

Private IPv4 addresses are defined by specific address ranges. Addresses outside these private ranges are not automatically guaranteed to be publicly routable, but the addresses in this question can be classified as follows.

### Classification of the Given IP Addresses

| IP Address | First Octet | Traditional Class | Private/Public Status | Reason |
|---|---:|---|---|---|
| `10.10.10.5` | 10 | Class A | Private | The `10.0.0.0/8` range is reserved for private networks. |
| `172.16.5.20` | 172 | Class B | Private | The `172.16.0.0/12` private range covers `172.16.0.0` through `172.31.255.255`. |
| `192.168.1.50` | 192 | Class C | Private | The `192.168.0.0/16` range is reserved for private networks. |
| `8.8.8.8` | 8 | Class A | Public | It is outside the private IPv4 ranges and is used as a publicly reachable Google Public DNS address. |

### Traditional IPv4 Class Ranges

| Class | First-Octet Range | Traditional Purpose |
|---|---|---|
| A | 1–126 | Large unicast networks |
| B | 128–191 | Medium-sized unicast networks |
| C | 192–223 | Small unicast networks |
| D | 224–239 | Multicast |
| E | 240–255 | Reserved/experimental |

**Note:** `127.0.0.0/8` is reserved for loopback, and `0.0.0.0/8` has special purposes. Therefore, the traditional Class A range is often described as first-octet values 1–126 for ordinary classful networks.

### Conclusion

The addresses `10.10.10.5`, `172.16.5.20`, and `192.168.1.50` are private IPv4 addresses. The address `8.8.8.8` is public. Their traditional classes are determined by the first octet, independently of their private or public status.



## Q9. IP Components (10 Marks)

**Given:**

- IP address: `192.168.20.45`
- CIDR prefix: `/24`

We need to calculate the network address, host portion, subnet mask, broadcast address, and usable host range.

### 1. Subnet Mask

A `/24` prefix means that the first 24 bits are used for the network portion, leaving 8 bits for the host portion.

An IPv4 address contains 32 bits.

\[
\text{Host bits}=32-24=8
\]

The subnet mask has 24 network bits set to 1 and 8 host bits set to 0.

In binary:

`11111111.11111111.11111111.00000000`

Converting each octet to decimal gives:

**Subnet mask: `255.255.255.0`**

### 2. Network Address

The network address is obtained by performing a bitwise AND operation between the IP address and its subnet mask.

| Component | IP Address | Subnet Mask |
|---|---|---|
| First octet | 192 | 255 |
| Second octet | 168 | 255 |
| Third octet | 20 | 255 |
| Fourth octet | 45 | 0 |

The first three octets remain unchanged because their mask values are 255. The fourth octet becomes 0 because its mask value is 0.

Therefore:

**Network address: `192.168.20.0`**

### 3. Host Portion

The host portion is represented by the last 8 bits because the prefix is `/24`.

The last octet of the given address is 45.

In binary:

`45 = 00101101`

Therefore, the host portion has the value 45.

**Host portion: `0.0.0.45`**, or simply **host ID `45`** within network `192.168.20.0/24`.

### 4. Broadcast Address

The broadcast address is obtained by setting all host bits to 1.

The first three octets remain `192.168.20`, and the final octet becomes 255.

Therefore:

**Broadcast address: `192.168.20.255`**

### 5. Usable Host Range

A `/24` network contains 8 host bits.

The total number of addresses is:

\[
2^8=256
\]

In a conventional IPv4 `/24` subnet, the network address and broadcast address are not assigned to ordinary hosts.

\[
\text{Usable hosts}=2^8-2=254
\]

The first usable address is one greater than the network address, and the last usable address is one less than the broadcast address.

- **First usable address:** `192.168.20.1`
- **Last usable address:** `192.168.20.254`
- **Usable host count:** 254

### Final Answer Summary

| Required Component | Answer |
|---|---|
| Given IP address | `192.168.20.45/24` |
| Subnet mask | `255.255.255.0` |
| Network address | `192.168.20.0` |
| Host portion | `45` (last octet) |
| Broadcast address | `192.168.20.255` |
| First usable host | `192.168.20.1` |
| Last usable host | `192.168.20.254` |
| Total addresses | 256 |
| Usable host addresses | 254 |

### Conclusion

For `192.168.20.45/24`, the network address is `192.168.20.0`, the broadcast address is `192.168.20.255`, and the usable host range is `192.168.20.1` to `192.168.20.254`. The subnet mask is `255.255.255.0`.