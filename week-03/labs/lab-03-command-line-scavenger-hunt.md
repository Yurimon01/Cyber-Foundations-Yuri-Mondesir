# Week 3 Lab 03 — Command Line Scavenger Hunt (CLI Simulator)

**Student Name:** Yuri Mondesir

**Date Completed:** 08/06/2026

**Module:** 1 — Digital Infrastructure & CLI | **Week:** 3  
**Submission Path:** `week-03/labs/lab-03-command-line-scavenger-hunt.md`

---

## Overview

Labs 01 and 02 walked you through each command step by step. This lab is Week 3's wrap-up challenge: a deeper, more independent folder structure with three hidden files to track down, using the navigating and reading commands from Lessons 3A/3B, the creating and organizing commands from Lesson 3C, and your own judgment about when to ask for help. There's less hand-holding here on purpose — this is your chance to prove to yourself that the blinking cursor from the start of Lesson 3A doesn't intimidate you anymore.

**Nothing here can break anything real.** Same consequence-free CLI Simulator as Labs 01 and 02. Getting "lost" in the folder tree costs you nothing but a few extra `cd` moves.

---

## Lab Environment / Pre-Lab Check

| Component | Details |
|---|---|
| Environment | CyberFoundations CLI Simulator (browser-based, inside the Lab Portal) |
| Shell | Your choice — bash or PowerShell |
| Prerequisite | Labs 01 and 02 completed |

**Before you start:** log into the Lab Portal, open **Week 3 → CLI Simulator**, and load the **"Foundry District Archive Room"** scenario. This tree goes several folders deeper than Labs 01 and 02, and includes a few similarly-named folders on purpose — read carefully before you `cd` into anything.

---

## Part A — The Hunt

Find all three of the following, hidden at different depths in the Archive Room tree:

- A file related to a **shift log**
- A file related to a **maintenance note**
- A file related to a **supply inventory**

For each one, use `pwd`/`Get-Location` and `ls`/`dir` as many times as you need while you search, then record the **full path** once you find it.

Shift log file — full path once found:

```
archivist@archive-room:/home/archivist/operations/ops-log$ ls
```

Maintenance note file — full path once found:

```
archivist@archive-room:/home/archivist/records/records-2025$

```

Supply inventory file — full path once found:

```
archivist@archive-room:/home/archivist/records/records-2024$

```

---

## Part B — Read and Report

For each of the three files you found in Part A, use `cat`/`type` to read it and record what it says.

Shift log contents:

```
Shift Log - Foundry District Archive Room
07:00 - Archive opened, no incidents overnight.
15:00 - Routine filing complete.
```

Maintenance note contents:

```
Maintenance Note - Conveyor belt 3 serviced, next check due in 90 days.
```

Supply inventory contents:

```
Supply Inventory - Q4 2024
Gloves - 400 units
Masks - 250 units
Tape - 60 rolls
```

---

## Part C — Organize Your Findings

Now that you've located and read all three files, clean up after yourself the way a professional would — don't leave your findings scattered across the tree.

### Step 1 — Create a Sorted-Findings Folder

Create a new folder called `sorted-findings` in your home directory.

Command you ran:

```
cd ..
mkdir sorted-findings
```

### Step 2 — Move All Three Files Into It

Move the shift log, maintenance note, and supply inventory files — the same three you found in Part A — into `sorted-findings`.

Commands you ran:

```
mv /home/archivist/operations/ops-log/shift-log.txt sorted-findings/

mv /home/archivist/records/records-2025/maintenance-note.txt sorted-findings/

mv /home/archivist/records/records-2024 supply-inventory.txt/

```

### Step 3 — Confirm the Move

List the contents of `sorted-findings` to confirm all three files are now there.

Command you ran:

```
archivist@archive-room:/home/sorted-findings$ ls
```

Output:

```
maintenance-note.txt  shift-log.txt  supply-inventory.txt
```

---

## Part D — When You Get Stuck

At some point in the Archive Room, you'll likely run across a command or folder name you don't immediately recognize.

### Step 1 — Ask the Terminal

When that happens, use `--help`, `man`, or `Get-Help` instead of guessing. Record what you looked up and what you learned.

Command or term you looked up:

```
man mv
```

What the help text (or the folder's contents) told you:

```
It explains that this is the move command or < rename > and it moves from an item from a source location to a new destination.
```

### Step 2 — Describe a Wrong Turn

Everyone takes at least one wrong turn in a tree this size. Describe one moment you ended up somewhere unexpected, and how you used `pwd`/`Get-Location` and `cd ..` to recover.

```
I took a couple wrong turns. One of them had to be using the command < cd.. > too many times, I ended up initially creating the sorted-findings button in the root folder instead of the home folder. Pwd helped me see that this new folder I created was sitting along side the home directory instead of inside of it.
```

---

## Analysis Questions

### Analysis Question 1

Which of the three files in Part A took the longest to find, and what was it about the tree's structure (depth, similarly-named folders, etc.) that made it harder?

```
I would say the shift-log.txt took the longest to find. As my mind naturally assumed a log would be in some form of records folder. And from there, there were additional record files that branch from the OG records file.
```

### Analysis Question 2

Compare how you felt starting this lab to how you felt at the very start of Lesson 3A, looking at a blank blinking cursor for the first time. What changed?

```
I won't like it all feels way less intimidating. Pwd and Ls are commands that just make navigating through folders feel way less scary. There is less risk knowing that I can always check my work before moving forward.
```

### Analysis Question 3

Week 4 moves from managing your own files to controlling who's allowed to do what to them — permissions — plus your first look at what a virtual machine is. Based on everything you've practiced this week, what's one thing you're curious about or looking forward to?

```
I am curious to how simple changing permissions will be. I am curious as to whether it will be something that clicks to me like this lesson here.
```

---

## Submission Checklist

- [x] All three target files located, with full paths recorded (Part A)

- [x] All three target files read and their contents recorded (Part B)

- [x] `sorted-findings` folder created and all three files moved into it, confirmed with a listing (Part C)

- [x] At least one command or term looked up with `--help`/`man`/`Get-Help`, with what you learned recorded (Part D, Step 1)

- [x] One wrong-turn moment described, including how you recovered (Part D, Step 2 — minimum 2 sentences)

- [x] All three Analysis Questions answered (minimum sentence counts met)

- [x] This file is committed to your portfolio repo at `week-03/labs/lab-03-command-line-scavenger-hunt.md`

---

## GitHub Commit Subsection

Same mechanism as Labs 01 and 02: fill out this lab's worksheet in the **CyberFoundations Lab Portal** (Week 3 → Lab 03) and click **Submit to GitHub** — the Portal commits the completed file to `week-03/labs/lab-03-command-line-scavenger-hunt.md` automatically. No manual typing or commit needed.

**📌 Optional:** a CLI Simulator session screenshot can be added the same way as Labs 01 and 02 — upload to `assets/screenshots/week-03/`, then right-click the uploaded image and choose **Copy image address**/**Copy Image Link** to embed it — but it isn't required and won't affect your grade.

---

*CyberVisionaries Institute · Cyber Foundations · Tier I*
