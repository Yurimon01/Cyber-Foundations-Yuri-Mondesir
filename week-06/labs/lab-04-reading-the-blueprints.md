# Week 6 Lab 04 — Reading the Blueprints

**Student Name:** Yuri Mondesir

**Date Completed:** 9/12/2026

**Module:** 2 — Networking & Cloud Foundations | **Week:** 6  
**Submission Path:** `week-06/labs/lab-04-reading-the-blueprints.md`

---

> ### 🔒 Cloud Heights Security Rule
> Your Bastion link and Cloud Heights password are **private access credentials**. Never paste either into a worksheet, screenshot, GitHub repository, Circle post, or chat message. When taking screenshots, crop out the browser address bar and all login information.

---

## Overview

**This is a SHORT lab — 15 to 20 minutes.** It is deliberately small. You already have the commands; this lab is about matching a drawing to reality.

The **Cloud Heights Network Blueprint** is displayed at the top of this lab page in the portal. Everything you write about the network's architecture comes from that blueprint or from your own machine — never from a guess.

---

## Lab Environment / Pre-Lab Check

| Component | Details |
|---|---|
| Environment | Cloud Heights — live Ubuntu 22.04 VM, reached through Azure Bastion |
| Source of truth | The Cloud Heights Network Blueprint shown at the top of this lab page |
| Commands used | `ip addr`, `ip route` |
| Known value | Student subnet: **`10.60.6.0/26`** |

---

## Part A — Read the Drawing

### Step 1 — Record the Architecture Values

From the blueprint at the top of this page, record each value **exactly as drawn**. If a value is not shown on the blueprint, write "not shown on blueprint" — do not guess.

| Item | Value from the blueprint |
| --- | --- |
| VNet name | vent-cf-labs |
| VNet address space | 10.60.6.0/24 |
| Student subnet range | 26 |

---

## Part B — Verify Against Your Own Machine

### Step 1 — Confirm Your Address Lives in the Subnet

Run `ip addr` and find your private IPv4 address.

Command and output:

```
ip addr

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 60:45:bd:4b:c0:b8 brd ff:ff:ff:ff:ff:ff
    inet 10.60.6.30/26 metric 100 brd 10.60.6.63 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::6245:bdff:fe4b:c0b8/64 scope link 
       valid_lft forever preferred_lft forever
3: enP62367s1: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master eth0 state UP
 group default qlen 1000
    link/ether 60:45:bd:4b:c0:b8 brd ff:ff:ff:ff:ff:ff
    altname enP62367p0s2
```

Your private IP:

```
10.60.6.30
```

Explain how you know your address falls inside `10.60.6.0/26` — what range does that prefix actually cover:

```
Sobecause 32-26 = 6. We have 6 bits that tells us what neighborhood were in. so 2 to the power of 6 is 64. Meaning whatever lies between 0 and 63 are covered!
```

### Step 2 — Confirm Route Behaviour

Run `ip route`.

Command and output:

```
ip route 

10.60.6.0/26 dev eth0 proto kernel scope link src 10.60.6.30 metric 100 
10.60.6.1 dev eth0 proto dhcp scope link src 10.60.6.30 metric 100 
168.63.129.16 via 10.60.6.1 dev eth0 proto dhcp src 10.60.6.30 metric 100 
169.254.169.254 via 10.60.6.1 dev eth0 proto dhcp src 10.60.6.30 metric 100 
analyst@cf-student-11:~$ ^C
```

What the default route tells you about traffic that is not destined for your own subnet:

```
My default route tells me that traffic that is not included in my subset will be routed to that default gateway.
```

### Step 3 — Capture Your Evidence

**Required filename:** `blueprint-verified.png`

This must be **your own `ip addr` and `ip route` output** — not a re-screenshot of the blueprint. Crop out the address bar and any login information.

![Blueprint verified — my address inside the student subnet](https://raw.githubusercontent.com/Yurimon01/Cyber-Foundations-Yuri-Mondesir/refs/heads/main/assets/screenshots/week-06/blueprint-verified.png)

---

## Part C — How Traffic Actually Moves

### Step 1 — No Public IP

Your VM has a private address and **no public IP**. Explain what that means for who can reach it directly from the internet:

```
Our VMs have private addresses and public addresses, that means that there is no information from our VM that can reach the internet. And vise versa, the only way this is able to happen is through NAT.
```

### Step 2 — Outbound vs. Inbound

Outbound internet traffic from your VM leaves through address **translation (NAT)**. Inbound access for you arrives through **Azure Bastion**, not through a public address on the VM.

Explain both directions in your own words:

```
So basically when my VM sends traffic to the internet, it has to goes through NAT because my VM only has a private IP address. (This is basically like a front desk that meets in the middle) When I need to access my VM inbound, I use Azure Bastion instead of connecting directly to a public IP on the VM. This allows my VM to communicate outside of its private network without needing its own public IP address.
```

### Step 3 — The Guard Post You Do Not Touch Yet

Each student machine sits behind its own **network security group** — a per-student guard post that decides what traffic is allowed in.

**In Week 6 you do not configure it.** Week 7 is when you take control of those rules.

Write one sentence naming what the guard post does and one sentence stating what you are *not* doing with it this week:

```
The NSG acts a guard post who decides what is allowed to come in and we are not configuring anything this week.
```

---

## Analysis Questions

**Analysis Question 1.** Why would an organization put every student machine in one small subnet instead of giving each machine a public address? *(Minimum 3 sentences.)*

```
Well, there are a couple benefits to not doing the latter. For one you can protect your assets more easily if you have a private IP and a VM. This way communicating between IPs would be easier. As each machine would be in the same neighborhood. A company can also curate its own protections, permissions and configurations for the machines on the subnet more efficiently.
```

**Analysis Question 2.** Segmentation means separating a network into parts that cannot freely reach each other. Give one concrete benefit of segmentation during a security incident. *(Minimum 3 sentences.)*

```
Segmentation brings the benefit of easy clean-ups. If an issue occured in one part of the network there will be more time to fix that issue without worry of it spreading into another network. This is more of an after-the-fact benefit, that aids in situations that are more sporadic. But once it does occur, an organization would be glad that the system was set up that way.
```

**Analysis Question 3.** A diagram and a live machine disagree about an address range. Which do you trust, what do you do next, and why? *(Minimum 2 sentences.)*

```
I am going to say a live machine. A live machine is getting data from it's programmers and users on the daily. A diagram could've been made at a point in time that differs from the configurations of the current day. 
```

---

## Submission Checklist

- [x] VNet name, address space, and subnet range recorded from the blueprint (Part A)

- [x] `ip addr` run and own private IP confirmed inside `10.60.6.0/26` (Part B, Step 1)

- [x] `ip route` run and default route behaviour explained (Part B, Step 2)

- [x] `blueprint-verified.png` captured from your own terminal, cropped, uploaded to `assets/screenshots/week-06/` (Part B, Step 3)

- [x] Private address / NAT / Bastion explained (Part C, Steps 1–2)

- [x] Per-student guard post identified — and explicitly not configured this week (Part C, Step 3)

- [x] All three Analysis Questions answered (minimum sentence counts met)

- [x] This file is committed to your portfolio repo at `week-06/labs/lab-04-reading-the-blueprints.md`

---

## GitHub Commit Subsection

1. Open **Week 6 → Lab 04: Reading the Blueprints** in the Lab Portal.
2. Fill in the worksheet fields and upload `blueprint-verified.png` to `assets/screenshots/week-06/`.
3. Click **Submit to GitHub** — the Portal commits to `week-06/labs/lab-04-reading-the-blueprints.md`.

---

*CyberVisionaries Institute · Cyber Foundations · Tier I*
