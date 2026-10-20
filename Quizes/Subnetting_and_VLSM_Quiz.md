# CCNA Practice Quiz: IPv4 Subnetting & VLSM (30 Questions)

Welcome to the **CCNA IPv4 Subnetting and Variable Length Subnet Masking (VLSM)** practice quiz. This quiz is structured into three progressive difficulty tiers:

1. **Part 1: Basic Subnetting Fundamentals (Questions 1–10)**
2. **Part 2: Intermediate Subnet Math & Interface Configuration (Questions 11–20)**
3. **Part 3: Advanced CCNA Scenarios, VLSM Design & Troubleshooting (Questions 21–30)**

> **How to Use:**
> Read each question, choose your answer, and click **"View Answer & Explanation"** to verify your answer with a complete step-by-step breakdown.

---

## Part 1: Basic Subnetting Fundamentals (Questions 1–10)

### Question 1 [Basic]
What is the default subnet mask for a Class B IPv4 network?

- [ ] A) `255.0.0.0`
- [ ] B) `255.255.0.0`
- [ ] C) `255.255.255.0`
- [ ] D) `255.255.240.0`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) `255.255.0.0`**

**Explanation:**
- Class A default mask: `255.0.0.0` (`/8`) — First octet range: 1–126
- Class B default mask: `255.255.0.0` (`/16`) — First octet range: 128–191
- Class C default mask: `255.255.255.0` (`/24`) — First octet range: 192–223
</details>

---

### Question 2 [Basic]
What is the dotted decimal equivalent of the prefix length `/27`?

- [ ] A) `255.255.255.192`
- [ ] B) `255.255.255.224`
- [ ] C) `255.255.255.240`
- [ ] D) `255.255.255.248`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) `255.255.255.224`**

**Explanation:**
A `/27` mask has 27 contiguous binary 1s:
- Octet 1: `11111111` = 255
- Octet 2: `11111111` = 255
- Octet 3: `11111111` = 255
- Octet 4: `11100000` = $128 + 64 + 32 = 224$
Thus, the mask is `255.255.255.224`.
</details>

---

### Question 3 [Basic]
How many usable host IP addresses are available on a `/28` subnet?

- [ ] A) 14
- [ ] B) 16
- [ ] C) 30
- [ ] D) 6

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **A) 14**

**Explanation:**
1. A standard IPv4 address has 32 bits.
2. Host bits ($h$) = $32 - 28 = 4$ bits.
3. Total IP addresses = $2^h = 2^4 = 16$.
4. Usable host addresses = $2^h - 2 = 16 - 2 = 14$ (subtracting 2 for the Network ID and the Broadcast address).
</details>

---

### Question 4 [Basic]
Given the IP address `192.168.10.130/25`, what is the network address and directed broadcast address for this subnet?

- [ ] A) Network: `192.168.10.0`, Broadcast: `192.168.10.127`
- [ ] B) Network: `192.168.10.128`, Broadcast: `192.168.10.255`
- [ ] C) Network: `192.168.10.128`, Broadcast: `192.168.10.191`
- [ ] D) Network: `192.168.10.64`, Broadcast: `192.168.10.191`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) Network: `192.168.10.128`, Broadcast: `192.168.10.255`**

**Explanation:**
1. `/25` has a block size (magic number) in the 4th octet: $256 - 128 = 128$.
2. Subnets increment by 128:
   - Subnet 1: `192.168.10.0/25` (Valid hosts: `.1` – `.126`, Broadcast: `.127`)
   - Subnet 2: `192.168.10.128/25` (Valid hosts: `.129` – `.254`, Broadcast: `.255`)
3. The IP `192.168.10.130` falls into the second subnet:
   - **Network ID:** `192.168.10.128`
   - **Broadcast ID:** `192.168.10.255`
</details>

---

### Question 5 [Basic]
Which of the following IP addresses can be legally assigned to a host device?

- [ ] A) `10.1.1.32/27`
- [ ] B) `192.168.5.127/26`
- [ ] C) `172.16.8.0/23`
- [ ] D) `172.16.9.0/23`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **D) `172.16.9.0/23`**

**Explanation:**
- **A) `10.1.1.32/27`:** Block size is 32 ($256 - 224$). Subnets are `.0`, `.32`, `.64`. `10.1.1.32` is a **Network Address**, not assignable to a host.
- **B) `192.168.5.127/26`:** Block size is 64. Subnet is `.64`, broadcast is `.127`. This is a **Broadcast Address**, not assignable to a host.
- **C) `172.16.8.0/23`:** In `/23`, the mask is `255.255.254.0` (block size in 3rd octet is 2). Subnets are `172.16.0.0`, `172.16.2.0`, ..., `172.16.8.0`. Thus, `172.16.8.0` is the **Network Address**.
- **D) `172.16.9.0/23`:** For subnet `172.16.8.0/23`, the valid host range is `172.16.8.1` through `172.16.9.254`. Therefore, `172.16.9.0` has host bits set to `00000001 00000000` (neither all 0s nor all 1s), making it a **valid, usable host address**!
</details>

---

### Question 6 [Basic]
If a `/24` network is divided into subnets using a `/28` mask, how many subnets are created, and how many usable hosts exist per subnet?

- [ ] A) 8 subnets, 30 usable hosts each
- [ ] B) 16 subnets, 14 usable hosts each
- [ ] C) 16 subnets, 16 usable hosts each
- [ ] D) 32 subnets, 6 usable hosts each

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) 16 subnets, 14 usable hosts each**

**Explanation:**
1. Subnet bits borrowed ($s$) = $28 - 24 = 4$ bits.
2. Number of subnets created = $2^s = 2^4 = 16$.
3. Remaining host bits ($h$) = $32 - 28 = 4$ bits.
4. Usable hosts per subnet = $2^h - 2 = 2^4 - 2 = 14$.
</details>

---

### Question 7 [Basic]
An administrator needs a subnet that can accommodate at least 30 usable host devices. What is the shortest prefix length (most host-conserving) that satisfies this requirement?

- [ ] A) `/26`
- [ ] B) `/27`
- [ ] C) `/28`
- [ ] D) `/29`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) `/27`**

**Explanation:**
1. Host formula: $2^h - 2 \ge 30$.
2. Testing values for $h$:
   - If $h = 4$: $2^4 - 2 = 14$ (Too small)
   - If $h = 5$: $2^5 - 2 = 30$ (Exact match!)
3. Prefix length = $32 - h = 32 - 5 = 27$ (`/27`).
</details>

---

### Question 8 [Basic]
Convert the subnet mask `255.255.240.0` into CIDR notation prefix length.

- [ ] A) `/18`
- [ ] B) `/19`
- [ ] C) `/20`
- [ ] D) `/21`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **C) `/20`**

**Explanation:**
- 1st octet: `255` = 8 bits
- 2nd octet: `255` = 8 bits
- 3rd octet: `240` = `11110000` = 4 bits
- 4th octet: `0` = 0 bits
Total 1s = $8 + 8 + 4 + 0 = 20$, which corresponds to `/20`.
</details>

---

### Question 9 [Basic]
What is the broadcast address for the subnet `172.20.16.0/20`?

- [ ] A) `172.20.16.255`
- [ ] B) `172.20.31.255`
- [ ] C) `172.20.32.255`
- [ ] D) `172.20.255.255`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) `172.20.31.255`**

**Explanation:**
1. Mask for `/20` is `255.255.240.0`.
2. The interesting octet is the 3rd octet ($240$).
3. Block size (magic number) = $256 - 240 = 16$.
4. The next subnet starts at $16 + 16 = 32$, which is `172.20.32.0`.
5. The broadcast address is one address below the next subnet: `172.20.31.255`.
</details>

---

### Question 10 [Basic]
Which of the following RFC 1918 private IPv4 address ranges is designated as Class A private space?

- [ ] A) `10.0.0.0` to `10.255.255.255` (`10.0.0.0/8`)
- [ ] B) `172.16.0.0` to `172.31.255.255` (`172.16.0.0/12`)
- [ ] C) `192.168.0.0` to `192.168.255.255` (`192.168.0.0/16`)
- [ ] D) `169.254.0.0` to `169.254.255.255` (`169.254.0.0/16`)

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **A) `10.0.0.0` to `10.255.255.255` (`10.0.0.0/8`)**

**Explanation:**
Per RFC 1918:
- Class A private: `10.0.0.0/8` (`10.0.0.0` – `10.255.255.255`)
- Class B private: `172.16.0.0/12` (`172.16.0.0` – `172.31.255.255`)
- Class C private: `192.168.0.0/16` (`192.168.0.0` – `192.168.255.255`)
*(Note: `169.254.0.0/16` is APIPA / Link-Local, RFC 3927).*
</details>

---

## Part 2: Intermediate Subnet Math & Practical Allocation (Questions 11–20)

### Question 11 [Intermediate]
A host is assigned IP `192.168.1.100` with subnet mask `255.255.255.248`. What is the valid host range for the subnet containing this host?

- [ ] A) `192.168.1.96` – `192.168.1.103`
- [ ] B) `192.168.1.97` – `192.168.1.102`
- [ ] C) `192.168.1.97` – `192.168.1.104`
- [ ] D) `192.168.1.96` – `192.168.1.102`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) `192.168.1.97` – `192.168.1.102`**

**Explanation:**
1. Mask `255.255.255.248` is a `/29`.
2. Block size in the 4th octet = $256 - 248 = 8$.
3. Multiples of 8 near 100:
   - $8 \times 12 = 96$
   - $8 \times 13 = 104$
4. Network Address: `192.168.1.96`
5. Broadcast Address: `192.168.1.103`
6. First usable host: `192.168.1.97`
7. Last usable host: `192.168.1.102`
</details>

---

### Question 12 [Intermediate]
What is the subnet network ID for the IP address `10.50.179.45/19`?

- [ ] A) `10.50.128.0`
- [ ] B) `10.50.160.0`
- [ ] C) `10.50.176.0`
- [ ] D) `10.50.192.0`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) `10.50.160.0`**

**Explanation:**
1. `/19` means:
   - Octet 1: 8 bits
   - Octet 2: 8 bits
   - Octet 3: 3 bits (`11100000` = 224)
   - Octet 4: 0 bits
   Mask = `255.255.224.0`.
2. Interesting octet: 3rd octet. Block size = $256 - 224 = 32$.
3. Multiples of 32 in 3rd octet:
   `0, 32, 64, 96, 128, 160, 192...`
4. The 3rd octet of the IP is 179, which falls between 160 and 192.
5. Therefore, the network address is `10.50.160.0/19`.
</details>

---

### Question 13 [Intermediate]
A network engineer attempts to configure a router interface with the command:
`Router(config-if)# ip address 192.168.1.191 255.255.255.224`
Why will the router return an error or reject this assignment?

- [ ] A) The IP is a private address and cannot be assigned to a routed interface.
- [ ] B) `192.168.1.191` is the directed broadcast address for that subnet.
- [ ] C) `192.168.1.191` is the subnet network address.
- [ ] D) The subnet mask `255.255.255.224` is not supported on Cisco IOS router interfaces.

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) `192.168.1.191` is the directed broadcast address for that subnet.**

**Explanation:**
1. Mask `255.255.255.224` (`/27`) has a block size of $256 - 224 = 32$.
2. Subnets:
   - `192.168.1.128` (Broadcast: `.159`)
   - `192.168.1.160` (Broadcast: `.191`)
   - `192.168.1.192` (Broadcast: `.223`)
3. `192.168.1.191` is the broadcast address of the `192.168.1.160/27` subnet.
4. Cisco IOS will display: `Bad mask /27 for address 192.168.1.191` because broadcast addresses cannot be assigned to interfaces.
</details>

---

### Question 14 [Intermediate]
What is the usable host range for the subnet `172.16.32.0/22`?

- [ ] A) `172.16.32.1` – `172.16.32.254`
- [ ] B) `172.16.32.1` – `172.16.33.254`
- [ ] C) `172.16.32.1` – `172.16.35.254`
- [ ] D) `172.16.32.1` – `172.16.63.254`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **C) `172.16.32.1` – `172.16.35.254`**

**Explanation:**
1. `/22` mask in binary has 22 ones: `255.255.252.0`.
2. Block size in the 3rd octet = $256 - 252 = 4$.
3. Subnet starts at `172.16.32.0`.
4. Next subnet starts at `32 + 4 = 36` $\implies$ `172.16.36.0`.
5. Broadcast address is `172.16.35.255`.
6. Usable host range is `172.16.32.1` through `172.16.35.254` (total of $2^{10} - 2 = 1022$ usable hosts).
</details>

---

### Question 15 [Intermediate]
A company needs to configure a VLAN that will host up to 500 employee workstations. Which subnet mask provides enough host addresses while wasting the fewest possible IPs?

- [ ] A) `255.255.254.0` (`/23`)
- [ ] B) `255.255.255.0` (`/24`)
- [ ] C) `255.255.252.0` (`/22`)
- [ ] D) `255.255.248.0` (`/21`)

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **A) `255.255.254.0` (`/23`)**

**Explanation:**
1. Host formula: $2^h - 2 \ge 500$.
2. Powers of 2:
   - $2^8 - 2 = 254$ (Insufficient for 500 hosts)
   - $2^9 - 2 = 510$ (Sufficient, wastes only 10 addresses!)
3. Host bits required = 9.
4. Prefix length = $32 - 9 = /23$.
5. Subnet mask = `255.255.254.0`.
</details>

---

### Question 16 [Intermediate]
PC-A (`192.168.10.65/26`) and PC-B (`192.168.10.130/26`) are connected to the same unmanaged switch. Can PC-A communicate directly with PC-B without a router or default gateway?

- [ ] A) Yes, because they share the same `/26` subnet mask and switch.
- [ ] B) Yes, because both IPs fall within the same Class C network.
- [ ] C) No, because PC-A and PC-B reside on different logical subnets.
- [ ] D) No, because unmanaged switches block broadcast frames between different hosts.

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **C) No, because PC-A and PC-B reside on different logical subnets.**

**Explanation:**
1. `/26` has a block size of 64:
   - Subnet 1: `192.168.10.0/26` (Hosts: `.1` – `.62`)
   - Subnet 2: `192.168.10.64/26` (Hosts: `.65` – `.126`) $\rightarrow$ PC-A
   - Subnet 3: `192.168.10.128/26` (Hosts: `.129` – `.190`) $\rightarrow$ PC-B
2. When PC-A performs an AND operation between PC-B's IP and its own subnet mask (`255.255.255.192`), it determines PC-B is on an external network (`192.168.10.128` $\neq$ `192.168.10.64`).
3. PC-A will attempt to send the packet to its default gateway rather than ARPing directly for PC-B's MAC address. Without a router, communication fails.
</details>

---

### Question 17 [Intermediate]
What is the wildcard mask used in Cisco IOS Access Control Lists (ACLs) to match all hosts in the subnet `192.168.50.192/28`?

- [ ] A) `0.0.0.15`
- [ ] B) `0.0.0.31`
- [ ] C) `0.0.0.240`
- [ ] D) `255.255.255.240`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **A) `0.0.0.15`**

**Explanation:**
1. The subnet mask for `/28` is `255.255.255.240`.
2. The wildcard mask is the bitwise inverse of the subnet mask:
   ```
     255.255.255.255
   - 255.255.255.240
   ------------------
       0.  0.  0. 15
   ```
3. Therefore, the wildcard mask is `0.0.0.15`.
</details>

---

### Question 18 [Intermediate]
How many point-to-point WAN links using `/30` subnets can be carved out of a single `192.168.100.0/27` block?

- [ ] A) 4
- [ ] B) 8
- [ ] C) 16
- [ ] D) 32

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) 8**

**Explanation:**
1. Starting prefix = `/27`. Target prefix = `/30`.
2. Bits borrowed for subnetting = $30 - 27 = 3$ bits.
3. Number of `/30` subnets = $2^3 = 8$.
4. Each `/30` provides 2 usable host addresses ($2^2 - 2 = 2$).
</details>

---

### Question 19 [Intermediate]
What is the last usable host IP in the subnet that contains the IP `10.10.10.10/13`?

- [ ] A) `10.10.255.254`
- [ ] B) `10.13.255.254`
- [ ] C) `10.15.255.254`
- [ ] D) `10.16.255.254`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **C) `10.15.255.254`**

**Explanation:**
1. Prefix `/13` mask:
   - Octet 1: `11111111` (255)
   - Octet 2: `11111000` (248)
   - Octets 3 & 4: `0.0`
   Mask = `255.248.0.0`.
2. Block size in 2nd octet = $256 - 248 = 8$.
3. Subnets in 2nd octet increment by 8: `10.0.0.0`, `10.8.0.0`, `10.16.0.0`.
4. Host `10.10.10.10` falls into subnet `10.8.0.0/13`.
5. Next subnet is `10.16.0.0`, so the broadcast address is `10.15.255.255`.
6. The last usable host is `10.15.255.254`.
</details>

---

### Question 20 [Intermediate]
Which statement best describes CIDR (Classless Inter-Domain Routing) compared to traditional classful routing?

- [ ] A) CIDR requires all subnets across an enterprise to use identical subnet masks.
- [ ] B) CIDR allows variable prefix lengths to be transmitted within routing updates, eliminating strict Class A, B, and C boundary restrictions.
- [ ] C) CIDR uses the first 3 bits of an address to mandate where the network boundary lies.
- [ ] D) CIDR was replaced by VLSM and is no longer used in IPv4 internet routing.

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) CIDR allows variable prefix lengths to be transmitted within routing updates, eliminating strict Class A, B, and C boundary restrictions.**

**Explanation:**
- Classful routing protocols (e.g., RIPv1, IGRP) do not send subnet masks in routing updates and assume default Class A, B, or C boundaries.
- CIDR (Classless Inter-Domain Routing, RFC 1519) includes the prefix length in routing updates, allowing arbitrary prefix boundaries, route summarization (supernetting), and VLSM.
</details>

---

## Part 3: Advanced CCNA Scenarios, VLSM Design & Troubleshooting (Questions 21–30)

### Question 21 [Advanced / CCNA Design]
You are assigned the network block `192.168.10.0/24`. Using VLSM, design subnets for the following departments in order to minimize address waste:
- **Sales LAN:** 60 hosts
- **Marketing LAN:** 28 hosts
- **Admin LAN:** 12 hosts
- **WAN Link 1:** 2 hosts
- **WAN Link 2:** 2 hosts

Which of the following represents the optimal subnet allocation?

- [ ] A)
  - Sales: `192.168.10.0/26`
  - Marketing: `192.168.10.64/27`
  - Admin: `192.168.10.96/28`
  - WAN 1: `192.168.10.112/30`
  - WAN 2: `192.168.10.116/30`
- [ ] B)
  - Sales: `192.168.10.0/26`
  - Marketing: `192.168.10.64/26`
  - Admin: `192.168.10.128/26`
  - WAN 1: `192.168.10.192/30`
  - WAN 2: `192.168.10.196/30`
- [ ] C)
  - Sales: `192.168.10.0/25`
  - Marketing: `192.168.10.128/27`
  - Admin: `192.168.10.160/28`
  - WAN 1: `192.168.10.176/30`
  - WAN 2: `192.168.10.180/30`
- [ ] D)
  - WAN 1: `192.168.10.0/30`
  - WAN 2: `192.168.10.4/30`
  - Admin: `192.168.10.8/28`
  - Marketing: `192.168.10.24/27`
  - Sales: `192.168.10.56/26`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **A) Sales: `192.168.10.0/26`, Marketing: `192.168.10.64/27`, Admin: `192.168.10.96/28`, WAN 1: `192.168.10.112/30`, WAN 2: `192.168.10.116/30`**

**Step-by-Step VLSM Calculation:**
Always allocate from largest host requirement to smallest:
1. **Sales (60 hosts):**
   - $2^6 - 2 = 62 \ge 60 \implies 6$ host bits $\implies /26$ (block size 64).
   - Subnet: `192.168.10.0/26` (Range: `.0` – `.63`).
2. **Marketing (28 hosts):**
   - $2^5 - 2 = 30 \ge 28 \implies 5$ host bits $\implies /27$ (block size 32).
   - Starts at `.64`: `192.168.10.64/27` (Range: `.64` – `.95`).
3. **Admin (12 hosts):**
   - $2^4 - 2 = 14 \ge 12 \implies 4$ host bits $\implies /28$ (block size 16).
   - Starts at `.96`: `192.168.10.96/28` (Range: `.96` – `.111`).
4. **WAN 1 (2 hosts):**
   - $2^2 - 2 = 2 \ge 2 \implies 2$ host bits $\implies /30$ (block size 4).
   - Starts at `.112`: `192.168.10.112/30` (Range: `.112` – `.115`).
5. **WAN 2 (2 hosts):**
   - Needs `/30` (block size 4).
   - Starts at `.116`: `192.168.10.116/30` (Range: `.116` – `.119`).
Next free IP is `192.168.10.120`, leaving `.120` through `.255` available for future growth.
</details>

---

### Question 22 [Advanced / Troubleshooting]
Review the four subnets planned for an enterprise network:
- Subnet A: `172.16.0.0/23`
- Subnet B: `172.16.2.0/24`
- Subnet C: `172.16.2.128/25`
- Subnet D: `172.16.4.0/22`

Which two subnets suffer from overlapping address space and cannot coexist?

- [ ] A) Subnet A and Subnet B
- [ ] B) Subnet B and Subnet C
- [ ] C) Subnet A and Subnet D
- [ ] D) Subnet C and Subnet D

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) Subnet B and Subnet C**

**Explanation:**
Let us determine the exact address space of each subnet:
- **Subnet A (`172.16.0.0/23`):** Spans `172.16.0.0` to `172.16.1.255`.
- **Subnet B (`172.16.2.0/24`):** Spans `172.16.2.0` to `172.16.2.255`.
- **Subnet C (`172.16.2.128/25`):** Spans `172.16.2.128` to `172.16.2.255`.
- **Subnet D (`172.16.4.0/22`):** Spans `172.16.4.0` to `172.16.7.255`.

Subnet C (`172.16.2.128` – `172.16.2.255`) resides entirely inside the range already allocated to Subnet B (`172.16.2.0` – `172.16.2.255`). Therefore, Subnet B and Subnet C overlap.
</details>

---

### Question 23 [Advanced / Standards]
Under **RFC 3021**, Cisco IOS allows configuring a `/31` subnet mask on point-to-point links. How many usable host IP addresses are provided by a `/31` prefix?

- [ ] A) 0 usable hosts
- [ ] B) 1 usable host
- [ ] C) 2 usable hosts
- [ ] D) 4 usable hosts

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **C) 2 usable hosts**

**Explanation:**
1. In standard subnets, 2 addresses are reserved ($2^h - 2$): the network address (all host bits 0) and the directed broadcast address (all host bits 1).
2. With a `/31` prefix, $h = 1$, giving $2^1 = 2$ total addresses.
3. RFC 3021 eliminates the requirement for directed broadcast and network address reservations on dedicated point-to-point links.
4. Both IP addresses (e.g., `10.0.0.0` and `10.0.0.1`) are valid and usable host endpoints on the link. This conserves 50% of the IP addresses compared to traditional `/30` subnets!
</details>

---

### Question 24 [Advanced / Route Summarization]
A core router needs to advertise a single summary route for the following four internal routes:
- `192.168.16.0/24`
- `192.168.17.0/24`
- `192.168.18.0/24`
- `192.168.19.0/24`

What is the most specific summary route (CIDR supernet) that encompasses all four networks without including unnecessary addresses?

- [ ] A) `192.168.16.0/21`
- [ ] B) `192.168.16.0/22`
- [ ] C) `192.168.16.0/23`
- [ ] D) `192.168.0.0/16`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) `192.168.16.0/22`**

**Step-by-Step Binary Summarization:**
Look at the 3rd octets in binary:
```
16 = 0 0 0 1 0 0 | 0 0
17 = 0 0 0 1 0 0 | 0 1
18 = 0 0 0 1 0 0 | 1 0
19 = 0 0 0 1 0 0 | 1 1
     ^^^^^^^^^^^
     6 matching bits
```
1. Octets 1 and 2 match completely: $8 + 8 = 16$ bits.
2. In Octet 3, the first 6 bits match (`000100`).
3. Total matching prefix length = $16 + 6 = /22$.
4. Mask = `255.255.252.0`.
5. Summary Network = `192.168.16.0/22`.
Range covered: `192.168.16.0` through `192.168.19.255`. It matches all 4 routes perfectly.
</details>

---

### Question 25 [Advanced / Route Summarization]
What is the optimal route summary for the subnets `10.1.4.0/24`, `10.1.5.0/24`, `10.1.6.0/24`, and `10.1.7.0/24`?

- [ ] A) `10.1.4.0/21`
- [ ] B) `10.1.4.0/22`
- [ ] C) `10.1.0.0/22`
- [ ] D) `10.1.4.0/23`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) `10.1.4.0/22`**

**Explanation:**
1. Octets 1 and 2 are identical (`10.1.` = 16 bits).
2. Examine the 3rd octet in binary:
   - $4 =$ `00000100`
   - $5 =$ `00000101`
   - $6 =$ `00000110`
   - $7 =$ `00000111`
3. Notice that the first 6 bits (`000001`) are identical across all 4 numbers.
4. Total bits in common = $8 + 8 + 6 = 22$ bits.
5. Base network address = `10.1.4.0`.
6. Therefore, the optimal summary route is `10.1.4.0/22`.
</details>

---

### Question 26 [Advanced / VLSM Design Calculation]
An organization is allocated `10.100.0.0/20`. They must establish:
- 8 branch subnets, each requiring at least **200 usable host addresses**.
- 16 WAN links, each requiring **2 usable host addresses**.

After satisfying these requirements using optimal VLSM sizing, what is the maximum number of `/24` subnets that can still be created from the remaining unallocated address space?

- [ ] A) 4
- [ ] B) 6
- [ ] C) 7
- [ ] D) 8

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **C) 7**

**Step-by-Step Allocation Analysis:**
1. **Total Space in Parent Block:**
   - `10.100.0.0/20` spans `10.100.0.0` to `10.100.15.255`.
   - A `/20` contains $2^{24 - 20} = 16$ individual `/24` equivalents (4,096 total IP addresses).
2. **Branch Subnet Allocation:**
   - 200 hosts require $2^h - 2 \ge 200 \implies h = 8 \implies /24$ (254 usable hosts).
   - 8 branch subnets $\times$ `/24` = exactly 8 blocks of `/24` (consumed: `10.100.0.0/24` through `10.100.7.255`).
3. **WAN Link Allocation:**
   - 16 WAN links $\times$ `/30` (4 addresses each) = 64 total IP addresses.
   - 64 addresses = a single `/26` block (e.g., `10.100.8.0/26`).
4. **Remaining Space:**
   - `/24` block `10.100.8.0/24` has had only 64 addresses used, leaving 192 addresses (not a full `/24`).
   - The remaining full `/24` blocks are:
     `10.100.9.0/24`, `10.100.10.0/24`, `10.100.11.0/24`, `10.100.12.0/24`, `10.100.13.0/24`, `10.100.14.0/24`, `10.100.15.0/24`.
   - Count of whole, contiguous `/24` subnets remaining = **7**.
</details>

---

### Question 27 [Advanced / Troubleshooting Interface Overlap]
Router `R1` has interface `GigabitEthernet0/0` configured with IP `10.1.20.1 255.255.252.0`. A junior network engineer enters the following commands for `GigabitEthernet0/1`:

```
R1(config)# interface GigabitEthernet0/1
R1(config-if)# ip address 10.1.23.254 255.255.255.0
```

What will be the result in Cisco IOS?

- [ ] A) The command succeeds and both interfaces operate normally.
- [ ] B) The router issues a warning but automatically routes between them using proxy ARP.
- [ ] C) The command is rejected with `% 10.1.23.0 overlaps with GigabitEthernet0/0`.
- [ ] D) The router shuts down `GigabitEthernet0/0` to prevent an IP loop.

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **C) The command is rejected with `% 10.1.23.0 overlaps with GigabitEthernet0/0`.**

**Explanation:**
1. The mask for `Gi0/0` is `255.255.252.0` (`/22`).
2. Block size in the 3rd octet = $256 - 252 = 4$.
3. The subnet for `Gi0/0` is `10.1.20.0/22`:
   - Subnet starts at: `10.1.20.0`
   - Broadcast address: `10.1.23.255`
   - Address range: `10.1.20.0` through `10.1.23.255`
4. The engineer is attempting to configure `Gi0/1` in `10.1.23.0/24` (`10.1.23.0` – `10.1.23.255`), which falls completely inside the range of `Gi0/0`.
5. Cisco IOS prevents routing ambiguity by rejecting the command with an overlap error message.
</details>

---

### Question 28 [Advanced / Wildcard Masking]
A network engineer wants to configure an ACL statement to match all **even-numbered** Class C subnets in the range `192.168.0.0` through `192.168.254.0` (i.e., `192.168.0.0/24`, `192.168.2.0/24`, `192.168.4.0/24`, ..., `192.168.254.0/24`).

Which single IP address and wildcard mask combination achieves this?

- [ ] A) `192.168.0.0 0.0.254.255`
- [ ] B) `192.168.0.0 0.0.255.255`
- [ ] C) `192.168.0.0 0.0.1.255`
- [ ] D) `192.168.1.0 0.0.254.255`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **A) `192.168.0.0 0.0.254.255`**

**Explanation:**
1. In a wildcard mask:
   - A bit `0` means **must match exactly**.
   - A bit `1` means **ignore / don't care**.
2. Any even number has a least significant bit (LSB) of `0` in binary.
3. For the 3rd octet:
   - We want the lowest bit to be strictly `0` (matching the `0` in `192.168.0.0`).
   - The other 7 higher bits can be anything (`11111110` in binary = 254).
4. Therefore, the 3rd octet wildcard mask is `254` (`11111110`).
5. Combined wildcard mask: `0.0.254.255`.
This matches every address where the 3rd octet is even!
</details>

---

### Question 29 [Advanced / WAN Design]
A hub router connects to four remote branch routers over point-to-point serial interfaces using `/30` subnets.
What is the smallest single contiguous subnet block that can be allocated from the parent network to provide addressing for all four links?

- [ ] A) `/27`
- [ ] B) `/28`
- [ ] C) `/29`
- [ ] D) `/30`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) `/28`**

**Explanation:**
1. Each point-to-point link configured with a `/30` mask uses 4 IP addresses (1 network, 2 usable hosts, 1 broadcast).
2. For 4 links: $4 \times 4 = 16$ total IP addresses required.
3. An IP block of size 16 corresponds to host bits $h$:
   $2^h = 16 \implies h = 4$.
4. Prefix length = $32 - 4 = /28$.
5. A `/28` block precisely yields $2^{30 - 28} = 4$ subnets of `/30` with zero address waste.
</details>

---

### Question 30 [Advanced / VLSM Topology Architecture]
An enterprise network architect is designing the IP scheme for corporate headquarters using the private prefix `172.25.0.0/16`. The requirements are:
- **Engineering:** 1,000 hosts
- **Research & Development:** 500 hosts
- **Operations:** 250 hosts
- **DMZ:** 50 hosts
- **3 WAN Point-to-Point Links:** 2 hosts each

To avoid route fragmentation and overlapping, subnets are assigned strictly from largest to smallest. What is the correct prefix length assigned to the **DMZ** network, and what is the next available subnet address immediately following the third WAN link?

- [ ] A) DMZ: `/25`; Next available address: `172.25.7.12`
- [ ] B) DMZ: `/26`; Next available address: `172.25.7.76`
- [ ] C) DMZ: `/26`; Next available address: `172.25.7.12`
- [ ] D) DMZ: `/27`; Next available address: `172.25.8.0`

<details>
<summary><b>View Answer & Explanation</b></summary>

**Correct Answer:** **B) DMZ: `/26`; Next available address: `172.25.7.76`**

**Comprehensive Step-by-Step Architecture Walkthrough:**

1. **Engineering (1,000 hosts):**
   - $2^{10} - 2 = 1022 \ge 1000 \implies /22$ (block size 4 in 3rd octet).
   - **Subnet:** `172.25.0.0/22` (Range: `172.25.0.0` – `172.25.3.255`).

2. **Research & Development (500 hosts):**
   - $2^9 - 2 = 510 \ge 500 \implies /23$ (block size 2 in 3rd octet).
   - Starts at `172.25.4.0`:
   - **Subnet:** `172.25.4.0/23` (Range: `172.25.4.0` – `172.25.5.255`).

3. **Operations (250 hosts):**
   - $2^8 - 2 = 254 \ge 250 \implies /24$ (block size 1 in 3rd octet).
   - Starts at `172.25.6.0`:
   - **Subnet:** `172.25.6.0/24` (Range: `172.25.6.0` – `172.25.6.255`).

4. **DMZ (50 hosts):**
   - $2^6 - 2 = 62 \ge 50 \implies /26$ (block size 64 in 4th octet).
   - Starts at `172.25.7.0`:
   - **Subnet:** `172.25.7.0/26` (Range: `172.25.7.0` – `172.25.7.63`).
   - Thus, DMZ prefix is **`/26`**.

5. **WAN Links (2 hosts each):**
   - Each requires `/30` (block size 4).
   - **WAN Link 1:** `172.25.7.64/30` (`172.25.7.64` – `.67`)
   - **WAN Link 2:** `172.25.7.68/30` (`172.25.7.68` – `.71`)
   - **WAN Link 3:** `172.25.7.72/30` (`172.25.7.72` – `.75`)

6. **Next Available Address:**
   - Immediately following `172.25.7.75` is **`172.25.7.76`**.
</details>

---

## Quick Reference Summary Table

| Prefix | Subnet Mask | Usable Hosts | Magic Number (Block Size) | Common Use Case |
|---|---|---|---|---|
| `/24` | `255.255.255.0` | 254 | 1 (in octet 3) / 256 | Standard LAN |
| `/25` | `255.255.255.128` | 126 | 128 | Medium-Large Department |
| `/26` | `255.255.255.192` | 62 | 64 | Medium Office / VLAN |
| `/27` | `255.255.255.224` | 30 | 32 | Small Branch / Server segment |
| `/28` | `255.255.255.240` | 14 | 16 | Small Office / Management VLAN |
| `/29` | `255.255.255.248` | 6 | 8 | ISP / Multi-device gateway segment |
| `/30` | `255.255.255.252` | 2 | 4 | Traditional Point-to-Point WAN Link |
| `/31` | `255.255.255.254` | 2 | 2 | RFC 3021 Point-to-Point Link |
| `/32` | `255.255.255.255` | 1 | 1 | Loopback Interface / Host Route |
