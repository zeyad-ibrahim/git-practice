# Module 0 · Session 1 — Home Task Submission
## Proving the Lab Does What It Claims
**Course:** Professional Training in Cybersecurity I  
**Student name:** [CONFIRM FULL NAME]  
**Date:** [ENTER DATE]

> **Evidence notice:** Conceptual answers are drafted. Perform each actual test in the lab; write down observed results and add genuine screenshots before submission. Restore all modified lab settings.

## Task 1 — Finish the build
**What was unfinished?** `[ENTER WHAT WAS ACTUALLY UNFINISHED, OR NONE]`

**Three checks, from Kali:**
```bash
ip a
# [PASTE REAL OUTPUT]
ping -c 1 [ACTUAL_UBUNTU_IP]
# [PASTE REAL OUTPUT]
ssh lab
# [PASTE REAL OUTPUT]
```
**Check 1 on each system:**
```text
Kali, ip a: [REAL IP]
Ubuntu, ip a: [REAL IP]
Windows, ipconfig: [REAL IP]
```
**Evidence:** `[VERIFY: screenshots/task1-checks.png]`

## Task 2 — Prove a NAT Network is not plain NAT
**Prediction BEFORE changing anything:** With Kali switched from the shared `CyberLab` NAT Network to plain NAT, Kali should normally still obtain its own network address and retain outbound connectivity, but direct Kali-to-Ubuntu ping and `ssh lab` are expected to fail because plain NAT does not automatically place Kali on Ubuntu's reachable subnet. **Record your prediction before your test; actual outcomes can vary by configuration.**

**Three checks under plain NAT:**
```text
[PASTE ACTUAL ADDRESS / PING / SSH RESULTS]
```
**Evidence:** `[VERIFY: screenshots/task2-plain-nat.png]`

**Three checks after returning Adapter 1 to NAT Network / CyberLab:**
```text
[PASTE ACTUAL ADDRESS / PING / SSH RESULTS]
```
**Evidence:** `[VERIFY: screenshots/task2-restored.png, INCLUDING ADAPTER SETTING]`

**Q1. Which checks changed, and which failed first?**  
**Answer:** In the expected setup, obtaining an address still works, but ping to Ubuntu is the first failed connectivity test and SSH to `lab` fails as well. After returning to CyberLab, both should pass. [ADJUST TO YOUR OBSERVED RESULTS.]

**Q2. Why can Kali reach the Internet but not Ubuntu under plain NAT?**  
**Answer:** Plain NAT provides outbound translation toward external networks; it does not automatically establish the shared peer-to-peer virtual LAN used by the other lab VM. Internet access alone cannot prove Kali and Ubuntu can communicate directly.

**Q3. Why is the first failing check useful?**  
**Answer:** A failed ping isolates the problem earlier in the networking path than SSH: it shows reachability is already failing before we need to investigate credentials or the SSH server. The address check only proves interface configuration, while SSH adds application and authentication dependencies.

## Task 3 — Prove SSH client config also works for SCP
```bash
ssh lab uptime
# [PASTE REAL OUTPUT]
scp lab-notes.txt lab:
# [PASTE REAL OUTPUT]
scp lab:lab-notes.txt returned-notes.txt
cat returned-notes.txt
# [PASTE REAL OUTPUT]
```
**Evidence:** `[VERIFY: screenshots/task3-scp.png]`

**Q1. Where did the address, username and key come from?**  
**Answer:** From the matching `Host lab` block in Kali's `~/.ssh/config`: `HostName` sets the address, `User` sets the account, and `IdentityFile` chooses the private key. `scp` uses SSH and reads the same configuration.

**Q2. What should be edited if the server's DHCP address changes?**  
**Answer:** Update the `HostName` value in the `Host lab` entry in one place—Kali's `~/.ssh/config`—then use `lab` again in SSH and SCP commands.

**Q3. Why use `ssh lab uptime` rather than open a shell and type `uptime`?**  
**Answer:** It executes one remote command non-interactively, returns its output and exit status to the local shell, and can be scripted without starting an interactive session.

## Task 4 — Prove what a snapshot restores
**Create a file, then show it:**
```bash
# [ENTER THE ACTUAL COMMANDS AND OUTPUT FOR important-notes.txt AND ls ~]
```
**Stop the SSH listener and prove connection fails:**
```bash
# [ENTER THE ACTUAL COMMANDS AND OUTPUT]
```
**Evidence:** `[VERIFY: screenshots/task4-broken.png]`

**Restore Ubuntu's `clean install` snapshot, then prove the intended SSH state and file status:**
```bash
# [PASTE ACTUAL ssh lab AND ls ~ OUTPUT]
```
**Evidence:** `[VERIFY: screenshots/task4-restored.png]`

**Q1. What happened to important-notes.txt, and why?**  
**Answer:** If the file was created after the `clean install` snapshot, restoring that earlier snapshot removes it from the restored VM state. [CONFIRM YOUR OBSERVATION.]

**Q2. Explain why restoring is not just undoing the last action.**  
**Answer:** A snapshot restores the whole saved machine state, including filesystem and system settings, not just the most recent change. Multiple later changes may disappear together.

**Q3. What does a snapshot NOT protect you from?**  
**Answer:** It is not an independent backup. It does not protect against loss of the host's storage device or corruption/loss of the VM and snapshot files kept on that same device.

## Task 5 — Short answers
**Q1. Why create the network first?**  
**Answer:** So the correct named NAT Network can be assigned to all guests from the start. Otherwise, you must revisit each guest's adapter configuration and re-test IP addresses and reachability.

**Q2. Windows ping fails: one harmless and one real problem; how to tell?**  
**Answer:** Harmless: Windows Firewall blocks ICMP echo while the lab network is working. Real: Windows is attached to the wrong virtual network or has an incorrect address. Check its `ipconfig`, compare its network with the other guests, and verify Kali–Ubuntu ping/SSH. If the network checks pass, use an allowed Windows-specific connectivity test or check firewall rules rather than treating ping as definitive.

**Q3. What crosses the wire during SSH key login? Why can't an observer replay it?**  
**Answer:** The client sends proof based on a signature using its private key; the private key itself never crosses the network. SSH's exchange binds authentication to the current session, so captured traffic is not reusable as a fresh login credential.

**Q4. Why does Ubuntu not need the private key?**  
**Answer:** Ubuntu keeps the matching public key in `authorized_keys` and uses it to verify signatures. It cannot use the public key to derive the client's private key.

**Q5. What prevents outsiders from initiating connections to VMs without a special rule?**  
**Answer:** The NAT gateway normally has no unsolicited inbound mapping or port forwarding to the lab guests, so unsolicited inbound connections cannot directly reach them. It is not a substitute for host firewalls.

**Q6. What prevents YOUR outbound traffic from contacting real targets?**  
**Answer:** NAT does not provide that restriction; your ethical rules, authorization scope, and any deliberately configured egress filtering determine what you are allowed or able to contact.

## Confirmation — verify rather than assume
- [ ] Kali Adapter 1 returned to NAT Network / CyberLab
- [ ] Ubuntu restored to intended state and SSH verified
- [ ] All three guests boot; all three checks tested
- [ ] Original screenshots attached beside this file in `screenshots/`

## AI assistance disclosure
ChatGPT was used to explain technical concepts and draft written answers. VM operations, results, and screenshots are not generated or verified by ChatGPT and must be supplied from the student's actual work.
