# Module 0 · Session 1 — Practical Guide Submission
## The Virtual Lab: VirtualBox, the Course Machines, and SSH
**Course:** Professional Training in Cybersecurity I  
**Student name:** [CONFIRM FULL NAME]  
**Date:** [ENTER DATE]

> **Evidence notice:** Conceptual questions are drafted below. Commands, screenshots, IP addresses, installed software, and actions must be verified on your own VMs. Never submit the `[VERIFY]` fields as proof of an action you have not performed.

## Exercise 1 — Install VirtualBox (required)
**Evidence:** `[VERIFY: add screenshots/ex1-manager.png of your host VirtualBox Manager]`

**Q1. Did you change firmware, and how did you confirm virtualization?**  
**Answer:** [VERIFY ACTUAL HOST EXPERIENCE]. On Windows, Task Manager → Performance → CPU shows whether **Virtualization** is enabled; alternatively confirm AMD-V/Intel VT-x in UEFI/BIOS and verify VirtualBox can start a 64-bit guest. Whether firmware settings were changed depends on the host.

## Exercise 2 — Create the CyberLab network (required)
**Command/output:**
```bash
VBoxManage list natnets
# [PASTE ACTUAL CYBERLAB NETWORK OUTPUT]
```
**Evidence:** `[VERIFY: screenshots/ex2-cyberlab.png]`

**Q1. Why create the network before the machines?**  
**Answer:** The shared NAT Network needs to exist so every VM can select the same named network during adapter configuration. If it is created later, the adapter settings for each VM must be revisited and connectivity re-tested.

**Q2. NAT Network versus plain NAT?**  
**Answer:** A NAT Network lets VMs on the same virtual subnet reach one another while using NAT for outbound access. VirtualBox's per-VM plain NAT commonly allows outbound access but does not automatically put separate VMs on one reachable virtual LAN.

## Exercise 3 — Build Kali (required)
**Kali `ip a`:**
```bash
ip a
# [PASTE ACTUAL IPV4 INTERFACE LINE]
```
**Evidence:** `[VERIFY: screenshots/ex3-kali-desktop.png]`

**Q1. Why import Kali while installing the others?**  
**Answer:** An imported Kali appliance is already configured as a VM image, saving setup time and providing a consistent tool environment. An ISO installation of Ubuntu Server or Windows requires going through the installation workflow and selecting its settings.

**Q2. What did you do about Kali's published password?**  
**Answer:** [VERIFY WHAT YOU ACTUALLY DID]. The correct action is to change any published default using `passwd` and secure the VM, because anyone who knows the default credentials could log in if they can reach it.

## Exercise 4 — Build Ubuntu Server (required)
**Ubuntu `ip a`:**
```bash
ip a
# [PASTE ACTUAL IPV4 INTERFACE LINE]
```
**Username:** `[VERIFY: often student in the guide]`  
**Evidence:** `[VERIFY: screenshots/ex4-ubuntu-console.png]`

**Q1. What does “Install OpenSSH server” do?**  
**Answer:** It installs and configures the SSH server, allowing Kali to connect remotely to Ubuntu. Without it, the server package/service would need to be installed, enabled, and tested later.

## Exercise 5 — Build Windows 11 (required)
**Windows `ipconfig`:**
```text
[PASTE ACTUAL IPV4 ADDRESS / ADAPTER]
```
**Evidence:** `[VERIFY: screenshots/ex5-windows-desktop.png]`

**Q1. Why install without a product key instead of an evaluation edition?**  
**Answer:** Skipping key entry may let setup proceed with an unactivated installation, subject to licensing requirements and activation restrictions such as personalization limits. An evaluation edition is designed for time-limited testing; the course may favor a standard lab installation. [VERIFY THIS MATCHES YOUR INSTALLATION AND LICENSE.]

**Q2. How did you create a local account, and why use one?**  
**Answer:** [ENTER YOUR ACTUAL SETUP PATH]. A local account keeps this isolated lab separate from personal cloud identities and limits synchronization of personal data.

## Exercise 6 — Reach Ubuntu via SSH (required)
**Actual Kali SSH configuration:**
```sshconfig
Host lab
    HostName [ACTUAL_UBUNTU_IP]
    User student
    IdentityFile ~/.ssh/[ACTUAL_PRIVATE_KEY_FILENAME]
```
**Actual session:**
```bash
ssh lab
# [PASTE ACTUAL PROMPT / OUTPUT]
```
**Evidence:** `[VERIFY: screenshots/ex6-ssh-lab.png]`

**Q1. Where is the private key, and what did the server receive?**  
**Answer:** The private key stays on the Kali client, normally within `~/.ssh/`. Ubuntu receives the matching **public** key in the user's `~/.ssh/authorized_keys`, never the private key.

**Q2. Why isn't the Ubuntu password needed after `ssh-copy-id`?**  
**Answer:** `ssh-copy-id` installs the public key on Ubuntu. On later logins, SSH verifies a cryptographic signature made with Kali's private key, so key authentication can succeed without typing the account password (assuming the server is configured to allow it).

## Exercise 7 — Verify the complete lab (required)
**Check 1 — addresses:**
```text
Kali: [PASTE REAL IP]
Ubuntu: [PASTE REAL IP]
Windows: [PASTE REAL IP]
```
**Check 2 — Kali to Ubuntu:**
```bash
ping -c 1 [ACTUAL_UBUNTU_IP]
# [PASTE ACTUAL RESULT]
```
**Check 3 — Kali SSH:**
```bash
ssh lab
# [PASTE ACTUAL RESULT]
```
**Evidence:** `[VERIFY: screenshots/ex7-three-checks.png]`

**Q1. Check 1 passes, check 2 fails: what do you know?**  
**Answer:** The guests have assigned IP settings, but that alone does not prove reachability. A failed ping can indicate mismatched virtual networks, incorrect destinations, a stopped guest, or filtering; it does not, on its own, prove an SSH problem.

**Q2. Why not ping Windows for check 2?**  
**Answer:** Windows Defender Firewall may block inbound ICMP echo requests by default. A failed ping could therefore mislead you even when its VM is connected properly. Ubuntu provides a more dependable target for the documented test.

## Exercise 8 — Take snapshots (required)
**Evidence:** `[VERIFY: screenshots/ex8-snapshots-kali.png, ex8-snapshots-ubuntu.png, ex8-snapshots-windows.png; each showing clean install]`

**Q1. Why name snapshots after their state?**  
**Answer:** A state-based name such as `clean install` immediately explains what can be restored; a date alone does not tell you what software, settings, and changes are included.

**Q2. A file was created after the snapshot. What must happen before restoring?**  
**Answer:** Copy the important file to a safe place outside the VM/snapshot first (for example, an approved host folder or backup). Restoring an earlier state can discard later changes inside the VM.

## Anything that failed
`[DESCRIBE REAL ERRORS AND FIXES, OR SAY NOTHING FAILED AFTER VERIFYING]`

## AI assistance disclosure
ChatGPT was used to draft explanations and improve Markdown formatting. All environment-specific observations, commands, and screenshots must be independently checked and captured by the student.

## Before submitting
- [ ] Replace every `[VERIFY]`, `[PASTE]`, and `[ENTER]` item with real evidence.
- [ ] Store screenshots beside the worksheet under `screenshots/` and embed them.
- [ ] Confirm all three guests, networking, SSH, and snapshots actually work.
- [ ] Check name/date, then commit and push.
