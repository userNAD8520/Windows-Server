---
title: Windows Server Midterm — Plain-English Notes, Analogies & Draw Prompts
week: midterm
tags: [windows-server, plain-english, feynman, analogies, active-directory, hyper-v, storage]
---

# Windows Server Midterm — Plain-English Notes, Analogies & Draw Prompts

> **📘 How to use this file:** For each topic you get three things —
> 1. **📝 In my own words** — a human, informal definition (write this in your notebook).
> 2. **🧠 Analogy** — a Feynman-style everyday comparison (say it out loud to lock it in).
> 3. **🖼️ Draw prompt** — paste this into Gemini to get a hand-drawn reference image, then redraw it.
>
> All prompts use the same style: **black marker on a whiteboard, simple and minimal, easy to redraw by hand.**

---

## AD DS (Active Directory Domain Services)

### 1. What is AD DS? (the three jobs)

**📝 In my own words:** AD DS is Windows' master list of every user, computer, and group, plus the security guard that checks who you are and what you're allowed to touch. It does three jobs: **STORE** everyone's identity, **AUTHENTICATE** you (prove it's really you), and **AUTHORIZE** you (decide what you can access).

**🧠 Analogy:** A VIP club. Store = the guestbook. Authenticate = the bouncer checks your ID and hands you a ticket. Authorize = the rules list (ACL) + your badge (SID) decide which rooms you can enter.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard diagram, black marker, simple minimal style, easy to redraw by hand.
Title at top: "AD DS = The VIP Club".
Three numbered sections stacked vertically:
1. STORE — draw a small notebook labeled "Guestbook" with two handwritten lines "Alice Moore" and "PC-LAB-07", and a note "the file is ntds.dit".
2. AUTHENTICATE — draw a stick-figure bouncer checking an ID card, with a speech bubble: "You're Alice! Here's your TGT ticket".
3. AUTHORIZE — draw a VIP room door, a list labeled "ACL = rules", small badges labeled "SIDs = groups", and a checkmark "ACCESS GRANTED".
Use boxes, arrows, and short handwritten labels only. No color except black marker.
```

### 2. Why do we need domain services?

**📝 In my own words:** In a workgroup, every computer keeps its OWN list of users — so Alice exists 300 times with 300 passwords. With AD DS, Alice exists **once**, and every computer trusts that one central list. One password, one place to disable, one place to audit.

**🧠 Analogy:** A workgroup is every door having its own separate lock and key. AD DS is **one master key card** that opens every door in the building — and when you're fired, they deactivate that one card and you're locked out everywhere.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
Two panels side by side:
LEFT panel — three doors, each with a different key, labeled "workgroup: 300 separate keys".
RIGHT panel — one key card labeled "ONE account" opening many doors, labeled "domain: one key opens all".
Short arrows and handwritten labels only.
```

### 3. AD DS Database Partitions

**📝 In my own words:** The AD database (`ntds.dit`) is split into 4 sections, and each section gets copied to a different set of servers. **Schema** (the rulebook of what fields exist) and **Configuration** (the map of the forest) go to EVERY server. **Domain** (the actual users/computers) stays in its own domain. **Application** (app data) goes only where you choose.

**🧠 Analogy:** A company filing cabinet with 4 drawers. Two drawers (the rules + the company map) get photocopied to every office. One drawer (employee files) stays in its own office. One drawer (special app files) goes only to the offices that need it.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
Draw a filing cabinet with 4 labeled drawers: "Schema", "Configuration", "Domain", "Application".
Arrows: Schema and Configuration → "photocopied to ALL offices". Domain → "this office only". Application → "chosen offices only".
Short handwritten labels, no color.
```

### 4. Physical components: Sites & Replication

**📝 In my own words:** A **site** is just a physical location with fast internet (one office building). Within a site, servers sync instantly (fast, no compression). Between sites, they sync on a schedule over the slower link (compressed, timed). Sites also make users log in to the **nearest** server.

**🧠 Analogy:** Two office branches. People in the SAME office talk face-to-face constantly. Between Toronto and Montreal they send a courier on a fixed schedule to save bandwidth. And you always walk to the desk in YOUR building, not the other city.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
Two office buildings connected by a dashed line labeled "site link = scheduled courier".
Inside each building, two stick figures with a label "instant, uncompressed" (within a site).
On the dashed line, label "compressed, scheduled".
Handwritten labels only, no color.
```

### 5. Logical components: Domains, Trees, Forests, OUs

**📝 In my own words:**
- **OU** = a folder inside a domain to group users and apply rules (GPO).
- **Domain** = one neighborhood of users with its own rules.
- **Tree** = domains that share the same last name (contiguous namespace).
- **Forest** = the whole city — the ultimate security wall that everything shares.

**🧠 Analogy:** Forest = a walled city (one shared wall = the security boundary). Tree = streets named in the same family style. Domain = a neighborhood. OU = the filing folders inside a neighborhood's office.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
Draw a big walled city labeled "Forest (security boundary)".
Inside it, two neighborhoods labeled "Domain: contoso.com" and "Domain: emea.contoso.com".
A street sign between them reads "contiguous namespace = Tree".
Inside one neighborhood, a small folder labeled "OU".
No color, handwritten labels only.
```

### 6. FSMO Roles

**📝 In my own words:** Even though AD normally lets any server make changes, FIVE special jobs can only be done by ONE server at a time (so two people don't edit the same thing). **2 are forest-wide** (Schema, Domain Naming), **3 are per-domain** (RID, PDC Emulator, Infrastructure).

**🧠 Analogy:** A company where only ONE person holds each special key: one signs all contract changes (Schema), one creates new departments (Domain Naming), one hands out employee ID numbers (RID), one is the emergency boss + timekeeper (PDC Emulator), and one updates the cross-office directory (Infrastructure).

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
Two columns:
LEFT column header "Forest-wide (2)": a key labeled "Schema Master" and a key labeled "Domain Naming Master", each with a "only ONE holder" tag.
RIGHT column header "Per-domain (3)": keys labeled "RID Master", "PDC Emulator", "Infrastructure Master", each with "only ONE holder".
Draw a small person icon holding each key. No color.
```

### 7. Global Catalog

**📝 In my own words:** A condensed, read-only phone book that has EVERY person from EVERY domain, but only their name + a few key fields (not the full file). Used to find anyone fast, and to log you in (it knows which domain you belong to and your universal group memberships).

**🧠 Analogy:** A master index card at the front desk listing every employee's name + department + extension — not their full HR file. If the front desk is closed (GC down) in a multi-office company, normal employees can't check in (log on), but managers still can.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
A front desk with a big open index book labeled "Global Catalog".
On the book: "everyone's name + dept + extension — NOT the full file".
Arrows from the book to several small folders labeled "Domain A", "Domain B", "Domain C".
No color, handwritten labels.
```

### 8. IGDLA Model

**📝 In my own words:** The clean way to hand out permissions: put people (**Identity**) into a **Global group** (their job role), put that Global group into a **Domain Local group** (the resource's access list), and give the permission to the Domain Local group. Never give a user permission directly.

**🧠 Analogy:** A membership pipeline. You join a club (Global group = "Sales Team"). The club gets added to a specific room's VIP list (Domain Local group = "who can enter the Sales room"). That list grants you access. To add a person, just add them to the club — done.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
A left-to-right assembly line with four boxes and arrows:
"Identity (people)" → "Global group (Sales Team)" → "Domain Local group (Sales room access list)" → "Access to folder".
Label the last box "permission lives here".
No color, handwritten labels.
```

### 9. Security Identifier (SID)

**📝 In my own words:** Every user/group/computer gets a permanent ID number. Windows always checks the **number**, never the name. Rename yourself → same number, permissions follow. Delete + recreate → new number, old access lost.

**🧠 Analogy:** Your employee badge number (or SSN). The door scanner reads your number, not your name. If HR deletes and recreates you as a "new hire," you get a new number and lose your old door access.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
A badge with a big ID number on it (label it "SID"), being scanned at a door.
A caption next to it: "scanner reads the NUMBER, not the name".
Small note: "rename = same number; delete + recreate = new number".
No color, handwritten labels.
```

---

## Hyper-V & Hypervisors

### 10. What is Hyper-V? (hypervisor types)

**📝 In my own words:** Hyper-V is Windows' built-in tool that turns ONE physical computer into many virtual computers (VMs). A hypervisor is the manager that splits the hardware. **Type 1** runs directly on the hardware (Hyper-V, ESXi). **Type 2** runs as a program on top of an OS (VirtualBox, VMware Workstation).

**🧠 Analogy:** Type 1 = building your hotel directly on empty land (the building IS the structure). Type 2 = renting an office inside someone else's building, then subletting rooms inside it — an extra layer, less efficient but convenient.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
Two panels:
LEFT "Type 1 (bare-metal)": Hardware → Hypervisor → VM1, VM2 (direct stack of boxes).
RIGHT "Type 2 (hosted)": Hardware → Host OS → Hypervisor app → VM3, VM4 (one extra layer).
Arrows between boxes, handwritten labels, no color.
```

### 11. Hyper-V Virtual Switches (Internal / External / Private)

**📝 In my own words:** A virtual switch connects VMs to networks. **External** = plugged into a real network card (VMs reach the internet). **Internal** = VMs + the host can talk, but NOT outside. **Private** = only VMs can talk, not even the host.

**🧠 Analogy:** External = a door to the street. Internal = an intercom inside the house (family + guests talk, no one outside). Private = a sealed room with no doors (only the people already inside can talk).

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
Three rooms:
1. A room with a door to a cloud labeled "street/internet" → label "External".
2. A room with an intercom to a box labeled "host" → label "Internal".
3. A sealed box with no doors → label "Private (VMs only)".
Handwritten labels, no color.
```

### 12. Checkpoints

**📝 In my own words:** A checkpoint is a save point of a VM — its disk, settings, and maybe memory — that you can roll back to. Take one before a risky change; if it breaks, revert. It's **not** a backup.

**🧠 Analogy:** A video-game save state. Save before the boss fight (risky patch). If you die (the change breaks), reload the save. It lives on the same machine, so it won't save you if the whole console dies.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
A game "SAVE" screen with a save slot labeled "before patch".
A "RELOAD" arrow pointing back to it.
Caption below: "checkpoint = save state, NOT a backup".
No color, handwritten labels.
```

---

## Storage

### 13. iSCSI Storage Server

**📝 In my own words:** iSCSI sends hard-drive commands over the network, so a server can use a disk that's physically in another machine as if it were plugged in locally. The storage box is the **target**; the server connecting is the **initiator**. The server formats its own filesystem on it (block-level).

**🧠 Analogy:** A very long cable to a warehouse of raw shelves. The warehouse (target) hands you raw shelf space (LUNs); you (initiator) arrange it however you want (format it).

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
A server labeled "Initiator" connected by a long cable (labeled "iSCSI over Ethernet") to a storage box labeled "Target".
Inside the storage box, draw two shelves labeled "LUN 0" and "LUN 1".
Caption: "server formats its own filesystem on the LUN".
No color, handwritten labels.
```

### 14. Storage Pools

**📝 In my own words:** Dump all your physical disks into one big pool, then carve virtual disks (Storage Spaces) out of that pool with a chosen safety level (Simple = no safety, Mirror = duplicate, Parity = rebuild-able). Format those into drives.

**🧠 Analogy:** A big bucket of LEGO bricks (physical disks). Pour them in, then build specific models (Storage Spaces) from the bucket. Add more bricks = build bigger things.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
A big bucket labeled "Storage Pool" filled with small brick shapes labeled "disks".
Arrows from the bucket to two built models labeled "Mirror" and "Parity".
Caption: "pool = bucket of disks; space = the model you build".
No color, handwritten labels.
```

### 15. RAID (0, 1, 5, 10)

**📝 In my own words:** RAID combines disks for speed and/or safety. **0** = split across disks (fast, no safety). **1** = exact copy on a second disk (safe). **5** = data + a parity note across 3 disks (survives one death). **10** = copy THEN split (fast + safe, needs 4).

**🧠 Analogy:** Writing your homework across pages. RAID 0 = write half the answer on two pages (lose one = fail). RAID 1 = photocopy the whole thing. RAID 5 = write answers + a "checksum cheat note" so you can rebuild if one page is lost. RAID 10 = photocopy THEN split.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
Four small diagrams in a 2x2 grid:
"RAID 0" two boxes labeled A1 A2 (split, no copy).
"RAID 1" two identical boxes labeled A A (mirror).
"RAID 5" three boxes, one labeled "parity".
"RAID 10" four boxes grouped in two mirrored pairs.
Short labels only, no color.
```

### 16. Enterprise Storage: DAS vs NAS vs SAN

**📝 In my own words:** Three ways to connect storage. **DAS** = drive plugged straight into one server. **NAS** = a shared folder box on the network (file-level, SMB/NFS). **SAN** = raw block storage delivered over a network (iSCSI/Fibre Channel); servers see it as local.

**🧠 Analogy:** DAS = your own closet. NAS = a shared library where anyone borrows books (files). SAN = a warehouse that hands you raw shelves to arrange yourself.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
Three panels:
"DAS" — one server with a direct-attached disk.
"NAS" — several client figures pointing to one box labeled "files (SMB/NFS)".
"SAN" — servers pointing to a network cloud, then to a box labeled "raw blocks (iSCSI/FC)".
Handwritten labels, no color.
```

### 17. Storage Layout & Disk Requirements

**📝 In my own words:** Planning how many disks and which RAID you need. Minimums: **0 = 2, 1 = 2, 5 = 3, 10 = 4**. Usable space: **0 = 100%, 1 = 50%, 5 = N−1, 10 = 50%**. Match the need: OS → RAID 1, database → RAID 10, files → RAID 5, scratch → RAID 0.

**🧠 Analogy:** Budgeting for insurance. You decide how many copies of your data to keep and how much "premium" (extra disks) you're willing to pay. More safety = more disks.

**🖼️ Draw prompt:**
```text
Hand-drawn whiteboard, black marker, simple minimal style.
A simple checklist table:
Row "RAID 0" → "min 2 disks" → "100% usable".
Row "RAID 1" → "min 2 disks" → "50% usable".
Row "RAID 5" → "min 3 disks" → "N-1 usable".
Row "RAID 10" → "min 4 disks" → "50% usable".
A note at the bottom: "match RAID to need: OS→1, DB→10, files→5, scratch→0".
No color, handwritten labels.
```
