# Section D — Subnetting & Calculations

## Q10. Basic Subnet Calculation (10 Marks)

**Given:** `192.168.10.0/26`

We need to calculate the subnet mask, number of `/26` subnets obtainable from a `/24` network, usable hosts per subnet, network address, first usable address, last usable address, and broadcast address.

### 1. Subnet Mask

A `/26` prefix means that 26 bits are used for the network portion and the remaining bits are used for host addressing.

\[
\text{Host bits}=32-26=6
\]

The subnet mask in binary is:

`11111111.11111111.11111111.11000000`

Converting it to decimal gives:

**Subnet mask: `255.255.255.192`**

### 2. Number of `/26` Subnets from a `/24`

The original network has a `/24` prefix, and the new subnet prefix is `/26`.

\[
\text{Borrowed bits}=26-24=2
\]

The number of resulting subnets is:

\[
2^2=4
\]

**Number of `/26` subnets: 4**

### 3. Usable Hosts per Subnet

The number of host bits is:

\[
32-26=6
\]

Total addresses per subnet:

\[
2^6=64
\]

For a conventional IPv4 subnet, subtract the network and broadcast addresses:

\[
\text{Usable hosts}=2^6-2=62
\]

**Usable hosts per subnet: 62**

### 4. Block Size and Subnet Ranges

The block size in the fourth octet is:

\[
256-192=64
\]

Therefore, the four `/26` subnets within `192.168.10.0/24` begin at fourth-octet values 0, 64, 128, and 192.

| Subnet | Network Address | First Usable | Last Usable | Broadcast |
|---|---|---|---|---|
| 1 | `192.168.10.0/26` | `192.168.10.1` | `192.168.10.62` | `192.168.10.63` |
| 2 | `192.168.10.64/26` | `192.168.10.65` | `192.168.10.126` | `192.168.10.127` |
| 3 | `192.168.10.128/26` | `192.168.10.129` | `192.168.10.190` | `192.168.10.191` |
| 4 | `192.168.10.192/26` | `192.168.10.193` | `192.168.10.254` | `192.168.10.255` |

### 5. Details of the Given Subnet

The given address is `192.168.10.0/26`, which is the first subnet listed above.

- **Network address:** `192.168.10.0`
- **Subnet mask:** `255.255.255.192`
- **First usable address:** `192.168.10.1`
- **Last usable address:** `192.168.10.62`
- **Broadcast address:** `192.168.10.63`
- **Total addresses:** 64
- **Usable host addresses:** 62

### Conclusion

A `/26` prefix uses the subnet mask `255.255.255.192`, provides 62 usable host addresses per conventional subnet, and divides a `/24` network into four equal `/26` subnets.



## Q11. Subnetting Design (15 Marks)

**Given network:** `192.168.10.0/24`

The organization requires separate subnets for IT (50 hosts), HR (30 hosts), Finance (20 hosts), and Management (10 hosts).

### 1. Choosing the Subnet Sizes

Variable Length Subnet Masking (VLSM) allows subnets of different sizes to be allocated according to the number of hosts required.

For each department, we need enough host bits to provide the required number of usable addresses.

The formula for usable hosts in a conventional IPv4 subnet is:

\[
\text{Usable hosts}=2^h-2
\]

where \(h\) is the number of host bits.

| Department | Required Hosts | Host Bits Needed | Prefix | Total Addresses | Usable Hosts |
|---|---:|---:|---|---:|---:|
| IT | 50 | 6 | `/26` | 64 | 62 |
| HR | 30 | 5 | `/27` | 32 | 30 |
| Finance | 20 | 5 | `/27` | 32 | 30 |
| Management | 10 | 4 | `/28` | 16 | 14 |

**Reasoning:**

- IT needs at least 50 usable addresses. With 6 host bits, \(2^6-2=62\), so it requires `/26`.
- HR needs 30 usable addresses. With 5 host bits, \(2^5-2=30\), so it requires `/27`.
- Finance needs 20 usable addresses. A `/27` provides 30 usable addresses, so it fits.
- Management needs 10 usable addresses. With 4 host bits, \(2^4-2=14\), so it requires `/28`.

### 2. Allocating the Subnets

Starting from `192.168.10.0/24`, assign the largest subnet first and then use the next correctly aligned available network address for each smaller subnet.

**Allocation order:** IT → HR → Finance → Management.

| Department | Network Address / CIDR | Subnet Mask | Usable Host Range | Broadcast Address | Usable Host Count |
|---|---|---|---|---|---:|
| IT | `192.168.10.0/26` | `255.255.255.192` | `192.168.10.1 – 192.168.10.62` | `192.168.10.63` | 62 |
| HR | `192.168.10.64/27` | `255.255.255.224` | `192.168.10.65 – 192.168.10.94` | `192.168.10.95` | 30 |
| Finance | `192.168.10.96/27` | `255.255.255.224` | `192.168.10.97 – 192.168.10.126` | `192.168.10.127` | 30 |
| Management | `192.168.10.128/28` | `255.255.255.240` | `192.168.10.129 – 192.168.10.142` | `192.168.10.143` | 14 |

### 3. Verification of the Allocation

The subnet blocks are:

- IT: `.0` through `.63` — 64 total addresses.
- HR: `.64` through `.95` — 32 total addresses.
- Finance: `.96` through `.127` — 32 total addresses.
- Management: `.128` through `.143` — 16 total addresses.

Each subnet begins at a valid network boundary, and none of the allocated ranges overlap.

The total number of addresses allocated is:

\[
64+32+32+16=144
\]

The original `/24` network contains:

\[
2^8=256 \text{ total addresses}
\]

Therefore, the remaining unallocated address range is:

`192.168.10.144` through `192.168.10.255`

This remaining space can support future growth or additional subnets, provided they are allocated without overlapping existing ranges.

### Conclusion

VLSM provides a suitable subnet for each department according to its host requirement. IT receives a `/26`, HR and Finance each receive a `/27`, and Management receives a `/28`. All four subnets fit within `192.168.10.0/24` without overlap, and address space remains available for future use.