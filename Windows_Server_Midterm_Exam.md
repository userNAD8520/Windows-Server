---
title: Windows Server Midterm — Mock Exam (Complete Scope)
week: midterm
tags: [windows-server, mock-exam, active-directory, sid, hyper-v, storage, raid, das, nas, san]
---

# Windows Server Midterm — Mock Exam (Complete Scope)

> **📋 Exam header**
> - **Total points:** 80
> - **Suggested time:** 90 minutes
> - **Multiple choice** — 23 questions × 1 pt = **23 pts**
> - **Select-all-that-apply** — 12 questions × 2 pts (all-or-nothing) = **24 pts**
> - **Short answer** — 11 questions × 3 pts = **33 pts**
>
> **Rules:** Select-all questions award points only if *every* correct option is chosen and *no* incorrect
> option is chosen. No partial credit. This file contains **no answers** — use it for a closed-book run,
> then check against the separate answer key.

---

## Part A — Active Directory Domain Services (26 questions)

### Multiple choice (1 pt each)

**1.** Which server role hosts the directory database (NTDS.dit) and acts as the Kerberos Key Distribution
Center (KDC)?
A. Member server
B. DNS server
C. Domain controller
D. Global Catalog server (standalone)
*AD DS · What is AD DS* · Difficulty: Medium

**2.** A 300-workstation company is replacing a workgroup with AD DS. What is the PRIMARY benefit?
A. Faster network throughput
B. Centralized identity and a single point of administration
C. Automatic hardware failover
D. Built-in antivirus protection
*AD DS · Why domain services* · Difficulty: Medium

**3.** Which AD DS database partition holds a single domain's users, computers, and groups?
A. Schema partition
B. Configuration partition
C. Domain partition
D. Application partition
*AD DS · Database partitions* · Difficulty: Medium

**4.** An administrator needs to locate where the forest's site topology (sites, site links, and domain
controllers) is stored. Which partition contains it?
A. Schema partition
B. Configuration partition
C. Domain partition
D. Application partition
*AD DS · Database partitions* · Difficulty: Hard

**5.** How does intersite replication differ from intrasite replication?
A. It is uncompressed and change-notified
B. It is compressed and scheduled over site links
C. It replicates more frequently than intrasite replication
D. It replicates only schema changes
*AD DS · Sites & replication* · Difficulty: Medium

**6.** A user consistently authenticates to a domain controller in a remote site instead of the local DC.
What is the most likely cause?
A. The local DC is a Global Catalog server
B. The user's subnet is not mapped to the correct site
C. The domain functional level is too low
D. The site link cost is set too high
*AD DS · Sites & replication* · Difficulty: Hard

**7.** Which is the ultimate security boundary in Active Directory?
A. Domain
B. Organizational unit
C. Forest
D. Tree
*AD DS · Logical components* · Difficulty: Medium

**8.** A forest contains the domains `contoso.com` and `fabrikam.com`. How are these two namespaces related?
A. They must both belong to the same tree
B. They are separate trees within the same forest
C. They must be placed in separate forests
D. They must be collapsed into a single domain
*AD DS · Logical components* · Difficulty: Hard

**9.** A forest contains three domains. How many FSMO role holders exist in total?
A. 5
B. 8
C. 11
D. 15
*AD DS · FSMO roles* · Difficulty: Hard

**10.** Which FSMO role handles password changes, account lockouts, and time synchronization?
A. RID Master
B. PDC Emulator
C. Infrastructure Master
D. Schema Master
*AD DS · FSMO roles* · Difficulty: Medium

**11.** In a multi-domain forest, the Global Catalog becomes unavailable. What happens?
A. Nothing — users can still log on normally
B. Ordinary users cannot log on, but members of Domain Admins still can
C. Only cross-domain searches fail; logons are unaffected
D. All replication stops immediately
*AD DS · Global Catalog* · Difficulty: Hard

**12.** In the IGDLA model, which nesting is correct?
A. A Domain Local group inside a Global group
B. A Global group inside a Domain Local group
C. A Global group inside a Universal group only
D. A Domain Local group inside a Universal group
*AD DS · IGDLA model* · Difficulty: Hard

**13.** An administrator deletes a user account and then recreates it with the identical name and logon.
The recreated user loses access to their old files. Why?
A. The user's password hash changed
B. A new SID was assigned, and the old ACLs reference the previous SID
C. The GUID was reused and now conflicts with the old object
D. The user must be re-added to the Global Catalog
*AD DS · SID* · Difficulty: Hard

### Select-all-that-apply (2 pts each)

**14.** Which of the following are benefits of AD DS over a workgroup? (Select all that apply.)
- [ ] A. Centralized account management
- [ ] B. Single sign-on across resources
- [ ] C. Group Policy for central configuration
- [ ] D. Each workstation maintains its own independent account database
- [ ] E. Delegation of administration scoped to an OU
*AD DS · Why domain services* · Difficulty: Medium

**15.** Which statements about AD DS database partitions are TRUE? (Select all that apply.)
- [ ] A. The Schema partition is replicated to every DC in the forest.
- [ ] B. The Configuration partition holds forest topology and is forest-wide.
- [ ] C. The Domain partition replicates only to DCs in that domain.
- [ ] D. Application partitions replicate to a chosen subset of DCs.
- [ ] E. All four partitions replicate to every DC in the forest.
*AD DS · Database partitions* · Difficulty: Hard

**16.** Which statements about domains, trees, forests, and OUs are TRUE? (Select all that apply.)
- [ ] A. A forest is the security boundary and shares one schema.
- [ ] B. A tree consists of domains with a contiguous namespace.
- [ ] C. An OU is used for delegation and Group Policy.
- [ ] D. A forest can contain domains with discontiguous namespaces.
- [ ] E. An OU is itself a security boundary.
*AD DS · Logical components* · Difficulty: Medium

**17.** Which statements about sites and replication are TRUE? (Select all that apply.)
- [ ] A. A site is a group of well-connected subnets.
- [ ] B. Intrasite replication is change-notified and uncompressed.
- [ ] C. Intersite replication is compressed and scheduled.
- [ ] D. Subnets are mapped to sites to direct clients to the nearest DC.
- [ ] E. A site is a logical grouping of users, just like a domain.
*AD DS · Sites & replication* · Difficulty: Hard

**18.** Which statements about FSMO roles are TRUE? (Select all that apply.)
- [ ] A. Schema Master and Domain Naming Master are forest-wide roles.
- [ ] B. RID Master, PDC Emulator, and Infrastructure Master are domain-wide roles.
- [ ] C. The first DC in a forest holds all five roles by default.
- [ ] D. A forest with N domains has 2 + 3N role holders.
- [ ] E. All five roles exist once per domain.
*AD DS · FSMO roles* · Difficulty: Medium

**19.** Which statements about the Global Catalog are TRUE? (Select all that apply.)
- [ ] A. It holds a partial copy of every object in the forest.
- [ ] B. It stores only a subset of each object's attributes.
- [ ] C. It facilitates forest-wide searches.
- [ ] D. It supplies universal group membership during logon.
- [ ] E. It holds a full copy of every attribute of every object.
*AD DS · Global Catalog* · Difficulty: Hard

**20.** Which statements about SIDs are TRUE? (Select all that apply.)
- [ ] A. A SID is used in access control lists to grant permissions.
- [ ] B. Renaming a user keeps the same SID, so permissions follow.
- [ ] C. Deleting and recreating a user gives it a new SID.
- [ ] D. The RID Master FSMO role supplies the RIDs used to build SIDs.
- [ ] E. A SID is the same thing as a GUID.
*AD DS · SID* · Difficulty: Medium

### Short answer (3 pts each)

**21.** Describe what AD DS is, and explain how it both authenticates and authorizes users. (2–4 sentences)

*AD DS · What is AD DS* · Difficulty: Hard

**Your answer:**




**22.** Name the four AD DS database partitions and state the replication scope of each. (2–4 sentences)

*AD DS · Database partitions* · Difficulty: Hard

**Your answer:**




**23.** Explain the difference between transferring and seizing a FSMO role, and state what you must do
to the old DC after a seize. (2–4 sentences)

*AD DS · FSMO roles* · Difficulty: Hard

**Your answer:**




**24.** Describe the two roles the Global Catalog plays in an Active Directory environment. (2–4 sentences)

*AD DS · Global Catalog* · Difficulty: Medium

**Your answer:**




**25.** Explain the IGDLA model — what each letter stands for, why the pattern is used, and when you would
insert a Universal group into the chain. (2–4 sentences)

*AD DS · IGDLA model* · Difficulty: Hard

**Your answer:**




**26.** Describe the AD DS logical hierarchy from forest down to an OU, and state the role an OU plays in
administration. (2–4 sentences)

*AD DS · Logical components* · Difficulty: Medium

**Your answer:**




---

## Part B — Hyper-V & Hypervisors (8 questions)

**27.** You enable the Hyper-V role on a Windows Server host. Which statement is correct?
A. Hyper-V is a Type 2 hypervisor because Windows is still installed
B. Enabling Hyper-V causes Windows to run under the hypervisor, so it is a Type 1 (bare-metal) hypervisor
C. Hyper-V is a Type 2 hypervisor, just like VMware Workstation
D. Hyper-V runs entirely in user mode
*Hyper-V · Hypervisor types* · Difficulty: Hard

**28.** Which statement about Hyper-V checkpoints is correct?
A. A checkpoint is a full backup of the virtual machine
B. A production checkpoint uses VSS and is application-consistent
C. A standard checkpoint is application-consistent
D. Checkpoints protect against host or storage failure
*Hyper-V · Checkpoints* · Difficulty: Hard

**29.** Virtual machines must be able to reach the physical LAN and the internet. Which Hyper-V virtual
switch type should you use?
A. Private
B. Internal
C. External
D. NAT-only
*Hyper-V · Virtual switches* · Difficulty: Medium

**30.** Which checkpoint type is application-consistent and does NOT capture the VM's memory state?
A. Standard checkpoint
B. Production checkpoint
C. Differencing checkpoint
D. Full checkpoint
*Hyper-V · Checkpoints* · Difficulty: Medium

**31.** Which statements about Type 1 and Type 2 hypervisors are TRUE? (Select all that apply.)
- [ ] A. A Type 1 hypervisor runs directly on the hardware.
- [ ] B. A Type 2 hypervisor runs on top of a host OS.
- [ ] C. Hyper-V and ESXi are Type 1 hypervisors.
- [ ] D. VirtualBox and VMware Workstation are Type 2 hypervisors.
- [ ] E. Type 2 hypervisors are generally faster than Type 1.
*Hyper-V · Hypervisor types* · Difficulty: Medium

**32.** Which statements about Hyper-V virtual switches are TRUE? (Select all that apply.)
- [ ] A. An External switch binds to a physical NIC.
- [ ] B. An Internal switch connects VMs and the host.
- [ ] C. A Private switch connects VMs only.
- [ ] D. Only the External switch requires a physical NIC.
- [ ] E. An Internal switch gives VMs direct internet access.
*Hyper-V · Virtual switches* · Difficulty: Medium

**33.** Explain the difference between a Type 1 and a Type 2 hypervisor, give an example of each, and state
a typical use case for each. (2–4 sentences)

*Hyper-V · Hypervisor types* · Difficulty: Hard

**Your answer:**




**34.** Explain the difference between an Internal and a Private virtual switch. (2–4 sentences)

*Hyper-V · Virtual switches* · Difficulty: Medium

**Your answer:**




---

## Part C — Storage: iSCSI, Pools, RAID & Enterprise Storage (12 questions)

**35.** In an iSCSI deployment, which component presents the LUNs (the storage disks)?
A. The initiator
B. The target
C. The IQN
D. The switch
*Storage · iSCSI* · Difficulty: Hard

**36.** iSCSI provides block-level storage. What does this mean in practice?
A. The storage device serves files over SMB
B. The connecting server formats its own filesystem on the LUN
C. The storage device owns and manages the filesystem
D. Data is accessed through NFS
*Storage · iSCSI* · Difficulty: Hard

**37.** In Windows Storage Spaces, what is a storage pool?
A. A virtual disk with a resiliency setting
B. A group of physical disks aggregated into one pool of capacity
C. A formatted volume with a drive letter
D. A hardware RAID controller
*Storage · Storage pools* · Difficulty: Medium

**38.** Which RAID level provides striping with NO redundancy?
A. RAID 0
B. RAID 1
C. RAID 5
D. RAID 10
*Storage · RAID* · Difficulty: Hard

**39.** Which enterprise storage solution serves files over SMB/NFS (file-level)?
A. DAS
B. NAS
C. SAN
D. iSCSI target
*Storage · DAS vs NAS vs SAN* · Difficulty: Medium

**40.** Four 2 TB disks are configured in RAID 5. What is the usable capacity?
A. 2 TB
B. 4 TB
C. 6 TB
D. 8 TB
*Storage · Storage Layout & Disk Requirements* · Difficulty: Hard

### Select-all-that-apply (2 pts each)

**41.** Which of the following are benefits of storage pools in virtualization? (Select all that apply.)
- [ ] A. Aggregate disks of different sizes and types
- [ ] B. Add capacity by adding more disks to the pool
- [ ] C. Provide resiliency (Mirror/Parity) without a hardware RAID controller
- [ ] D. Enable storage tiering (SSD + HDD)
- [ ] E. Require a dedicated hardware RAID controller
*Storage · Storage pools* · Difficulty: Medium

**42.** Which statements about RAID are TRUE? (Select all that apply.)
- [ ] A. RAID 0 has no fault tolerance.
- [ ] B. RAID 1 requires a minimum of 2 disks.
- [ ] C. RAID 5 requires a minimum of 3 disks and tolerates 1 disk failure.
- [ ] D. RAID 10 requires a minimum of 4 disks.
- [ ] E. RAID 5 provides 100% usable capacity.
*Storage · RAID* · Difficulty: Hard

**43.** Which statements about usable capacity are TRUE? (Select all that apply.)
- [ ] A. RAID 0 provides 100% usable capacity.
- [ ] B. RAID 1 provides 50% usable capacity.
- [ ] C. RAID 5 provides N−1 disks of usable capacity.
- [ ] D. RAID 10 provides 50% usable capacity.
- [ ] E. RAID 5 provides 100% usable capacity.
*Storage · Storage Layout & Disk Requirements* · Difficulty: Medium

### Short answer (3 pts each)

**44.** Explain the difference between an iSCSI target and an iSCSI initiator, and explain why iSCSI is
considered block-level storage. (2–4 sentences)

*Storage · iSCSI* · Difficulty: Hard

**Your answer:**




**45.** Compare RAID 0, 1, 5, and 10 in terms of fault tolerance and minimum disk count. (2–4 sentences)

*Storage · RAID* · Difficulty: Hard

**Your answer:**




**46.** Compare DAS, NAS, and SAN in terms of access level (block vs file) and give a typical use case for
each. (2–4 sentences)

*Storage · DAS vs NAS vs SAN* · Difficulty: Hard

**Your answer:**




---
