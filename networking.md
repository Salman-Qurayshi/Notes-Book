# Networking

### Overview

### **1. Public and Private IP Addresses**

- **Public IP Address**: A globally unique IP assigned by an ISP, visible on the internet.
- **Private IP Address**: Used within a local network, not visible on the public internet. Common ranges include:
    - **192.168.x.x**
    - **10.x.x.x**
    - **172.16.x.x - 172.31.x.x**
- **Purpose**: Allows multiple devices within a local network to connect to the internet using a single public IP.

---

### **2. Network Address Translation (NAT)**

- **NAT**: Translates private IP addresses to a public IP address for internet communication.
    - **How It Works**: Converts private IP addresses (e.g., **192.168.1.4**) to the router’s public IP (e.g., **203.0.113.45**) when accessing the internet. Uses port numbers to track which device made the request.
    - **Port Numbers**: Unique identifiers used to manage multiple devices behind the same public IP.

---

### **3. CIDR (Classless Inter-Domain Routing)**

- **CIDR Notation**: Describes IP addresses and their network masks more flexibly than the old classful system.
    - **Example**: **192.168.1.0/24**
        - **/24** indicates that the first 24 bits are used for the network part, and the remaining 8 bits are for the host part.
        - **Benefits**: Efficient IP allocation, reduces waste, and provides flexibility for network sizing.
- **Why CIDR Is Used**: Replaces old classful addressing, which had fixed sizes (Class A, B, C) and often wasted IP addresses. CIDR allows for more precise network sizes.
    - **CIDR Example**: **192.168.1.0/24** gives 256 possible IP addresses (192.168.1.0 to 192.168.1.255), with 254 usable for hosts after reserving addresses for the network and broadcast.

---

### **Understanding the IP Address:**

- **192.168.1.4** is your full IP address in "dotted decimal" form.
- **/24** is the CIDR notation that tells us how many bits are used for the **network part**.

### **Converting the IP to Binary:**

IP addresses are made up of 32 bits, split into 4 "octets" (sets of 8 bits). Let’s convert your IP address **192.168.1.4** to its binary form:

| Decimal | 192 | 168 | 1 | 4 |
| --- | --- | --- | --- | --- |
| Binary | 11000000 | 10101000 | 00000001 | 00000100 |

So, your IP address **192.168.1.4** in binary is:
**11000000.10101000.00000001.00000100**

### **What the "/24" Means:**

- **/24** tells us that the first 24 bits are for the **network** part.
- The remaining **8 bits** (32 total - 24 for the network = 8 bits) are for the **host** part.

Here’s how the bits are divided:

- Network part: **11000000.10101000.00000001** (**192.168.1**)
- Host part: **00000100** (**4** in decimal)

### **Identifying the Network and Host:**

- **Network part (192.168.1.0):**
The first 24 bits (192.168.1) are the **network address**. This identifies the specific network your device belongs to. All devices on this network will have the same first 24 bits, meaning their IP addresses will start with **192.168.1**.
- **Host part (4):**
The last 8 bits (00000100) are for the **host**, or specific device. This means your device is assigned number **4** on the network.

### **Range of IP Addresses on Your Network:**

Because you’re using **/24** (which leaves 8 bits for hosts), the total number of available IP addresses for hosts in your network is 28=256 2^8 = 256 28=256. However, not all are usable for devices.

- **Network address (192.168.1.0):** This is reserved to represent the whole network.
- **Broadcast address (192.168.1.255):** This is reserved for sending messages to all devices on the network.

This leaves **254 usable IP addresses**, from **192.168.1.1** to **192.168.1.254**.

### **Recap Using Your IP (192.168.1.4/24):**

- **192.168.1** is the **network** your device is part of (like the street name in an address).
- **4** is your **host** ID (like your house number on that street).
- Your network can have up to **254 devices**, and your device is the **4th** one.

---

### **4. IP Address Structure**

- **IPv4 Address**: 32 bits divided into 4 octets.
    - **Decimal Example**: **192.168.1.4**
    - **Binary Conversion**:
        - 192 = 11000000
        - 168 = 10101000
        - 1 = 00000001
        - 4 = 00000100
        - **Full Binary**: 11000000.10101000.00000001.00000100
- **Network and Host Parts**:
    - **Network Part**: Identified by CIDR (e.g., **192.168.1** in **192.168.1.4/24**). Determines the specific network.
    - **Host Part**: Identifies the specific device within the network (e.g., **4** in **192.168.1.4**).

---

### **5. Range of IP Addresses in a Network**

- **CIDR Notation Impact**:
    - **/24** provides a block of 256 IP addresses.
    - **Network Address**: **192.168.1.0** (represents the entire network).
    - **Broadcast Address**: **192.168.1.255** (used for sending messages to all devices in the network).
    - **Usable IP Addresses**: From **192.168.1.1** to **192.168.1.254** (254 addresses).

---

### **6. Understanding Network Addressing**

- **Network Address**: The part of the IP that specifies the network segment (e.g., **192.168.1**).
- **Host Address**: The part of the IP that specifies the individual device within the network (e.g., **4** in **192.168.1.4**).
- **Why This Matters**:
    - **Network Part**: Helps routers and switches identify the correct network.
    - **Host Part**: Directs data to the specific device within the network.

---

### **7. Multiple Networks and Public IP Sharing**

- **Multiple Networks**: Devices on different private networks (e.g., **192.168.1.x** and **192.168.2.x**) can share the same public IP because private IPs are used internally and do not conflict across different networks.
- **Public IPs**: Each house or network has a unique public IP assigned by the ISP. Private IPs can be reused across different networks.

---

### **8. Internet Service Provider (ISP) Role**

- **Public IP Assignment**: ISPs assign a unique public IP to each customer (house or business) that connects to the internet.
- **Private Networks**: ISPs do not manage private IP addresses. The router within each home assigns private IPs.

---

These notes should now cover a

### Decimal to Binary Conversion ( one of the methods )

### **Example 1: Decimal 13**

| **128** | **64** | **32** | **16** | **8** | **4** | **2** | **1** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **0** | **0** | **0** | **0** | **1** | **1** | **0** | **1** |

**Decimal Calculation:**

0 + 0 + 0 + 0 + 8 + 4 + 0 + 1 = 13

**Binary Representation:** **00001101** (Including leading zeros for clarity)

**Simplified Binary Representation:** **10101**

---

### **Example 2: Decimal 45**

| **128** | **64** | **32** | **16** | **8** | **4** | **2** | **1** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **0** | **0** | **1** | **0** | **1** | **1** | **0** | **1** |

**Decimal Calculation:**

32 + 8 + 4 + 1 = 45

**Binary Representation:** **00101101** (Including leading zeros for clarity)

**Simplified Binary Representation:** **101101**

---

### **Example 3: Decimal 1024**

| **1024** | **512** | **256** | **128** | **64** | **32** | **16** | **8** | **4** | **2** | **1** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **1** | **0** | **0** | **0** | **0** | **0** | **0** | **0** | **0** | **0** | **0** |

**Decimal Calculation:**

1024 = 1024

**Binary Representation:** **10000000000** (Including leading zeros for clarity)

**Simplified Binary Representation:** **10000000000**

---

### **Example 4: Decimal 1025**

| **1024** | **512** | **256** | **128** | **64** | **32** | **16** | **8** | **4** | **2** | **1** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **1** | **0** | **0** | **0** | **0** | **0** | **0** | **0** | **0** | **0** | **1** |

**Decimal Calculation:**

1024 + 1 = 1025

**Binary Representation:** **10000000001** (Including leading zeros for clarity)

**Simplified Binary Representation:** **10000000001**

---

### **Example 5: Decimal 1026**

| **1024** | **512** | **256** | **128** | **64** | **32** | **16** | **8** | **4** | **2** | **1** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **1** | **0** | **0** | **0** | **0** | **0** | **0** | **0** | **1** | **0** | **0** |

**Decimal Calculation:**

1024 + 4 + 2 = 1026

**Binary Representation:** **10000000010** (Including leading zeros for clarity)

**Simplified Binary Representation:** **10000000010**

### To calculate the number of hosts in a network from its CIDR notation (like `/24`, `/16`, etc.), you can follow these steps:

### 1. **Understand CIDR Notation**:

CIDR (Classless Inter-Domain Routing) notation specifies how many bits of an IP address are reserved for the network portion and how many are left for the hosts.

- For example, in `192.168.1.0/24`:
    - `/24` means 24 bits are used for the network.
    - The remaining bits (32 - 24 = 8 bits) are available for host addresses.

### 2. **Formula to Calculate Hosts**:

To calculate the number of **usable hosts** in a network, use this formula:

```tsx
Number of hosts = 2^(number of bits for hosts) - 2
```

The `-2` accounts for:

- **1 IP** for the network address.
- **1 IP** for the broadcast address.

### 3. **Examples**:

### Example 1: `/24` Network

- **CIDR**: `/24` (e.g., `192.168.1.0/24`)
- **Network bits**: 24
- **Host bits**: `32 - 24 = 8 bits`

So, the number of hosts:

```makefile
Hosts = 2^8 - 2 = 256 - 2 = 254 usable hosts
```

- **Explanation**: With 8 bits for the hosts, we can have 254 usable IP addresses in this network, like `192.168.1.1` to `192.168.1.254`.

---

### Example 2: `/16` Network

- **CIDR**: `/16` (e.g., `192.168.0.0/16`)
- **Network bits**: 16
- **Host bits**: `32 - 16 = 16 bits`

So, the number of hosts:

```makefile
Hosts = 2^16 - 2 = 65536 - 2 = 65534 usable hosts
```

- **Explanation**: With 16 bits for the hosts, we can have 65,534 usable IP addresses in this network, like `192.168.0.1` to `192.168.255.254`.

---

### Example 3: `/30` Network

- **CIDR**: `/30` (e.g., `192.168.1.0/30`)
- **Network bits**: 30
- **Host bits**: `32 - 30 = 2 bits`

So, the number of hosts:

```makefile
Hosts = 2^2 - 2 = 4 - 2 = 2 usable hosts
```

- **Explanation**: With only 2 bits for hosts, you get only 2 usable IP addresses, typically used in point-to-point links like between routers.

---

### Quick Table of Common CIDR Ranges:

| **CIDR** | **Network Bits** | **Host Bits** | **Usable Hosts** |
| --- | --- | --- | --- |
| `/30` | 30 | 2 | 2 |
| `/29` | 29 | 3 | 6 |
| `/28` | 28 | 4 | 14 |
| `/24` | 24 | 8 | 254 |
| `/16` | 16 | 16 | 65,534 |
| `/8` | 8 | 24 | 16,777,214 |

---

### **Summary**:

- CIDR notation tells you how many bits are for the network and how many are left for hosts.
- Use the formula `2^(host bits) - 2` to calculate the number of usable hosts.
- The larger the host portion, the more addresses are available for devices in the network.

**why** we use the formula `2^(host bits)` to calculate the number of hosts in a network, and why we subtract 2. This will help you understand the logic behind it.

### 1. **IP Address Structure**:

IP addresses (IPv4) are 32 bits long, divided into two parts:

- **Network portion**: Identifies the network.
- **Host portion**: Identifies individual devices (hosts) on that network.

When we talk about CIDR notation like `/24`, the number after the slash (`/24`) tells us how many bits are reserved for the **network** portion. The remaining bits are available for the **hosts**.

- Example:
    - In `192.168.1.0/24`, the first 24 bits are for the network, and the remaining 8 bits (32 - 24 = 8) are for the hosts.

### 2. **Why `2^(host bits)`?**:

The number of **available addresses** depends on how many bits you have for the host portion.

Each **bit** can represent either a `0` or a `1`, which means **one bit** can have **2 possibilities** (`0` or `1`).

- If you have **1 bit** for hosts:
    - There are **2 possible combinations** (`0` or `1`).
- If you have **2 bits** for hosts:
    - There are **4 possible combinations**: `00`, `01`, `10`, `11`.

So, the number of unique combinations you can make with `n` bits is **2 raised to the power of `n`**, which gives you `2^n`.

In the context of networks:

- If you have 8 bits for hosts, the total number of possible addresses is `2^8 = 256`.
- If you have 16 bits for hosts, the total number of possible addresses is `2^16 = 65,536`.

### 3. **Why Subtract 2?**:

When calculating **usable hosts**, we subtract 2 from the total number of addresses to account for:

1. **Network Address** (the lowest address in the range):
    - This address represents the network itself and can't be assigned to any device.
    - Example: In `192.168.1.0/24`, the address `192.168.1.0` is the network address.
2. **Broadcast Address** (the highest address in the range):
    - This address is used to send data to all hosts on the network and also can't be assigned to a specific device.
    - Example: In `192.168.1.0/24`, the address `192.168.1.255` is the broadcast address.

So, from the total `2^n` possible addresses, we subtract 2 to exclude the network and broadcast addresses.

---

### 4. **Breaking It Down with an Example**:

Let’s take a `/24` network:

- **CIDR**: `192.168.1.0/24`
- **Network bits**: 24 (fixed)
- **Host bits**: `32 - 24 = 8 bits` for hosts

Now, why `2^8`? Because we have 8 bits for the host part. Since each bit can be `0` or `1`, 8 bits can generate 256 possible combinations (addresses).

However:

- **One address** (`192.168.1.0`) is reserved for the network.
- **Another address** (`192.168.1.255`) is reserved for broadcasting.

Thus, the usable addresses are `256 - 2 = 254`, meaning you can assign addresses to 254 hosts in this `/24` network.

---

### 5. **Why Do We Divide the IP Address?**

The reason we divide the IP address into **network** and **host** parts is for **efficient routing** and **addressing**:

- **Network portion**: Helps routers know which network the data should go to.
- **Host portion**: Helps identify specific devices (computers, phones, etc.) within that network.

By limiting the number of bits for hosts (and giving more bits to the network portion), we can create smaller, more manageable networks. On the other hand, if we need more hosts, we reduce the network portion to allow more host addresses.

---

### **Summary**:

- **Why `2^host bits`**: Each bit in the host portion can be either `0` or `1`, giving 2 possibilities per bit. So, with `n` bits, you get `2^n` possible combinations (addresses).
- **Why subtract 2**: Two addresses (network and broadcast) are reserved, so we subtract them from the total.
- **Why divide the IP address**: The split between network and host parts allows routers to efficiently send data to the correct network, and within that network, to the correct device.

### Subnetting a network

To get the **subnets** of a network, you need to break down a larger network into smaller networks, or subnets. This process is called **subnetting**. The idea is to take an IP block (like a `/16` or `/24`) and divide it into smaller blocks, each with its own network and host portions.

### Steps for Subnetting:

1. **Determine the Network You Are Starting With**:
    - You’ll have a **base network** (e.g., `192.168.1.0/24`), which has a certain number of **available host bits**.
    - For instance, in `192.168.1.0/24`, you have 8 bits available for hosts (32 bits in total minus 24 bits for the network portion).
2. **Decide How Many Subnets You Want**:
    - To create subnets, you "borrow" some of the **host bits** and convert them into **network bits**.
    - The number of subnets you can create depends on how many bits you borrow. For example, borrowing 2 bits gives you `2^2 = 4` subnets.
3. **Calculate the New Subnet Mask**:
    - Every time you borrow a bit, you increase the subnet mask. For example, starting with `/24`, if you borrow 2 bits, the subnet mask becomes `/26` (24 + 2 = 26).
4. **Determine the Subnet Ranges**:
    - After borrowing bits, you can calculate the range of IP addresses in each subnet. These ranges will be smaller than the original network, with fewer hosts available per subnet.

---

### Example: Subnetting a `/24` Network

Let's say you have the network `192.168.1.0/24` and you want to divide it into **4 subnets**. Here's how to do it:

### 1. **Start with the Base Network**:

- Network: `192.168.1.0/24`
- This means there are 8 bits available for hosts (since the first 24 bits are for the network).

### 2. **Borrow 2 Host Bits for Subnetting**:

- To create 4 subnets, you need to borrow 2 bits (because `2^2 = 4`).
- New subnet mask: `/24 + 2 = /26`.
- This leaves 6 bits for hosts (32 total bits minus 26 network bits).

### 3. **Calculate the Subnets**:

- The original `/24` network can be divided into **4 subnets**, each with a `/26` prefix.
- Each subnet will have a block size of `2^6 = 64` IP addresses (since 6 bits are left for hosts).

The subnets are:

1. **Subnet 1**: `192.168.1.0/26`
    - Range: `192.168.1.0` to `192.168.1.63` (64 addresses)
2. **Subnet 2**: `192.168.1.64/26`
    - Range: `192.168.1.64` to `192.168.1.127` (64 addresses)
3. **Subnet 3**: `192.168.1.128/26`
    - Range: `192.168.1.128` to `192.168.1.191` (64 addresses)
4. **Subnet 4**: `192.168.1.192/26`
    - Range: `192.168.1.192` to `192.168.1.255` (64 addresses)

Each of these subnets has 62 usable IP addresses (since 2 addresses in each subnet are reserved for the network and broadcast addresses).

---

### **Steps Summarized**:

1. **Start with your base network** (e.g., `192.168.1.0/24`).
2. **Determine how many subnets you need** and borrow bits accordingly.
3. **Increase the subnet mask** by the number of bits you borrowed.
4. **Calculate the subnet ranges** based on the new subnet mask.
5. **Assign subnets** to smaller networks.

---

### Additional Notes:

- **CIDR notation**: The more bits you borrow, the more subnets you can create, but each subnet will have fewer hosts.
- **Subnet mask**: This helps define the split between the network and the host portions of the IP address.

---

### Why We Subnet and How the Formula Works

Subnetting helps divide a large network into smaller, more manageable segments, each with its own subnet. This allows efficient use of IP addresses, provides better network organization, and enhances security by isolating network segments.

The formula for calculating subnets and hosts works because IP addresses are represented in **binary** form, which allows us to manipulate individual bits to represent either **network bits** or **host bits**.

Let’s break it down step-by-step:

---

### **The IP Address Structure**

- **IP addresses** are 32 bits long (IPv4) and are split into two parts:
    1. **Network portion**: This identifies the network.
    2. **Host portion**: This identifies the specific devices (hosts) within the network.

For example, an address like `192.168.1.0/24` means the first 24 bits are for the **network** and the remaining 8 bits are for **hosts**.

---

### **How the Formula Works**

Let’s understand two formulas:

1. **Number of Subnets** =

$$
2^{\text{Number of bits borrowed}}
$$

1. **Number of Hosts per Subnet** =
    
    $$
    2^{\text{Number of host bits}} - 2
    $$
    

### 1. **Number of Subnets**:

$$
2^{\text{Number of bits borrowed}}
$$

- When we "borrow" bits from the host portion to create subnets, each borrowed bit doubles the number of subnets. This is because every binary bit can represent 2 values (0 or 1).
- For example, if we start with a `/24` network (8 host bits) and we borrow 2 bits for subnetting, we get:
22=4 subnets.
This gives you 4 subnets.
    
    22=4 subnets.2^2 = 4 \text{ subnets}.
    

### 2. **Number of Hosts per Subnet**:

$$
2^{\text{Number of host bits}} - 2
$$

- The number of host bits left after borrowing determines how many devices (hosts) you can have in each subnet.
- For example, in a `/26` network (after borrowing 2 bits), you have 6 bits left for hosts (since 32 bits in total minus 26 for the network leaves 6 bits for hosts). The formula becomes:
26−2 = 64−2 =62 hosts per subnet.
    
    26−2 = 64−2 = 62 hosts per subnet. 2^6 - 2 = 64 - 2 = 62 hosts per subnet.
    
    - The -**2** is because the first IP is reserved for the **network address** and the last one is for the **broadcast address**.

---

### **Why the Formula Works**

IP addresses are **binary** numbers, which means the number of possible values doubles with each additional bit. Let’s look at how binary counting works:

- A **single bit** can represent two values: 0 and 1.
- **Two bits** can represent four values: 00, 01, 10, 11.
- **Three bits** can represent eight values: 000, 001, 010, 011, 100, 101, 110, 111.

Thus, for every bit you borrow (for subnetting), you double the number of subnets. This is why the formula $2^{\text{bits}}$  works: each bit represents a power of 2.

Similarly, each bit you leave for **hosts** increases the number of available hosts. Since the number of hosts is calculated by the remaining host bits, $2^{\text{host bits}}$ represents how many possible combinations of IPs there are for hosts.

---

### **Real-World Example**

Let’s say you manage a company with **200 devices**. You have a `/24` block (which can support 254 hosts), but you want to break the company into **4 subnets** to isolate different departments.

1. You start with the `192.168.1.0/24` network. You decide to borrow 2 bits for subnetting because you want 4 subnets (`2^2 = 4`).
    - New subnet mask: `/24 + 2 = /26`.
    - Each subnet will now have 62 usable IP addresses (`2^6 - 2 = 62`).
2. You create 4 subnets:
    - **Subnet 1**: `192.168.1.0/26` (hosts 0-63)
    - **Subnet 2**: `192.168.1.64/26` (hosts 64-127)
    - **Subnet 3**: `192.168.1.128/26` (hosts 128-191)
    - **Subnet 4**: `192.168.1.192/26` (hosts 192-255)

Each department can now be assigned a subnet, with up to 62 devices in each. You efficiently used your `/24` block and organized the network.

---

### **Summary of Why and How Subnetting Works**:

- **Why**: Subnetting allows you to divide a larger network into smaller, more manageable pieces, optimizing IP usage, improving performance, and enhancing security.
- **How**: Subnetting uses binary mathematics to borrow host bits to create new subnets, with each borrowed bit doubling the number of subnets. The remaining host bits determine the number of available IP addresses in each subnet.

By understanding binary operations, you can see why 2x2^x2x is used for calculating both the number of subnets and hosts per subnet, and how the formulas ensure efficient IP management.

### Steps for Subnetting a `/16` into `/24` Subnets

When you're subnetting a `/16` network into `/24` subnets, you're essentially creating smaller networks with a more specific subnet mask. In this case, you don’t necessarily need to worry about how many subnets are being created if you just want a specific size of `/24` subnets. Let's break it down:

### Steps for Subnetting a `/16` into `/24` Subnets

1. **Start with the Base Network**:
    - You have a `/16` network, like `192.168.0.0/16`.
    - In a `/16` network, the first 16 bits are for the network portion, leaving you 16 bits for hosts.
2. **New Subnet Mask**:
    - You want to create `/24` subnets, which means you’re going to extend the network portion from 16 bits to 24 bits.
    - You’re "borrowing" 8 bits from the original 16 host bits to create these subnets.
3. **Number of Subnets**:
    - By borrowing 8 bits, you’re creating 28=256 subnets.
        
        28=2562^8 = 256
        
    - Each subnet will have 256 IP addresses (because a `/24` has 8 bits left for hosts).
4. **Subnet Size**:
    - Each `/24` subnet has 256 addresses in total, with 254 usable IP addresses (since 2 are reserved for the network and broadcast addresses).

---

### Subnet Example

Let's say you have the network `192.168.0.0/16`. You want to create `/24` subnets from this. Here's how it works:

- **Original Network**: `192.168.0.0/16` (this allows for up to 65,536 IP addresses).
- By subnetting it into `/24`, you create subnets with 256 addresses each.

### First few `/24` Subnets:

1. **Subnet 1**: `192.168.0.0/24`
    - Range: `192.168.0.0` to `192.168.0.255` (256 addresses)
2. **Subnet 2**: `192.168.1.0/24`
    - Range: `192.168.1.0` to `192.168.1.255` (256 addresses)
3. **Subnet 3**: `192.168.2.0/24`
    - Range: `192.168.2.0` to `192.168.2.255` (256 addresses)
4. **Subnet 4**: `192.168.3.0/24`
    - Range: `192.168.3.0` to `192.168.3.255` (256 addresses)

This pattern continues up to `192.168.255.0/24`.

---

### Does it Make Sense to Care About the Number of Subnets?

In many cases, you don't need to worry about how many subnets you're creating, especially if you're designing a network for a specific purpose (e.g., needing multiple `/24` subnets for a particular setup). The important thing is:

- **Subnet Size**: The `/24` subnets each provide 256 IP addresses.
- **Subnet Management**: Depending on your network structure, you might want to track how many subnets you create, but the focus is on creating the right subnet size to meet your needs.

However, from a planning perspective, knowing that you create 256 subnets when subnetting a `/16` into `/24` networks helps manage the allocation of these subnets effectively.

### Why You Do This:

1. **Flexibility**: Subnetting allows you to divide a large network into smaller, manageable blocks. If you need `/24` subnets for different departments, regions, or purposes, you can easily break down the network.
2. **Efficient Use of IPs**: This approach helps in efficient allocation, where each `/24` subnet is small enough to prevent waste while still providing enough IPs for your needs.

So, you can break down a `/16` network into as many `/24` subnets as needed, and in this case, you would get exactly 256 `/24` subnets.

### **how many subnets** were made when subnetting a network, you can use this formula:

$$
\text{Number of Subnets} = 2^{\text{number of bits borrowed from the host portion}}
$$

### Step-by-Step Explanation

1. **Identify the original prefix** (network size) before subnetting.
2. **Identify the new prefix** (subnet size) after subnetting.
3. **Calculate the number of bits borrowed**: Subtract the original prefix length from the new prefix length.
4. Use the formula  $2^{\text{bits borrowed}}$ to calculate how many subnets were created.

---

### Example 1: Subnetting a `/24` into `/26`

- **Original network**: `/24` (which means the first 24 bits represent the network, leaving 8 bits for hosts).
- **New subnet**: `/26` (meaning 26 bits represent the network, leaving 6 bits for hosts).
- **Bits borrowed**: 26−24 = 2 bits.
    
    `26−24 = 226 - 24 = 2`
    

Using the formula:

$$
\text{Number of subnets} = 2^2 = 4 \text{ subnets}.
$$

So, subnetting a `/24` into `/26` gives you **4 subnets**.

---

### Example 2: Subnetting a `/24` into `/25`

- **Original network**: `/24` (leaving 8 bits for hosts).
- **New subnet**: `/25` (meaning 25 bits represent the network, leaving 7 bits for hosts).
- **Bits borrowed**: 25−24=1 bit.
    
    $25−24 = 1$
    

Using the formula:

$$
\text{Number of subnets} = 2^1 = 2 \text{ subnets}.
$$

So, subnetting a `/24` into `/25` gives you **2 subnets**.

---

### Subnetting Visualization

To better understand, here’s a visualization of how a `/24` network can be subnetted:

1. **Subnetting a `/24` into `/25`**:
    - Network: `192.168.1.0/24`
    - Two subnets:
        - **Subnet 1**: `192.168.1.0/25` (hosts 0-127)
        - **Subnet 2**: `192.168.1.128/25` (hosts 128-255)
2. **Subnetting a `/24` into `/26`**:
    - Network: `192.168.1.0/24`
    - Four subnets:
        - **Subnet 1**: `192.168.1.0/26` (hosts 0-63)
        - **Subnet 2**: `192.168.1.64/26` (hosts 64-127)
        - **Subnet 3**: `192.168.1.128/26` (hosts 128-191)
        - **Subnet 4**: `192.168.1.192/26` (hosts 192-255)

---

### Summary of Key Points

- **To calculate the number of subnets**: Subtract the original prefix length from the new subnet prefix length to find the number of bits borrowed. Then use 2bits borrowed2^{\text{bits borrowed}}2bits borrowed to find the number of subnets.
- **Subnetting a `/24` into `/25`**: You get 2 subnets.
- **Subnetting a `/24` into `/26`**: You get 4 subnets.

This method helps manage large networks by dividing them into smaller subnetworks.