---
title: Windows Server Midterm — Mock Exam Answer Key & Analysis (Teacher's Scope)
week: midterm
tags: [windows-server, answer-key, active-directory, hyper-v, storage, raid]
---

# Windows Server Midterm — Mock Exam: Answer Key & Analysis

> **🔑 How to use this key:** Grade strictly first. Select-all questions score only if your set is *exactly*
> correct (no missing, no extra). Then read the wrong-option lines for every question you missed or
> guessed — that's where the learning is. Finally, fill the tracking table and drive the restudy list.

---

## Part A — Active Directory Domain Services

### Question 1
**Answer: C (a domain controller).**
- **A — wrong:** A member server does not run AD DS and holds no NTDS.dit.
- **B — wrong:** DNS provides name resolution, not the directory database or the KDC.
- **C — correct:** The DC hosts **NTDS.dit** and acts as the **KDC** for Kerberos.
- **D — wrong:** The Global Catalog is a *feature of* a DC, not a standalone role.

### Question 2
**Answer: B.**
- **A — wrong:** AD DS does not increase network throughput.
- **B — correct:** The primary benefit is **centralized identity and a single point of administration**.
- **C — wrong:** AD DS does not provide automatic hardware failover (that's clustering/NLB).
- **D — wrong:** AD DS is not antivirus.

### Question 3
**Answer: C (Domain partition).**
- **A — wrong:** The Schema partition defines classes and attributes.
- **B — wrong:** The Configuration partition holds forest topology.
- **C — correct:** The **Domain** partition holds one domain's users, computers, and groups.
- **D — wrong:** Application partitions hold app-specific data.

### Question 4
**Answer: B (Configuration partition).**
- **A — wrong:** Schema = object classes/attributes.
- **B — correct:** The **Configuration** partition stores forest topology — sites, site links, and DCs.
- **C — wrong:** Domain partition = domain objects (users/groups).
- **D — wrong:** Application partitions = app-specific data.

### Question 5
**Answer: B.**
- **A — wrong:** "Uncompressed and change-notified" describes **intrasite** replication.
- **B — correct:** Intersite replication is **compressed and scheduled** over site links to save WAN bandwidth.
- **C — wrong:** Intersite replication is *less* frequent (scheduled, default 180 min).
- **D — wrong:** Intersite replicates all changes, not just schema.

### Question 6
**Answer: B.**
- **A — wrong:** A GC server is fine; it doesn't force remote authentication.
- **B — correct:** If the user's **subnet isn't mapped to the correct site**, the client locates a DC in the wrong (distant) site.
- **C — wrong:** Functional level doesn't affect which DC a client uses.
- **D — wrong:** Site-link cost affects the *replication path*, not client DC selection.

### Question 7
**Answer: C (Forest).**
- **A — wrong:** A domain is a replication/management boundary, not the ultimate security boundary.
- **B — wrong:** An OU is not a security boundary at all.
- **C — correct:** The **forest** is the ultimate security boundary (shared schema + configuration).
- **D — wrong:** A tree is a namespace grouping, not the security boundary.

### Question 8
**Answer: B.**
- **A — wrong:** Same tree requires a *contiguous* namespace; `contoso.com` and `fabrikam.com` are discontiguous.
- **B — correct:** Discontiguous namespaces live as **separate trees in the same forest**.
- **C — wrong:** They can (and often do) share one forest.
- **D — wrong:** They are not required to be a single domain.

### Question 9
**Answer: C (11).**
- **A — wrong:** 5 is the number of role *types*, not holders.
- **B — wrong:** 8 is the count for a two-domain forest (2 + 3×2).
- **C — correct:** 2 forest-wide + (3 × 3 domains) = **11**.
- **D — wrong:** 15 doesn't fit the 2 + 3N formula for any whole N.

### Question 10
**Answer: B (PDC Emulator).**
- **A — wrong:** RID Master hands out RID pools for SID creation.
- **B — correct:** The **PDC Emulator** handles password changes, account lockouts, and time sync.
- **C — wrong:** Infrastructure Master updates cross-domain object references.
- **D — wrong:** Schema Master handles schema changes.

### Question 11
**Answer: B.**
- **A — wrong:** In a multi-domain forest, ordinary users **cannot** log on without the GC.
- **B — correct:** Without the GC, universal-group membership can't be enumerated, so ordinary users can't log on — but **Domain Admins can** (built-in fallback).
- **C — wrong:** Logons *are* affected, not just searches.
- **D — wrong:** Replication continues; the GC is not required for replication itself.

### Question 12
**Answer: B.**
- **A — wrong:** A Domain Local group cannot nest into a Global group (direction is reversed).
- **B — correct:** IGDLA nests a **Global group inside a Domain Local group**.
- **C — wrong:** Global *can* go into Universal, but "only" is wrong, and that's not the IGDLA chain.
- **D — wrong:** A Domain Local group cannot be a member of a Universal group.

### Question 13
**Correct set: A, B, C, E.**
- **A–C, E — correct:** Centralized accounts, SSO, Group Policy, and OU-scoped delegation are all AD DS benefits.
- **D — wrong:** "Each workstation keeps its own database" describes the *workgroup* model, not a benefit.

### Question 14
**Correct set: A, B, C, D.**
- **A–D — correct:** Schema (forest-wide), Configuration (forest-wide), Domain (domain-wide), Application (scoped subset).
- **E — wrong:** Not all partitions go to every DC — Domain is domain-wide and Application is a scoped subset.

### Question 15
**Correct set: A, B, C, D.**
- **A–D — correct:** Forest = security boundary + one schema; tree = contiguous namespace; OU = delegation + GPO; forest can hold discontiguous namespaces.
- **E — wrong:** An OU is **not** a security boundary.

### Question 16
**Correct set: A, B, C, D.**
- **A–D — correct:** Sites group subnets; intrasite = change-notified/uncompressed; intersite = compressed/scheduled; subnets map clients to the nearest DC.
- **E — wrong:** A site is **physical** (subnets/location), not a logical grouping like a domain.

### Question 17
**Correct set: A, B, C, D.**
- **A–D — correct:** Two forest-wide roles, three domain-wide roles, first DC holds all five, 2 + 3N total.
- **E — wrong:** Only **three** of the five roles exist per domain; two are forest-wide.

### Question 18
**Correct set: A, B, C, D.**
- **A–D — correct:** Partial copy of all objects, subset of attributes, enables searches, supplies universal-group membership at logon.
- **E — wrong:** The GC holds a **subset** of attributes, not a full copy of every attribute.

### Question 19 — model answer
AD DS is Microsoft's directory service that stores network objects (users, computers, groups) in a centralized, hierarchical, replicated database. It **authenticates** via Kerberos (the DC acts as the KDC and issues tickets, with NTLM as fallback) and **authorizes** via ACLs and security groups that grant permissions to SIDs.

**Rubric (3 pts):** (1) describes a directory service storing objects; (2) authentication = Kerberos/KDC; (3) authorization = ACLs/groups/SIDs.

### Question 20 — model answer
The four partitions are: **Schema** (defines classes/attributes; forest-wide), **Configuration** (forest topology; forest-wide), **Domain** (one domain's objects; domain-wide), and **Application** (app-specific data; replicated to a chosen subset of DCs).

**Rubric (3 pts):** (1) names all four; (2) Schema + Configuration = forest-wide; (3) Domain = domain-wide and Application = scoped subset.

### Question 21 — model answer
A **transfer** is a graceful move performed while both DCs are online (via `Move-ADDirectoryServerOperationMasterRole` or `ntdsutil transfer`). A **seize** is a forceful take-over used when the role holder is permanently failed (via `ntdsutil seize`). After a seize, the old DC must **never** be brought back online — you reinstall it.

**Rubric (3 pts):** (1) transfer = graceful/online; (2) seize = forceful/failed holder; (3) old DC reinstall/not returned.

### Question 22 — model answer
The Global Catalog has two roles: (1) it enables **forest-wide searches** by holding a partial replica of every domain, so queries resolve without contacting each domain; and (2) it **facilitates logins** by resolving which domain a UPN account lives in and supplying the user's **universal group membership** for the security token.

**Rubric (3 pts):** (1) searches; (2) logins/UPN resolution; (3) universal group membership.

### Question 23 — model answer
IGDLA = **Identity → Global → Domain Local → Access**. User accounts (Identity) go into **Global groups** (role grouping within their own domain); Global groups nest into **Domain Local groups** (resource access); permissions (**Access**) are granted to the Domain Local group. This keeps permission assignment scalable and consistent. In a **multi-domain** forest, insert a **Universal** group (I-G-U-DL-A) to bridge Global groups across domains.

**Rubric (3 pts):** (1) what each letter stands for; (2) explains the purpose (single, scalable place to grant access); (3) Universal group for multi-domain.

### Question 24 — model answer
The hierarchy is **Forest → Domain Tree → Domain → OU → Object**. An **OU** is a container used to organize objects so administration can be **delegated** to a scoped subset and **Group Policy** can be applied to just that subset.

**Rubric (3 pts):** (1) correct top-to-bottom order; (2) OU = container; (3) OU's two purposes (delegation + GPO).

---

## Part B — Hyper-V & Hypervisors

### Question 25
**Answer: B.**
- **A — wrong:** Although Windows is installed, enabling Hyper-V puts the hypervisor *beneath* the OS.
- **B — correct:** Windows runs **under** the Hyper-V hypervisor, so it is **Type 1 (bare-metal)**.
- **C — wrong:** VMware Workstation is Type 2; Hyper-V is not.
- **D — wrong:** The hypervisor runs in privileged/kernel mode, not user mode.

### Question 26
**Answer: B.**
- **A — wrong:** A checkpoint is a rollback point, **not** a backup.
- **B — correct:** A **production checkpoint** uses guest VSS and is application-consistent.
- **C — wrong:** A standard checkpoint captures memory and is crash-consistent, not app-consistent.
- **D — wrong:** Checkpoints live on the same storage and do **not** protect against host/storage failure.

### Question 27
**Answer: C (External).**
- **A — wrong:** Private connects VMs only.
- **B — wrong:** Internal connects VMs + host but has no physical NIC (no internet).
- **C — correct:** External binds a physical NIC, giving VMs LAN/internet access.
- **D — wrong:** "NAT-only" is not a switch type; NAT is applied to an Internal switch.

### Question 28
**Answer: B (Production checkpoint).**
- **A — wrong:** Standard checkpoints capture memory (crash-consistent).
- **B — correct:** Production checkpoints use VSS (application-consistent) and don't capture memory.
- **C — wrong:** A "differencing checkpoint" isn't a checkpoint type (the differencing disk is the mechanism).
- **D — wrong:** A "full checkpoint" isn't a distinct type.

### Question 29
**Correct set: A, B, C, D.**
- **A–D — correct:** Type 1 = bare-metal; Type 2 = on a host OS; Hyper-V/ESXi = Type 1; VirtualBox/Workstation = Type 2.
- **E — wrong:** Type 1 is generally faster and better isolated, not Type 2.

### Question 30
**Correct set: A, B, C, D.**
- **A–D — correct:** External binds a NIC; Internal = VMs + host; Private = VMs only; only External needs a physical NIC.
- **E — wrong:** Internal has no physical NIC, so VMs get **no** direct internet access.

### Question 31 — model answer
A **Type 1 (bare-metal)** hypervisor runs directly on the hardware (e.g., Hyper-V, ESXi) and is used in production/datacenters for performance and isolation. A **Type 2 (hosted)** hypervisor runs as an application on a host OS (e.g., VirtualBox, VMware Workstation) and is used for desktop testing and convenience.

**Rubric (3 pts):** (1) Type 1 bare-metal + example; (2) Type 2 hosted + example; (3) a use case for each.

### Question 32 — model answer
An **Internal** switch connects VMs to each other **and** to the host (but has no physical NIC, so no external access). A **Private** switch connects **VMs only** — even the host is excluded. The single difference is whether the host participates.

**Rubric (3 pts):** (1) Internal = VMs + host; (2) Private = VMs only; (3) host participation is the distinction.

---

## Part C — Storage: iSCSI, Storage Pools & RAID

### Question 33
**Answer: B (the target).**
- **A — wrong:** The initiator *connects to* the LUNs; it doesn't present them.
- **B — correct:** The **target** (iSCSI Storage Server) presents the LUNs.
- **C — wrong:** An IQN is an identifier, not a component that presents LUNs.
- **D — wrong:** The switch is just transport.

### Question 34
**Answer: B.**
- **A — wrong:** SMB is file-level (NAS), not block-level.
- **B — correct:** Block-level means the connecting server **formats its own filesystem** on the LUN.
- **C — wrong:** "The storage device owns the filesystem" describes *file-level* storage.
- **D — wrong:** NFS is file-level, not block-level.

### Question 35
**Answer: B.**
- **A — wrong:** A virtual disk with a resiliency setting is a **Storage Space**, not a pool.
- **B — correct:** A **pool** is a group of physical disks aggregated into one pool of capacity.
- **C — wrong:** A formatted volume is created *from* a space.
- **D — wrong:** Pools are software-defined; they don't require a hardware RAID controller.

### Question 36
**Answer: A (RAID 0).**
- **A — correct:** RAID 0 is striping with **no redundancy**.
- **B — wrong:** RAID 1 is mirroring (redundant).
- **C — wrong:** RAID 5 uses parity (redundant).
- **D — wrong:** RAID 10 is mirror + stripe (redundant).

### Question 37
**Correct set: A, B, C, D.**
- **A–D — correct:** Aggregate mixed disks, grow by adding disks, resilience without hardware RAID, and tiering are all pool benefits.
- **E — wrong:** Storage pools are software-defined and do **not** require a hardware RAID controller.

### Question 38
**Correct set: A, B, C, D.**
- **A–D — correct:** RAID 0 = no fault tolerance; RAID 1 = 2 disks; RAID 5 = 3 disks, 1 failure; RAID 10 = 4 disks.
- **E — wrong:** RAID 5 provides **N−1** usable capacity, not 100%.

### Question 39 — model answer
The **iSCSI target** is the storage server that *provides/exposes* the LUNs; the **iSCSI initiator** is the client/server that *connects to* the target and consumes the LUNs. iSCSI is **block-level** because it presents raw blocks, and the connecting server (initiator) formats its own filesystem (NTFS/ReFS) on the LUN.

**Rubric (3 pts):** (1) target provides LUNs; (2) initiator connects; (3) block-level = server owns the filesystem.

### Question 40 — model answer
**RAID 0** = striping, no fault tolerance, min 2 disks. **RAID 1** = mirroring, tolerates 1 disk failure, min 2 disks. **RAID 5** = striping with parity, tolerates 1 disk failure, min 3 disks. **RAID 10** = mirror + stripe, tolerates at least 1 disk (one per mirror pair), min 4 disks.

**Rubric (3 pts):** (1) correct fault tolerance for each level; (2) correct minimum disk counts; (3) no contradictions/mix-ups between levels.

---

## Score-tracking table

Fill the **Correct** column as you grade. "n" = number of questions in that row.

| Area | Topic | Questions | Correct |
|---|---|---|---|
| AD DS | What is AD DS | 1, 19 | ___ / 2 |
| AD DS | Why domain services | 2, 13 | ___ / 2 |
| AD DS | Database partitions | 3, 4, 14, 20 | ___ / 4 |
| AD DS | Sites & replication | 5, 6, 16 | ___ / 3 |
| AD DS | Logical components | 7, 8, 15, 24 | ___ / 4 |
| AD DS | FSMO roles | 9, 10, 17, 21 | ___ / 4 |
| AD DS | Global Catalog | 11, 18, 22 | ___ / 3 |
| AD DS | IGDLA model | 12, 23 | ___ / 2 |
| Hyper-V | Hypervisor types | 25, 29, 31 | ___ / 3 |
| Hyper-V | Virtual switches | 27, 30, 32 | ___ / 3 |
| Hyper-V | Checkpoints | 26, 28 | ___ / 2 |
| Storage | iSCSI | 33, 34, 39 | ___ / 3 |
| Storage | Storage pools | 35, 37 | ___ / 2 |
| Storage | RAID | 36, 38, 40 | ___ / 3 |

**Total: ___ / 70**

---

## Prioritized restudy list

**Method:** rank each row by *(questions missed ÷ questions in row)*, highest first. Skip rows with 0 misses.
Tie-break: prioritize AD DS rows (the largest cluster on the real exam).

**Default high-risk order (review these first, even before grading — they're the most-likely-missed traps):**

1. **FSMO roles** (Q9, 10, 17, 21) — the 2 forest + 3×N domain count, which role does what, and transfer vs seize.
2. **Database partitions** (Q3, 4, 14, 20) — which partitions are forest-wide vs domain-wide, and *where* each kind of data lives.
3. **Global Catalog** (Q11, 18, 22) — its two jobs (searches **and** logins) and the "GC down in multi-domain forest" consequence.
4. **RAID** (Q36, 38, 40) — minimum disk counts, fault tolerance, and usable-capacity math per level.
5. **Sites & replication** (Q5, 6, 16) — intrasite vs intersite, and the subnet→site mapping that drives client DC selection.
6. **iSCSI** (Q33, 34, 39) — target vs initiator and *why* it's block-level.
7. **Checkpoints** (Q26, 28) — production (VSS/app-consistent) vs standard, and "not a backup."
8. **IGDLA** (Q12, 23) — Global → Domain Local direction, and the Universal-group extension.

**After grading:** re-rank with your actual misses, then for each weak row, rewrite that topic's notes from
memory (blank-page dump) *before* re-reading them — recall first, check second.
