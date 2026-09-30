# Week 6 Lab 05 — Layer Detective

**Student Name:** Yuri Mondesir

**Date Completed:** 9/17/2026

**Module:** 2 — Networking & Cloud Foundations | **Week:** 6  
**Submission Path:** `week-06/labs/lab-05-layer-detective.md`

---

## Overview

**This is a SHORT lab — 20 to 30 minutes — and it needs no VM.** No Cloud Heights session, no simulator, no screenshot. This is a thinking lab: you take the evidence you have already collected in Weeks 5 and 6 and sort it into layers.

This is an **independent** lab.

---

## Lab Environment / Pre-Lab Check

| Component | Details |
|---|---|
| Environment | This worksheet only — nothing to start, nothing to connect to |
| Prerequisite | Week 5 labs and Week 6 Labs 01–04 |
| Screenshot | None required |

---

## Part A — The Seven-Row Table

Fill in every row. For the last column, name one **real thing you personally saw** in Weeks 5–6 that belongs at that layer.

| # | Layer name | One-line job | Real thing from Weeks 5–6 |
| --- | --- | --- | --- |
| 7 | Application | The thing you actually interact with  | Any time I interacted with the shell  |
| 6 | Presentation | Puts data in a shape the other side can use - encoding, encryption | The HTTPS traffic that made is so that I wouldn't be able to watch the contents of certain |
| 5 | Session | Starts, holds and cleanly ends a longer conversation. | My SSH connection, when I called on it and conversation was started then my machines was asked for a password. |
| 4 | Transport | Runs the conversation between two machines, to the right app | I saw that in TCP port 22 for SSH |
| 3 | Network | Gets a message between networks - addresses, routes | We worked with this when using commands like <ip route> and <trace route> |
| 2 | Data Link | Gets a message across one local hop. | I saw this with my VM communication with the default gateway |
| 1 | Physical | Moves raw signal - electricity, light, radio. | I don't recall personally interacting with physical hardware. |

---

## Part B — Case Files

For each case, name the layer where the problem lives, and name the evidence proving the layers **below** it were already working.

### Case File 1 — The Name That Went Nowhere

A hostname lookup fails, but pinging the machine's IP address directly succeeds.

Layer:

```
Layer 7, more specifically DNS. 
```

Evidence that the layers below were working:

```
Being able to ping the IP address shows that the machine that we want is still reachable. Its just the actual use of that hostname is causing an issue.
```

### Case File 2 — Permission Denied

`ssh` to a host returns `Permission denied` after a password prompt.

Layer:

```
This layer is application as well. It involves us interacting with the shell.
```

Evidence that the layers below were working:

```
The layers below are working as there were multiple steps that worked even though the password was incorrect. For one the machine was reachable and SSH was used TCP to communicate through port 22. This was seen as obvious as the SSH was able to prompt a question and follow up question to the shell. 
```

### Case File 3 — The Cable Story

A machine reports no link on its interface and has no address at all.

Layer:

```
I would layer 1 since there is no physical signal
```

Evidence and reasoning:

```
There are no future layers being utilized here as the first layer is where the issue is found. An IP address at layer 3 or even a local link on layer 2 show that there is nothing occurring at layer 1 or after.
```

### Case File 4 — Ping Works, The Page Does Not

`ping` to a server succeeds, but `curl http://<that server>` returns nothing useful.

Layer:

```
Layer 7
```

Evidence that the layers below were working:

```
We see that because a web request is what is not being reached that this is clearly layer 7. We have reasonable reason to believe everything before that worked. As being able to ping to a server shows that there is an IP address and the physical connection is on. Also, that there were able to securely connect, as I would assume that it is through the secure shell that a user is pining a server.
```

### Case File 5 — Wrong Neighbourhood

A machine has an address, but its default route points somewhere that cannot forward its traffic.

Layer:

```
This is a network issue; layer 7.
```

Evidence and reasoning:

```
I say this because the concept of default route is found in layer 3. This is where we deal with IP addresses and routing issues. 
```

---

## Part C — The Silent Gateway Case

In Lab 03 the Azure default gateway did not answer your ping. However, your VM had a valid default route configured, and your local communication with the Grid Beacon — the ping replies, the HTTP banner, and `TRACE ID: CF-NET-0604` — succeeded.

A failed gateway ping is one piece of evidence — not automatically proof of a gateway or network failure. But the evidence you weigh against it has to be the right kind of evidence.

The Grid Beacon at `10.60.6.4` sits on the same local subnet as your VM (`10.60.6.0/26`). Reaching it proves **local-subnet connectivity** — that traffic never crosses the default gateway, so beacon success alone cannot prove the gateway forwarded anything. Your `ip route` output proves a **default route is configured** — your VM knows where it intends to send non-local traffic — but it does not prove the gateway forwarded that traffic. The evidence that demonstrates the **default path is functioning** is successful communication with a destination outside `10.60.6.0/26`, such as the outbound internet access through NAT that you examined in Lab 04.

### Step 1 — Rule on the Case

Is the failed gateway ping enough evidence to declare a network-layer failure? Explain your answer using the other evidence you collected. In your response, distinguish between:

- evidence that proves **local-subnet connectivity**
- evidence that proves a **default route is configured**
- evidence that supports **successful off-subnet connectivity**

```
So in this example a failed gateway ping is not enough to declare a network layer failure. We see that the ability to send information in the local neighborhood is working as the beacon was able to be reached. And the ip route command providing the default gateway shows that there IS one, there is a default route through the gateway. The successful conversation with the outside destination shows that the gateway is operating as the message is able to exit the local area. 
```

### Step 2 — Name the Correct Conclusion

For each of these four results, state what it actually proves: the Grid Beacon at `10.60.6.4` answering, the default route shown by `ip route`, a successful connection to a destination outside your local subnet, and the gateway's failed ping. Then state the rule you would give a junior colleague about the difference between an observation ("the gateway did not answer my ICMP probe") and a diagnosis ("the gateway is broken"):

```
The Grid Beacon answering proves that I am able to communicate within my local area and neighborhood or < subnet>. The ip route command shows that my machine has a default route configured for traffic that needs to leave the subnet. A successful connection to an outside destination gives evidence that non-local neighborhood traffic is actually working, while the failed gateway ping only proves that the gateway did not respond to the ping. I would tell a junior colleague to separate what they observed from what they think actually caused the issue, and not to run rampid with the first conclusion that "makes sense".
```

---

## Part D — Two Models, One Job

The OSI model has seven layers. The practical TCP/IP model most engineers speak day to day has four or five.

### Step 1 — Map Them

Briefly show how the seven OSI layers collapse into the practical model:

```
The last 3 layers tend to collapse into 1 < application layer >.
```

### Step 2 — When Each Is Useful

Explain when the seven-layer vocabulary helps and when the practical model is the better tool:

```
The seven-layer vocab is useful because it allows a worker to break a network problem up into many specific areas. Thus, allowing an analyst to be able to hound down a more specific issue. The practical model, however, combines those levels in a way that more resembles how networking looks on the day to day. The first one is probably necessary when needing to investigate a large-scale issue in the workplace.
```

---

## Analysis Questions

**Analysis Question 1.** Explain the Ladder Rule using layer language. What does "test the near thing first" mean when the rungs are layers? *(Minimum 3 sentences.)*

```
So the Ladder Rule means to test the nearest thing to you before the far thing and use the results as evidence before moving on. When the rungs are layers, I can test what is working at one layer before moving toward the layer where the problem may be occurring. I also should not assume a layer is broken from one failed test.
```

**Analysis Question 2.** Why is "which layer is this?" a faster question than "what is broken?" when you are under pressure? *(Minimum 3 sentences.)*

```
Asking ourselves which layer this is faster because it allows me to narrow down where I should be looking for the problem. 
Instead of trying to figure out everything that could possibly be broken like on a broad scale. With this type of headspace, I can use the evidence I have to determine which layer needs more investigation
```

**Analysis Question 3.** Pick one case file from Part B and describe the very next command you would run to confirm your ruling, and what result would change your mind. *(Minimum 2 sentences.)*

```
I will pick the case 1 file for this question. I would run dig on the hostname to see if DNS is able to resolve the name at all. But if dig successfully returned the correct IP address, I would have to change my ruling that DNS was the issue.
```

---

## Submission Checklist

- [x] All seven rows of the OSI table completed with a real Week 5–6 anchor each (Part A)

- [x] All five case files given a layer and supporting evidence (Part B)

- [x] Silent gateway case ruled on correctly (Part C)

- [x] OSI vs. practical TCP/IP model compared (Part D)

- [x] All three Analysis Questions answered (minimum sentence counts met)

- [x] No screenshot required for this lab

- [x] This file is committed to your portfolio repo at `week-06/labs/lab-05-layer-detective.md`

---

## GitHub Commit Subsection

1. Open **Week 6 → Lab 05: Layer Detective** in the Lab Portal.
2. Fill in the worksheet fields.
3. Click **Submit to GitHub** — the Portal commits to `week-06/labs/lab-05-layer-detective.md`.

---

*CyberVisionaries Institute · Cyber Foundations · Tier I*
