# Week 2 Lab — Cybersecurity Landscape & Digital Infrastructure Overview

**Student Name:** Yuri Mondesir

**Date Completed:** 7/26/2026

**Module:** 1 — Digital Infrastructure & CLI | **Week:** 2  
**Submission Path:** `week-02/labs/lab-01-hardware-os-software-diagram.md`

---

## Overview

In this lab, you build a working mental model of the system you'll be securing throughout this course: the hardware, operating system, and software layers that make up every computer, and where the cybersecurity field fits around them. This lab has two parts. Part A connects this week's material to the CyberFoundations City map. Part B has you build and explain a diagram of how a computer's hardware, OS, and software layers interact.

**No terminal or command line is required this week** — that starts in Week 3.

---

## Lab Environment

| Component | Details |
|---|---|
| Environment | Browser-based Lab Portal (Module 1 orientation) |
| Required Materials | CyberFoundations City map; a diagram tool of your choice (hand-drawn and photographed, or any digital tool) |

**Prerequisite:** Portfolio repo created from the CyberFoundations student template in Week 1. This file is already in your repo at `week-02/labs/lab-01-hardware-os-software-diagram.md`, ready to fill in.

**New to the Lab Portal?** Watch this short walkthrough of how to find your Week 2 lab worksheet: [Accessing the Lab Worksheet — Step by Step](PASTE-VIDEO-LINK-HERE) *(~3 min)*.

---

## Part A — CyberFoundations City & the Cybersecurity Landscape

The CyberFoundations City map is your visual guide to the next 11 weeks. Each district represents a module of this course. This part connects this week's material to the map you were introduced to in Week 1.

### Step 1 — Open the Lab Portal Orientation Module

Log into the Lab Portal with your Microsoft account. From your Student Dashboard, open the **Module 1 orientation** module.

### Step 2 — Complete the Orientation Walkthrough

Work through the orientation content. It covers the same hardware/OS/software material as this week's lessons from a different angle — use it to check your understanding, not to replace the lessons.

### Step 3 — Locate This Week's District on the City Map

Open the CyberFoundations City map (introduced in Week 1, Lesson 6). Identify which district corresponds to Module 1 — Digital Infrastructure & CLI.

**District name:** Foundry Districy

```
RAM (or Random Access Memory) is considered FAST, short-term memory, which then holds what is actively in use.
```

**Why this district fits this week's topics (1–2 sentences):**

```
Linux is an open source; its code is free and allowed to be modified. It is what most web servers are built off.
```

---

## Part B — Hardware, OS, and Software Diagram

A computer is a stack of layers: physical hardware at the bottom, an operating system managing that hardware in the middle, and the software you actually use on top. This part has you draw that stack and explain it in your own words.

### Step 1 — Identify the Layers

Before drawing anything, list the three layers you'll diagram and one example of what lives at each layer.

**Hardware layer — one example component:** RAM

```
(e.g., CPU, RAM, storage — your choice)
```

**Operating system layer — name an OS:** Windows

```
(e.g., Windows, Linux, macOS)
```

**Software layer — one example application:** Word Processor

```
(e.g., a web browser, a word processor)
```

### Step 2 — Sketch Your Diagram

Sketch a simple diagram (hand-drawn and photographed, or built in any digital tool) showing how the hardware, OS, and software layers stack and interact. Arrows or labels showing "what talks to what" matter more than visual polish. If you'd like a free browser-based option instead of hand-drawing, try [draw.io](https://www.drawio.com/) — no account required to get started.

### Step 3 — Upload and Embed Your Diagram

Upload your diagram image directly into your repo's assets folder — keep it there rather than pasting it loose into this file, so all of this week's images stay together and organized.

1. Go to your portfolio repository on GitHub.com and navigate to `assets/screenshots/week-02/`.
2. Click **Add file → Upload files**, then drag in your diagram image, and give it a descriptive name (lowercase, hyphens, no spaces, no timestamps — e.g. `hardware-os-software-diagram.png`).
3. Scroll down and click **Commit changes**.
4. Click on the uploaded image's filename to open it — you'll see the image itself displayed on the page.
5. Right-click directly on the image and choose **Copy image address** (Chrome/Edge) or **Copy Image Link** (Firefox).
6. Come back to this file, open the pencil (edit) icon, and paste that link into the embed line below, in place of the placeholder:

```markdown
![Hardware/OS/software diagram](paste your copied image link here)
```

**If right-click doesn't show that option:** click the small download-arrow icon in the top-right of the image preview instead, then copy the URL from your browser's address bar.

**My Diagram:**

### Step 4 — Explain Your Diagram

In your own words — not a copied definition — explain how the three layers interact. Reference your own diagram directly.

```
The three layers interact by all relying firstly on the hardware. The hardware provides the main components that the Operating Systems build of off. It provides memory, stores and provides data for the operating system. The Operating System actually "manages" that memory and acts as the middleman between the Hardware layer and the application layer. It also contains the Kernal, which is what provides the APIs for the application layer. And lastly the application layer talks to the Kernal. Think of someone who is giving requests to the Kernel < command line > because they're creating an application. All of this is using memory from the hardware layer by the way.

```

---

## Analysis Questions

Answer each question in your own words. These questions connect what you did in Parts A and B to the bigger picture of this course.

### Analysis Question 1

If the operating system crashed on the computer you diagrammed, which layer(s) would stop working, and which (if any) would keep working? Explain your reasoning.

```
Microsoft word is an example of a process that sits on the application layer. The applications of the software layer would most likely stop working as they rely on the operating system by giving it commands. I believe the hardware layer would continue to work as it does not rely on the other layers to simply exist.
```

### Analysis Question 2

Pick one piece of software you use daily. Trace it down through the OS to the hardware it ultimately depends on. What would happen to that software if the hardware layer failed?

```
An example is Microsoft Excel. The Operating System layer is Windows. If the hardware layer failed, I believe the very device < my computer > would fail to open.
```

### Analysis Question 3

Explain, in your own words, why a cybersecurity professional needs to understand all three layers — hardware, OS, and software — rather than just the software layer where most visible attacks (like phishing emails) happen.

```
A cybersecurity professional needs to understand all these layers for a couple reasons. The complete understanding of what all these layers do can aid a cybersecurity professional in analyzing what vulnerabilities can be exploited. Not just in the software layer, but from the ground up. If an attacker is able to place a form of malware in the hardware, they are then able to compromise the rest of the layers fairly easily.
```

---

## Lab Report Questions

Answer each question in complete sentences.

**1. What is the cybersecurity landscape, and why does it matter to someone starting this course?**

```
The cybersecurity landscape is the entire essence of all involved parties concerning cyber security. You have the attackers, the infrastructure that a professional is trained to protect, the professionals themselves and the users who use sed infrastructures. 
```

**2. Which CyberFoundations City district did you identify in Part A, and how does its theme connect to the hardware/OS/software material in Part B?**

```
The Foundry District. The correlation from the theme to the material in Part B is that we are building the foundation of knowledge of what is actually happening under the hood!
```

**3. Of the three layers (hardware, OS, software), which one do you think is hardest to secure, and why?**

```
I think the operating system might be the hardest to secure is the software layer. I say this because in addition to the hackers being present, there is now a need to monitor the uses of everyday users. Those user choices are ones that cannot be controlled, nor can you be assured that the user can understand their current situation.
```

---

## Submission Checklist

- [x] Lab Portal Module 1 orientation completed

- [x] District identified and explained

- [x] Hardware, OS, and software layer examples listed

- [x] Diagram uploaded to `assets/screenshots/week-02/` and embedded using a copied image link (not pasted loose, not a local file path)

- [x] Diagram explanation written in your own words (minimum 3 sentences)

- [x] All three Analysis Questions answered (minimum sentence counts met)

- [x] All three Lab Report Questions answered in complete sentences

- [x] This file is committed to your portfolio repo at `week-02/labs/lab-01-hardware-os-software-diagram.md`
