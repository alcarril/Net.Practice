# 🌐 Netpractice 🌐

## Overview

Netpractice is a networking project from the 42 curriculum focused on understanding **IP addressing and routing fundamentals**. The project consists of solving a set of interactive exercises where the user must correctly configure network devices so that communication between hosts is possible.

The main goal is to develop a solid understanding of how devices communicate at **OSI layers 1, 2, and 3**, with emphasis on IPv4 addressing, subnet masks, routing tables, and default gateways.



## Requirements

* Linux or macOS
* A modern web browser (Firefox, Chromium, Chrome, etc.)
* `tar` utility



## Installation

Extract the project archive provided in the repository.

**From the CLI:**

```bash
tar -xvf netpractice.tgz
```

**From the graphical environment:**

Double-click the `.tgz` file to extract it.



## Usage

After extracting the files, open the interface using a web browser.

**- From the CLI:**

```bash
firefox index.html
```

*(Any modern browser can be used.)*

**- From the graphical environment:**

Right-click on `index.html` → **Open with** → select your browser.

### Modes of Operation

Once opened, the Netpractice interface will load. There are two modes available:

<img src="img/Usage/interfaz.png" width="150" height="200">

#### Training Mode

Training mode allows practice using a **personalized configuration** associated with the user login.

* Contains **10 levels** with increasing difficulty.
* Each level presents a **network topology diagram** with missing fields.
* The user must configure:

  * IPv4 addresses
  * Subnet masks
  * Default gateways
  * Routing tables

The objective is to ensure correct communication between all devices according to the given topology.

<img src="img/Usage/demo.png" width="500" height="450">

After completing a level:

* **Check again** validates the configuration.
* **Get my config** exports the configuration as a **JSON file**.
* Successfully validating a level unlocks the **next level**.

<img src="img/Usage/Options.png" width="300" height="70">


At the bottom of the interface, **packet flow logs** display how IP packets traverse the network. These logs are essential for debugging issues such as:

* Incorrect or missing default gateways
* Invalid IP addresses
* Wrong subnet masks

<img src="img/Usage/login.png" width="250" height="250">

#### Evaluation Mode

Evaluation mode generates a **randomized network configuration**, intended for assessments.

* Exercises are selected randomly.
* Focuses mainly on **levels 6 and above**, where routing complexity increases.



## TCP/IP Concepts Covered

The project relies on the following networking concepts:

* Computer networks fundamentals
* OSI model (layers 1–3)
* Communication protocols
* IPv4 protocol:

  * IP addressing structure
  * Subnet masks
  * Network and broadcast addresses
  * Routing tables
  * Subnetting
  * Default gateway

---

## Levels Description

<details>
<summary>Level 1</summary>
# Level 1 – Basic LAN IP Assignment

## LAN 1 – 2 hosts connected
- **Fixed interface:** 104.97.23.12/24  
- **Network:** 104.97.23.0/24 (LAN)  
- **Available host IPs:** 104.97.23.1 – 104.97.23.254  
- **Task:** Assign any available host IP to the configurable interface  
- **Note:** Both interfaces belong to the same Layer 3 LAN and can communicate directly

## LAN 2 – 2 hosts connected
- **Fixed interface:** 211.191.153.75/16  
- **Network:** 211.191.0.0/16 (LAN)  
- **Available host IPs:** 211.191.0.1 – 211.191.255.254  
- **Task:** Assign any available host IP to the configurable interface  
- **Note:** Both interfaces belong to the same Layer 3 LAN and can communicate directly


<img src="img/levels/level1/L1raw.png" width="450" height="280">  <img src="img/levels/level1/L1solved.png" width="450" height="280">

</details>

<details>
<summary>Level 2</summary>
# Level 2 – LAN IP Address Configuration with Fixed and Configurable Interfaces

## LAN 1 – 2 hosts connected
- **Fixed interface:** 192.168.109.222/27  
- **Network:** 192.168.109.192/27 (LAN)  
- **Subnet mask:** 255.255.255.224 (/27)  
- **Available host IPs:** 192.168.109.193 – 192.168.109.222 (excluding fixed IP)  
- **Host addressing:** 4 bits available → 32 possible addresses per subnet  
- **Task:** Assign any available host IP to the configurable interface  
- **Note:** Both interfaces belong to the same Layer 3 LAN and can communicate directly

## LAN 2 – 2 hosts connected
- **Fixed interface:** 127.0.0.1/30  
- **Network:** 127.0.0.0/30 (LAN)  
- **Subnet mask:** 255.255.255.252 (/30)  
- **Available host IPs:** 127.0.0.1 – 127.0.0.2 (excluding loopback)  
- **Host addressing:** 2 bits available → 2 usable host IPs  
- **Task:** Assign a valid host IP to the configurable interface, avoiding loopback addresses  
- **Note:** Both interfaces belong to the same Layer 3 LAN and can communicate directly

<img src="img/levels/level2/L2raw.png" width="450" height="280">  <img src="img/levels/level2/L2solved.png" width="450" height="280">
</details>

<details>
<summary>Level 3</summary>
# Level 3 – LAN IP Address Configuration

## LAN 1 – 3 hosts connected through a switch
- **Network:** 104.198.85.0/25 (LAN)  
- **Subnet mask:** 255.255.255.128 (/25)  
- **Fixed interface IP:** 104.198.85.125  
- **Network address:** 104.198.85.0/25  
- **Broadcast address:** 104.198.85.127  
- **Usable host range:** 104.198.85.1 – 104.198.85.126  
- **Task:** Assign configurable interfaces any available IP within this range to remain in the same LAN  
- **Switch:** Operates at Layer 2 only, facilitating Ethernet frame forwarding; no IP configuration needed

<img src="img/levels/level3/L3raw.png" width="450" height="280">  <img src="img/levels/level3/L3solved.png" width="450" height="280">
</details>

<details>
<summary>Level 4</summary>
# Level 4 – LAN IP Address Configuration with Router

## Scenario
Two hosts connected through a switch to a router with 3 interfaces.

---

## R1 – Existing LAN interface
- **IP:** 85.207.110.244/26  
- **Subnet mask:** 255.255.255.192  
- **Network address:** 85.207.110.192/26  
- **Usable hosts:** 85.207.110.193 – 85.207.110.254  
- **Broadcast:** 85.207.110.255  
- **Total usable hosts:** 62  

---

## R2 – Existing LAN interface
- **IP:** 85.207.110.1/25  
- **Subnet mask:** 255.255.255.128  
- **Network address:** 85.207.110.0/25  
- **Usable hosts:** 85.207.110.1 – 85.207.110.127  
- **Broadcast:** 85.207.110.127  
- **Total usable hosts:** 126  

---

## R3 – Configurable LAN interface
- **Purpose:** Assign IPs to a new LAN without overlapping R1 or R2 subnets  
- **Subnet mask:** /26 (255.255.255.192)  
- **Network address:** 85.207.110.128/26  
- **Usable hosts:** 85.207.110.129 – 85.207.110.190  
- **Broadcast:** 85.207.110.191  
- **Example host IP:** 85.207.110.132  
- **Task:** Assign IP addresses to devices in the new LAN using this subnet  
- **Note:** All devices must share the same Layer 3 LAN and subnet mask (/26) for proper communication  
- **Switch:** Operates at Layer 2 only, forwarding Ethernet frames  

---

**Tip:** When router interfaces have the same network portion in their IPs, they belong to the same subnet. Ensure the new LAN's subnet does not overlap with existing subnets.

<img src="img/levels/level4/L4raw.png" width="450" height="280">  <img src="img/levels/level4/L4solved.png" width="450" height="280">
</details>

<details>
<summary>Level 5</summary>
# Level 5 – LAN-to-LAN Communication via Router (Gateways)

## Scenario
Two separate LANs connected to the same router. Each LAN has one host. Routing uses the router interfaces as gateways.

---

## LAN 1 – Host A connected to Router interface RA
- **Router interface RA:** 166.114.199.254/20 (mask 255.255.240.0, network 166.114.192.0/20, LAN)  
- **Broadcast address:** 166.114.207.255  
- **Usable host range:** 166.114.192.1 – 166.114.207.254  
- **Total usable hosts:** 4094  
- **Host A configuration:**  
  - IP: any available host in the LAN (example 166.114.192.1)  
  - Subnet mask: 255.255.240.0  
  - Gateway: 166.114.199.254 (RA)

---

## LAN 2 – Host B connected to Router interface RB
- **Router interface RB:** 87.71.70.126/25 (mask 255.255.255.128, network 87.71.70.0/25, LAN)  
- **Broadcast address:** 87.71.70.127  
- **Usable host range:** 87.71.70.1 – 87.71.70.126  
- **Total usable hosts:** 126  
- **Host B configuration:**  
  - IP: any available host in the LAN (example 87.71.70.1)  
  - Subnet mask: 255.255.255.128  
  - Gateway: 87.71.70.126 (RB)

---

## Routing / Gateway Logic
- There is no communication with other devices in the same LAN, so **all traffic is sent to the gateway**.  
- Two configuration options:
  1. **Default route:** All traffic goes to the router interface.  
  2. **Specific route:** Traffic to the other host or its network is sent to the gateway.  
- **Option 2 is convenient** since each LAN has only one external host to reach.

<img src="img/levels/level5/L5raw.png" width="450" height="280">  <img src="img/levels/level5/L5solved.png" width="450" height="280">
</details>

<details>
<summary>Level 6</summary>
# Level 6 – LAN-to-Internet Communication via Router (9-point structure)

## Scenario
One LAN connects a router to a host through a switch, with Internet connected to the router.  
**Main task:** Route all traffic from Internet to LAN 1 via the router interface and set the **default route in Host 1** for all traffic outside its LAN.

---

## LAN 1 – Host 1 connected to Router interface RA through a switch
- **Router interface RA (LAN side):** 92.79.157.227/25  
- **Subnet mask:** 255.255.255.128  
- **Network address:** 92.79.157.128/25  
- **Broadcast address:** 92.79.157.255  
- **Usable host range:** 92.79.157.129 – 92.79.157.254  
- **Total usable hosts:** 126  
- **Gateway for Host 1:** 92.79.157.227 (RA interface)  
- **Host 1 IP:** Any available host in the LAN (example 92.79.157.129)  
- **Routing logic:** All traffic outside the LAN is sent to the gateway RA (default route in Host 1 routing table)

---

## Router – connecting LAN 1 to Internet
- **Router interface RA:** connected to LAN 1  
- **Router interface RB:** 163.172.250.12/28 (Internet side)  
- **Subnet mask RB:** 255.255.255.240  
- **Network address RB:** 163.172.250.0/28  
- **Broadcast address RB:** 163.172.250.15  
- **Usable host range RB:** 163.172.250.1 – 163.172.250.14  
- **Total usable hosts RB:** 14  
- **Task:** Forward all traffic not in LAN 1 via RB  
- **Routing logic:** Default route for all unknown traffic goes to RB (towards Internet)

---

## Internet – connected to Router RB
- **Internet connection to Router RB interface**  
- **Gateway:** Router RB interface (163.172.250.12)  
- **Routing table:** Directs all traffic destined to LAN 1 (92.79.157.128/25) through Router RB  
- **Purpose:** Ensure packets reach LAN 1 via RA  
- **Other traffic:** Follows normal Internet routing rules  
- **Host configuration:** No additional configuration required  
- **Main task:** Route traffic to LAN 1 via RB; default routing outside LAN 1 handled by RB interface

<img src="img/levels/level6/L6raw.png" width="450" height="280">  <img src="img/levels/level6/L6solved.png" width="450" height="280">
</details>

<details>
<summary>Level 7</summary>
# Level 7 – Three Networks Connecting Two Hosts via Two Routers

**Scenario** – The main goal of this level is to configure subnets between LAN 1 (Host 1 ↔ Router 1) and WAN 1 (Router 1 ↔ Router 2) and ensure proper routing between routers. Each router has its own routing table. The key concept is that Router 1 must route traffic to Router 2 (next hop), and Router 2 must route traffic back to Router 1 for bidirectional communication. Host 1 and Host 2 must use their respective router interfaces as gateways to reach the other host.  

---

## Network Configuration Overview
**Main network:** 118.198.14.0/24 – this is the base network from which subnets will be derived.  
**Subnetting goal:**  
- LAN 1: connect Host 1 to Router 1  
- WAN 1: connect Router 1 to Router 2  
- LAN 3: connect Router 2 to Host 2 (can be a subnet of 118.198.14 or a new network)  

---

## LAN 1 – Host 1 to Router 1
**Router 1 interface (LAN side):** 118.198.14.1  
**Subnet mask:** 255.255.255.240 (/28) – supports 14 usable hosts (118.198.14.1 – 118.198.14.14)  
**Network address:** 118.198.14.0/28  
**Gateway (Host 1):** 118.198.14.1  
**Host 1 IP:** any available IP in subnet (example 118.198.14.2)  
**Routing logic:** all traffic outside LAN 1 is sent to Router 1 interface (default route) or via WAN 1 to reach Host 2  

---

## WAN 1 – Router 1 to Router 2
**Router 1 interface (WAN side):** 118.198.14.254  
**Router 2 interface (WAN side):** 118.198.14.253  
**Subnet mask:** 255.255.255.252 (/30) – 2 usable hosts  
**Network address:** 118.198.14.252/30  
**Task:** assign IPs to both router interfaces within this WAN subnet  
**Routing logic:** Router 1 default route → Router 2 (next hop), Router 2 default route → Router 1 (next hop)  

---

## LAN 3 – Router 2 to Host 2
**Router 2 interface (LAN side):** configurable IP (can be a subnet of 118.198.14 or a new network)  
**Subnet mask:** defined per network design  
**Gateway (Host 2):** Router 2 interface  
**Host 2 IP:** any available IP in subnet  
**Routing logic:** all traffic outside LAN 3 or destined to Host 1/network is sent to Router 2 interface (default route or via WAN 1)  

---

## Key Concepts
- Subnetting separates LAN 1 and WAN 1 to avoid IP overlap  
- WAN connecting routers uses a /30 subnet for two usable IPs  
- Hosts use router interfaces as default gateways  
- Routers forward unknown traffic via default route to the next router (next hop)  
- LAN 3 can be a new subnet or part of the main network 118.198.14  
<img src="img/levels/level7/L7raw.png" width="450" height="280">  <img src="img/levels/level7/L7solved.png" width="450" height="280">
</details>

<details>
<summary>Level 8</summary>
# Level 8 – Two LANs Connecting Hosts via Router 2 to Internet

**Scenario** – Two LANs, each with one host, connect to Router 2. Router 2 connects to Router 1 via a WAN, and Router 1 connects to Internet via another WAN. Hosts must communicate with each other and with Internet. Internet routing table specifies all traffic destined to 167.140.219.0/26 (64 usable IPs). Router 2 WAN interface connecting to Router 1 must share the same subnet as Router 1 WAN interface. Router 1 uses next hop 167.140.219.49 in its routing table for traffic destined to the subnet of Router 2 (the key concept of this level).

---

## Internet
**Destination network:** 167.140.219.0/26 (mask 255.255.255.192)  
**Usable host range:** 167.140.219.1 – 167.140.219.62  
**Routing logic:** all traffic destined to this network is sent via Router 1 WAN interface  

---

## Router 2 – Connecting Two LANs
**LAN 1 interface:** configurable IP within subnet < 64  
**LAN 2 interface:** configurable IP within subnet < 64, non-overlapping with LAN 1  
**WAN interface to Router 1:** part of the same subnet as Router 1 WAN (Next Hop 167.140.219.49)  
**Subnetting logic:** divide 64 available IPs into two sub-LANs for connected hosts  
**Routing logic:**  
- All traffic from LANs destined outside their subnet is sent to WAN interface (next hop Router 1)  
- Default route points to Router 1 for Internet-bound traffic  

---

## Router 1 – Connecting Router 2 to Internet
**WAN interface to Internet:** preconfigured  
**WAN interface to Router 2:** IP within the same subnet as Router 2 WAN interface  
**Routing table:** two entries  
1. **Default route:** all unknown traffic (Internet-bound) is sent via WAN interface to Internet  
2. **Subnet route:** all traffic destined to the subnet connecting Router 2 (167.140.219.0/26) is sent to next hop 167.140.219.49 (Router 2 WAN interface) – this is the key nexthop concept of this level  

---

## Hosts
**Host 1 & Host 2 IPs:** any available IP in their respective LAN subnets (<64)  
**Gateway:** Router 2 LAN interface connected to the host  
**Routing logic:** all traffic outside the LAN is sent to Router 2 interface (default route or specific route to the other host)  

---

## Key Concepts
- WAN connections between routers must be in the same subnet  
- Router 2 WAN interface IP aligns with Router 1 WAN next hop (167.140.219.49)  
- Router 1 routing table has two entries: default to Internet, subnet to Router 2 (nexthop)  
- Subnetting ensures LANs do not overlap and remain within 167.140.219.0/26 limits  
- Hosts use Router 2 interfaces as default gateways  
- Routers forward traffic appropriately: LAN ↔ LAN, LAN ↔ Internet via WANs  
<img src="img/levels/level8/L8raw.png" width="450" height="280">  <img src="img/levels/level8/L8solved.png" width="450" height="280">
</details>

<details>
<summary>Level 9</summary>
# Level 9 – Summary

This level consolidates most of the routing concepts seen so far.

## Network Topology
There are **5 networks** in total:

1. **LAN 1**  
   Two hosts (ION and MESON) are connected through a switch to router **R1**.  
   - The subnet mask is given on the router interface and must be used for all LAN devices.  
   - Each host configures a **default gateway** pointing to router interface **R11**.

2. **WAN to Internet**  
   Router **R1** connects directly to Internet through interface **R12**.  
   - IP address and mask are already provided.  
   - This interface is used for all unknown (default) traffic.

3. **WAN between routers**  
   Router **R1 (R13)** connects to **Router R2 (R21)**.  
   - This is a **WAN link**.  
   - Both interfaces (**R13 and R21**) must be in the **same subnet**.  
   - The subnet mask given on **R21** is reused on **R13**.

4. **LAN 2**  
   Router **R2** connects to host **CATION**.  
   - The subnet mask is given and must be used for all devices in this LAN.

5. **LAN 3**  
   Router **R2** connects to host **GLUON**.  
   - IP address and mask can be freely chosen.

## Routing Tables (Key Concept)

### Hosts
- All hosts use a **default route** pointing to their directly connected router interface.

### Router R2
- Routes **all default traffic** to its **next hop**, which is **Router R1**.

### Router R1 (Critical)
Router R1 has **two types of routes**:
1. **Default route** → Interface **R12** (Internet)
2. **Specific routes** → Traffic destined for **CATION and GLUON networks** is sent to **next hop R21**

### Internet
- Internet routes all traffic destined to **LAN 1 (ION and MESON)** through **R12**, ensuring bidirectional communication.

## Core Idea
The key point of this level is understanding how:
- WAN links between routers must share the same subnet
- Routers use **default routes + specific routes**
- Bidirectional communication requires correct routing on **both routers and Internet**
<img src="img/levels/level9/L9raw.png" width="450" height="280">  <img src="img/levels/level9/L9solved.png" width="450" height="280">
</details>

<details>
<summary>Level 10</summary>
# Level 10 — Multi-Subnet Routing over a Single Major Network (Corrected)

## Overview
This level focuses on **subnetting a single major network into 5 non-overlapping subnets** and configuring routing so that **all LANs and Internet can communicate** through two routers.  
The critical aspects are **correct address allocation**, **WAN separation**, and **routing tables on Router R1 and R2**.

---

## Major Network
- **Base network:** 150.233.186.0/24  
- All five networks are **subnets of this same /24**

---

## Network 1 — Internet ↔ Router R1 (WAN)
- **Type:** WAN
- Connects **Internet** to **Router R1**
- IP and mask are **given by default**
- Internet routes traffic destined to internal networks via **Router R1**

---

## Network 2 — LAN 1 (Router R1 ↔ Hosts)
- **Interface:** R11
- **Type:** LAN
- IP and mask are given on R11
- Subnet range:
  - **150.233.186.1 – 150.233.186.127**
- Hosts:
  - Share the same subnet mask
  - Use **R11 as default gateway**

---

## Network 3 — WAN (Router R1 ↔ Router R2)
- **Interfaces:** R13 (R1) ↔ R21 (R2)
- **Type:** WAN
- **Subnet range:**  
  - **150.233.186.253 – 150.233.186.254**
- This subnet:
  - Is used **only to interconnect the routers**
  - Must be the **same on both interfaces**
  - Typically uses a **/30 mask**

---

## Network 4 — LAN 2 (Router R2 ↔ Host)
- **Interface:** R23
- **Type:** LAN
- **Subnet range:**  
  - **150.233.186.198 – 150.233.186.194**  
  *(small dedicated LAN, mask adjusted accordingly)*
- Host uses **R23 as default gateway**

---

## Network 5 — LAN 3 (Router R2 ↔ Host)
- **Interface:** R22
- **Type:** LAN
- **Remaining address space**
- **Subnet range:**  
  - **150.233.186.196 – 150.233.186.252**
- Mask chosen to:
  - Avoid overlap
  - Cover all remaining usable addresses
- Host uses **R22 as default gateway**

---

## Routing Logic — Router R1
- **Default route:**
  - All unknown traffic → **R12 (Internet interface)**
- **Internal routing:**
  - Traffic destined to subnets behind **Router R2** → **R13**
- Routes can be configured as:
  - Specific routes for R22 and R23 subnets
  - Or a broader route covering the internal address space toward **R21**

---

## Routing Logic — Router R2
- **Default route:**
  - All traffic → **R21 (towards Router R1)**
- Directly connected routes:
  - LAN via **R22**
  - LAN via **R23**
  - WAN via **R21**

---

## Key Takeaways
- All subnets are carved from **one /24 network**
- The **router-to-router link** uses the **highest addresses (.253–.254)**
- R23 uses a **small, fixed LAN range**
- R22 consumes **all remaining addresses**
- Correct routing requires:
  - Default routes outward
  - Explicit routes toward internal subnets via the WAN

<img src="img/levels/level10/L10raw.png" width="450" height="280">  <img src="img/levels/level10/L10solved.png" width="450" height="280">
</details>

---
## Resources

* OSI Model documentation
* IPv4 addressing and subnetting guides
* Routing and networking fundamentals

---

## Author

**alcarril**  
42 Network Curriculum Project

