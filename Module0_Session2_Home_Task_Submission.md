# Module 0 · Session 2 — Home Task Submission

## A Lab Card, Written and Handed In

### Professional Training in Cybersecurity I

**Student Name:** Zeyad Ahmed Ramadan

**Date:**

---

> [!note] How to use this submission
> This single file is your **graded artifact** for the home task.
> Work through the Home Task and fill in the slots below, in task order.
>
> Two slots are different from the rest: **your lab card** in Task 1 and **your corrected section** in Task 2 are written directly on this page, as Markdown, not pasted into a box.
> Replace each one's placeholder line with your own Markdown, and check it in the reading view with **Ctrl+E**.
>
> Save each screenshot in the `screenshots/` folder beside this file, under the name its slot gives, and embed it with `![task1-lab-card](screenshots/task1-lab-card.png)` on its own line below its evidence callout, after a blank line.
>
> **Before you submit:** delete this note, then commit and push **this file together with its `screenshots/` folder**.

---

# Task 1: Write a Lab Card in Markdown

**Your lab card, written directly below this line in place of the placeholder:**

### My Lab

- **OS:** Kali Linux
- **Virtualization:** VMware Workstation
- **Tools:** Git, Obsidian, VS Code
- **Repository:** git-practice
- **Purpose:** Practice using Git, Markdown, and basic cybersecurity tools![](Screenshots/screenshots/task1-lab-card.png)

> [!example] Evidence — screenshot
> *(your lab card in the reading view — `task1-lab-card.png`)*

**Q1. Your screenshot's path is `screenshots/task1-lab-card.png`, not `/home/kali/student-YOUR-USERNAME/...`.
Where is that path read from, and why would the full path show a broken image to your instructor even though it works on your machine?**

```
The path is read relative to the Markdown file. A full path such as /home/kali/... only exists on my machine, so it would not work on my instructor's machine
```

**Q2. Your screenshot line starts with `!`.
What would the same line show without the `!`?**

```
Without the !, Markdown would show a clickable link to the image instead of displaying the image itself
```

---

# Task 2: Correct a Broken Section

**The four mistakes: for each line, what is wrong, and what Obsidian shows because of it.**

2a — Line 1 (`### Lab Checks`): Answer:
The heading is missing a space after the three # characters, so Obsidian does not render it as a level-3 heading.

2b — Lines 3–4 (the two table lines): Answer:
The table is missing the delimiter row, so Obsidian does not render it as a proper table.

2c — Line 6 (` ```bash `): Answer:
The code block is not closed after the ping command, so the following image and content are treated as part of the code block.

2d — Line 9 (the image line): Answer:
The image filename contains spaces and does not match the required task1-lab-card.png filename, so the image does not load.

**Your corrected section, written directly below this line in place of the placeholder:**

### Lab Checks

| Check | Result |
|---|---|
| Kali reaches Ubuntu | passed |

```bash
ping -c 1 10.0.2.5
> [!example] Evidence — screenshot
> *(the corrected section in the reading view, its picture showing — `task2-fixed.png`)*

**Q1. The mistake on line 6 broke more than its own line.
What did it do to the rest of the section, and why does that make it the most expensive of the four in a worksheet?**

```
(your answer here)
```

---

# Task 3: Hand It In and Confirm It Arrived

**Your `git push` output:**

```
Everything up-to-date
```

**Your `git status` output, after the push:**

```
Your branch is up to date with 'origin/main'.
```

**Your `git log --oneline -3` output:**

```
ebf3833 (HEAD -> main, origin/main) Module 0 Session 2: home task 2
```

> [!example] Evidence — screenshot
> *(this worksheet open on GitHub, showing your lab card and its picture — `task3-github.png`)*

**Q1. The newest line of `git log --oneline` shows `(HEAD -> main, origin/main)`.
What does each of the two names tell you, and what would it mean if `origin/main` were one line lower?**

```
HEAD -> main means my local main branch points to the newest commit. origin/main means the remote-tracking branch on GitHub points to the same commit. If origin/main were one line lower, my local main branch would be ahead of GitHub and the newest commit would not have been pushed yet.
```

**Q2. You committed twice but pushed once.
Until the push, who could see your two commits, and what would that have meant at 22:00 on Saturday?**

```
Until the push, only my local repository could see the two commits. GitHub would not have them yet, so if the deadline passed before the push, those commits would not count as submitted on GitHub.```

---

# Anything that failed

If something did not work, describe it here: **the exact step, the exact message, and what you tried.**
This is not a penalty.
A failure you can describe is a two-minute fix, and describing it accurately is a graded skill in this course.

```
I initially saved some screenshots in the wrong folder and had to move them to the correct screenshots folder before pushing the Home Task.```

---

# AI Assistance

One line, **required either way**: `None`, or the AI assistant you used and what you used it for, for example *"to explain the error `git push` printed"*.
Using one for learning, explanation or debugging is allowed.
Not disclosing it is an integrity violation.

```
I used ChatGPT to explain the Git and Markdown instructions, troubleshoot errors, and help me understand how to complete the Home Task.```
