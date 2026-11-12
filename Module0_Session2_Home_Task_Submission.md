# Module 0 · Session 2 — Home Task Submission
## A Lab Card, Written and Handed In
**Course:** Professional Training in Cybersecurity I  
**Student name:** Zeyad Ahmed Ramadan *(as shown in the original uploaded worksheet — verify against your official name)*  
**Date:** [ENTER DATE]

> **Status:** Markdown repairs and conceptual answers prepared. Evidence screenshots `task1-lab-card.png`, `task2-fixed.png` and `task3-github.png` were **not found under those names** in the available GitHub file tree; add real captures before submitting. The source worksheet contained a broken image path and an unclosed code fence, corrected here.

## Task 1 — Write a lab card in Markdown
### My Lab

- **OS:** Kali Linux
- **Virtualization:** VMware Workstation *(from existing student submission; verify actual course lab requirements)*
- **Tools:** Git, Obsidian, VS Code
- **Repository:** [git-practice](https://github.com/zeyad-ibrahim/git-practice)
- **Purpose:** Practice Git, Markdown, and foundational cybersecurity workflows.

**Evidence:** Capture the above card in Obsidian reading view, save beside this worksheet to `screenshots/task1-lab-card.png`, then uncomment the following line:

<!-- ![Lab card in reading view](screenshots/task1-lab-card.png) -->

**Q1. Why a relative screenshot path instead of an absolute `/home/kali/...` path?**  
**Answer:** The relative path resolves from the Markdown document's location inside the repository. An absolute path points to one computer's filesystem, so a reviewer on GitHub or another computer cannot open it.

**Q2. What if the screenshot syntax has no `!`?**  
**Answer:** Without `!`, `[label](path)` renders as a link that the reader must click, rather than an embedded image.

## Task 2 — Correct a broken section
**2a — Heading:** `###Lab Checks` needs a space after `###`; otherwise it may be displayed as plain text rather than a level-three heading.

**2b — Table:** It needs a header separator row such as `| --- | --- |`; without it, the rows do not form a correct Markdown table.

**2c — Code fence:** The `bash` block was left open; without the closing triple backticks, everything after it—including headings and the screenshot—can render as code.

**2d — Image line:** A screenshot path must match its actual filename, capitalization, and relative folder; a mistaken filename or unescaped space can break rendering.

### Lab Checks

| Check | Result |
| --- | --- |
| Kali reaches Ubuntu | [VERIFY WITH A REAL TEST] |

```bash
ping -c 1 [ACTUAL_UBUNTU_IP]
# [PASTE ACTUAL OUTPUT, IF REQUIRED]
```

**Evidence:** Take the corrected section in Obsidian reading view. Save to `screenshots/task2-fixed.png` and then uncomment:

<!-- ![Corrected section](screenshots/task2-fixed.png) -->

**Q1. Why was the unclosed code block the costliest formatting error?**  
**Answer:** It made the rest of the worksheet appear inside the code block. This can hide or distort later questions, tables and image evidence, so multiple otherwise-correct pieces of the assignment seem broken.

## Task 3 — Hand it in and confirm GitHub received it
**Previously recorded `git push` output (from original worksheet):**
```text
Everything up-to-date
```

**Previously recorded `git status` excerpt (from original worksheet):**
```text
Your branch is up to date with 'origin/main'.
```

**Previously recorded `git log --oneline -3` excerpt:**
```text
ebf3833 (HEAD -> main, origin/main) Module 0 Session 2: home task 2
```

> **Verify now:** These are historical excerpts from your uploaded file, not a fresh command run. Re-run `git push`, `git status`, and `git log --oneline -3` after adding final screenshots and paste the complete real output. Capture `screenshots/task3-github.png` showing this worksheet and a rendered image on GitHub.

<!-- ![Worksheet on GitHub](screenshots/task3-github.png) -->

**Q1. What do `HEAD -> main` and `origin/main` mean?**  
**Answer:** `HEAD -> main` identifies the commit pointed to by the locally checked-out `main` branch; `origin/main` identifies the last fetched/pushed remote-tracking position. If `origin/main` is one commit behind `main`, the local commit has not yet been pushed (assuming remote tracking is current).

**Q2. What if you committed twice locally but only pushed after the deadline?**  
**Answer:** Until the push, the commits only existed in the local repository. They would not be visible in the instructor's GitHub view at the deadline and could therefore count as late or not submitted.

## Anything that failed
The original worksheet recorded: *“I initially saved some screenshots in the wrong folder and had to move them to the correct screenshots folder before pushing the Home Task.”* Check that the final screenshot paths match the worksheet location.

## AI assistance disclosure
ChatGPT was used to explain the Git and Markdown instructions, troubleshoot errors, and help draft and repair this worksheet. Commands and screenshots must reflect the student's own work.

## Final checklist
- [ ] Confirm course name, student name and date
- [ ] Re-run the three Git commands and paste complete output
- [ ] Capture and embed all three real screenshots
- [ ] Verify images render on GitHub
- [ ] Commit and push before the deadline
