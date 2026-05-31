<<<<<<< HEAD
# Contributing Guide

## Program-Specific Guides

If you are contributing under a specific program, refer to the dedicated guide for your track:

| Track | Guide | 
 |-------|-------| 
 | GSSoC'26 Contributors | [GSSoC Contributor Guide](docs/GSSOC_CONTRIBUTOR_GUIDE.md) | 
 | GSSoC'26 Mentors | [GSSoC Mentor Guide](docs/GSSOC_MENTOR_GUIDE.md) | 
 | NSoC'26 Contributors | [NSoC Guide](docs/NSOC_GUIDE.md) | 
 | General Contributors | [General Contributor Guide](docs/GENERAL_CONTRIBUTOR_GUIDE.md) |


The rest of this document covers the shared rules, architecture, workflows, automation systems, and contribution policies that apply to all contributors.

---

## Project Philosophy

This repository follows a:

- Zero-build philosophy
- Minimal dependency philosophy
- Static-first architecture
- Edge-runtime compatible workflow

### Core Principles

- No unnecessary dependencies
- No heavy frameworks
- No bundlers unless absolutely required
- Simple and maintainable code
- Fast runtime performance
- Lightweight APIs
- Edge-compatible architecture
- Human-reviewed contributions over AI-generated spam

Contributors should avoid introducing:

- unnecessary npm packages
- client-side frameworks
- large runtime abstractions
- unnecessary build pipelines
- dependency-heavy tooling

unless clearly justified.

---

## Architecture

The project is built using:

| Layer | Technology |
|-------|------------|
| Frontend | Vanilla HTML/CSS/JS |
| Backend | Vercel Edge Functions |
| Hosting | Vercel |
| Data | Static JSON + GitHub API |
| Analytics | localStorage |

### Architecture Goals

- Fully static-first deployment
- Fast initial page load
- Minimal API overhead
- Edge-compatible runtime
- No hydration complexity
- Maintainable repository structure

---

## Local Development

**Install Vercel CLI**

```bash
npm install -g vercel
```

**Clone Repository**

```bash
git clone https://github.com/S3DFX-CYBER/GSoC-Org-Finder-.git
cd GSoC-Org-Finder-
```

**Start Local Development**

```bash
vercel dev
```

This simulates the Vercel Edge runtime locally.

---

## Repository Structure

```
GSoC-Org-Finder-
├── .github/
│   ├── workflows/
│   ├── reviewers/
│   ├── scripts/
│   └── ISSUE_TEMPLATE/
├── api/
├── data/
├── docs/
├── src/
│   ├── js/
│   ├── assets/
│   └── styles.css
├── index.html
├── sw.js
└── README.md
```

---

## How To Start Contributing

### Step 1 — Find an Issue

Go to the **Issues** tab and filter by labels:

- `level:beginner`
- `level:intermediate`
- `level:advanced`
- `type:bug`
- `type:docs`
- `type:ui`
- `type:enhancement`
- `type:api`
- `gssoc26`
- `nsoc26`

Issues are automatically analyzed using repository automation.

The triage system:

- categorizes difficulty
- detects duplicates
- identifies spam
- labels issue type
- flags low-quality reports

---

## Assignment Workflow

This repository uses a **mentor-assisted assignment pipeline**.

> Assignments are **NOT** handled manually through the GitHub UI.  
> All issue assignment requests are processed through repository automation.

### Requesting Assignment

To request an issue, comment:

```
/assign
```

> Do **NOT** self-assign using the GitHub interface.

---

### Mentor-Based Assignment Queue

When a contributor requests assignment:

1. The request is queued automatically
2. Two active mentors are randomly selected from the mentor activity pool
3. The mentors are notified on the issue
4. Mentors have **24 hours** to approve the assignment
5. If mentors do not respond within 24 hours:
   - Mentors are rotated automatically
   - New active mentors are selected
6. If no mentor approves after timeout:
   - The Project Admin (PA) is notified automatically
   - Manual assignment review begins

#### Mentor Selection System

Mentor selection is:

- Randomized
- Activity-aware
- Weighted toward active mentors
- Dynamically rotated
- Workload balanced

The system avoids repeatedly selecting the same mentors for every issue. Mentors are selected from the active mentor leaderboard and review activity data. Inactive mentors are deprioritized automatically.

---

### Assignment Approval Commands

**Contributors**

| Command | Description |
|---------|-------------|
| `/assign` | Request issue assignment |
| `/unassign` | Remove your current assignment |

**Mentors**

| Command | Description |
|---------|-------------|
| `/approve-assignment @username` | Approve and assign a contributor |

> Only currently pinged mentors may approve.

---

### Assignment Eligibility

#### Beginner Issues

Anyone may request assignment.

Examples: documentation fixes, UI tweaks, accessibility fixes, simple bug fixes

#### Intermediate Issues

**Requirements:** GitHub account at least 30 days old

Examples: filtering improvements, caching changes, API improvements, search improvements

#### Advanced Issues

**Requirements:** At least 1 merged PR in this repository

Examples: architecture changes, security-sensitive logic, performance optimization, workflow redesign

---

### Maximum Active Assignments

To ensure fairness:

| Program | Maximum Active Issues |
|---------|-----------------------|
| GSSoC | 3 |
| NSoC | 3 |
| General Contributors | 3 |

Requests above the limit are automatically rejected.

---

## Duplicate Issue Detection

The repository includes an **AI-assisted duplicate detection system**.

### How Duplicate Detection Works

The detector compares:

- Normalized issue titles
- Semantic keyword overlap
- Important technical keywords
- Issue intent similarity
- Token overlap scoring

The system intentionally avoids:

- Aggressive exact-title matching
- Weak substring matching
- Low-confidence duplicate flags

The duplicate detector uses:

- Weighted similarity scoring
- Keyword extraction
- Overlap thresholds
- Confidence filtering
- Technical term matching

This significantly reduces false positives.

> Issues are **NOT** auto-closed solely because they are flagged as possible duplicates.

---

## Smart Review Pipeline

Pull requests go through a **3-stage review pipeline**:

| Stage | Reviewer | Purpose |
|-------|----------|---------|
| Stage 1 | Automation | Validation + anti-spam |
| Stage 2 | Mentors | Code review |
| Stage 3 | Project Admin | Final merge gate |

### Stage 1 — Automated Validation

Automation checks:

- DCO sign-off
- PR formatting
- Issue linking
- Duplicate PR detection
- AI slop detection
- Context validation
- Diff quality
- Repository policy compliance

The repository also uses:

- LLM-assisted PR analysis
- Spam heuristics
- Low-effort detection
- Context validation against linked issues

### Stage 2 — Mentor Review

Once Stage 1 passes:

1. Active mentors are selected automatically
2. Mentors are requested dynamically
3. Review activity is tracked in the mentor leaderboard
4. Review quality scoring is calculated
5. Mentors have **24 hours** to respond
6. Inactive mentors are replaced automatically

#### Mentor Review Quality System

| Review Type | Score |
|-------------|-------|
| Low-effort approval | Low points |
| Detailed review with feedback | Higher points |
| Helpful requested changes | Higher points |
| Merge-quality approval | Highest points |

The mentor leaderboard tracks:

- Reviews completed
- Review quality
- Approvals
- Merged-review count
- Assignment approvals
- Priority review activity

### Mentor Review Leaderboard

The mentor leaderboard:

- Updates automatically
- Tracks all-time review activity
- Includes mentor profile avatars
- Generates visual leaderboard comments
- Updates after PR merges
- Powers mentor assignment weighting

The leaderboard prioritizes: active mentors, high-quality reviewers, and consistent participation.

---

## Contributor Leaderboard

The contributor leaderboard updates automatically after PR merges.

It includes:

- GitHub avatars
- Contributor rankings
- Merged PR counts
- Contribution scores
- Contextual leaderboard comments

Leaderboard comments are posted automatically on merged PRs.

---

## Pull Request Workflow

### Before Opening a PR

Ensure:

- The issue is assigned to you
- The work is complete
- Changes are tested locally
- Your PR follows repository conventions

### Linking Issues is Mandatory

Every PR **MUST** contain:

```
Closes #issue-number
```

> PRs without linked issues may be closed automatically.

### Required PR Standards

Your PR should:

- Remain focused
- Avoid unnecessary files
- Avoid unrelated changes
- Avoid dependency bloat
- Preserve architecture consistency
- Follow conventional commits

---

## Conventional Commit Format

**Format**

```
type: short description
```

**Examples**

```
feat: improve issue filtering
fix: resolve assignment queue race condition
ci: improve mentor rotation workflow
docs: update contribution guide
```

### Common Commit Types

| Type | Description |
|------|-------------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation |
| `style` | UI/styling |
| `refactor` | Internal cleanup |
| `perf` | Performance |
| `ci` | Workflow/configuration |
| `chore` | Maintenance |

---

## PR Checklist

Before submitting:

- [ ] Issue is assigned to me
- [ ] PR links an issue
- [ ] Changes are focused and minimal
- [ ] No unnecessary dependencies added
- [ ] Code follows repository architecture
- [ ] I tested changes locally
- [ ] I understand the code submitted

For UI changes:

- [ ] Screenshots attached

---

## AI-Generated Contributions Policy

AI assistance is **allowed**. However:

- Blindly generated PRs are prohibited
- Contributors must understand submitted code
- Low-quality AI spam is rejected
- Fake complexity is prohibited
- Meaningless documentation spam is prohibited

All PRs are reviewed for:

- Code quality
- Context accuracy
- Implementation understanding
- Contribution relevance

---

## Strictly Prohibited

The following may result in rejection:

- Fake complexity
- Spam PRs
- Duplicate PRs
- Copied code without attribution
- Low-effort documentation spam
- Meaningless formatting-only PRs
- Unnecessary dependency additions
- Claiming issues without intent to work
- Excessive maintainer pinging

---

## Maintainer Ping Policy

Avoid repeatedly pinging maintainers for issue assignment, mentor review, merge requests, labels, or review escalation.

**Recommended waiting periods:**

| Action | Recommended Wait |
|--------|-----------------|
| Mentor approval | 24 hours |
| Maintainer review | 24–72 hours |
| Assignment review | Up to 24 hours |

Mentor review rotation is automated. Repeated spam pings may result in comment cleanup, assignment removal, or spam labeling.

---

## Inactivity Policy

Assigned issues with no meaningful progress for **7 days** may be automatically unassigned.

Meaningful progress includes:

- Issue updates
- Linked PR creation
- Implementation discussion
- Active development progress

Contributors may need to wait before reclaiming inactive issues.

---

## Automation Features

The repository includes:

- AI issue triage
- Duplicate issue detection
- Mentor auto-rotation
- Smart assignment queueing
- Weighted mentor selection
- Contributor leaderboard automation
- Mentor leaderboard automation
- Review quality scoring
- Stale PR cleanup
- DCO enforcement
- PR size labeling
- AI-slop detection
- LLM PR validation
- Workflow-based review gates

---

## Testing

Before submitting:

```bash
vercel dev
```

Verify:

- Edge functions work correctly
- No build tooling was introduced
- No existing functionality breaks
- Responsive layout remains functional
- APIs behave correctly

---

## Need Help?

If you need help:

- Open a [GitHub Issue](https://github.com/S3DFX-CYBER/GSoC-Org-Finder-/issues)
- Use [GitHub Discussions](https://github.com/S3DFX-CYBER/GSoC-Org-Finder-/discussions)
- Ask in the community server

---

## Final Notes

This repository prioritizes:

- Quality over quantity
- Maintainable contributions
- Fair contributor practices
- Meaningful improvements
- Human-reviewed code quality

Not all PRs are guaranteed to be merged.

Thank you for contributing to FindMyGSoC 🚀
=======
# **Contributing Guidelines** 📄

This documentation contains a set of guidelines to help you during the contribution process.
We are happy to welcome all the contributions from anyone willing to improve/add new scripts to this project.
Thank you for helping out and remember, **no contribution is too small.**
<br>
Please note we have a [code of conduct](CODE_OF_CONDUCT.md)  please follow it in all your interactions with the project.


<br>

## **Need some help regarding the basics?🤔**


You can refer to the following articles on basics of Git and Github and also contact the Project Mentors,
in case you are stuck:

- [Forking a Repo](https://help.github.com/en/github/getting-started-with-github/fork-a-repo)
- [Cloning a Repo](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository)
- [How to create a Pull Request](https://opensource.com/article/19/7/create-pull-request-github)
- [Getting started with Git and GitHub](https://towardsdatascience.com/getting-started-with-git-and-github-6fcd0f2d4ac6)
- [Learn GitHub from Scratch](https://docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources)

<br>

**1.** Fork [this](https://github.com/ronisarkarexe/story-spark-ai.git) repository.

**2.** Clone your forked copy of the project.

```
git clone https://github.com/<your_user_name>/story-spark-ai.git
```

**3.** Navigate to the project directory :file_folder: .

```
cd story-spark-ai
```

**4.** Add a reference(remote) to the original repository.

```
git remote add upstream https://github.com/ronisarkarexe/story-spark-ai.git
```

**5.** Check the remotes for this repository.

```
git remote -v
```

**6.** Always take a pull from the upstream repository to your main branch to keep it at par with the main project (updated repository).

```
git pull upstream main
```

**7.** Create a new branch.

```
git checkout -b <your_branch_name>
```

**8.** Perform your desired changes to the code base.

**9.** Track your changes:heavy_check_mark: .

```
git add .
```

**10.** Commit your changes .

```
git commit -m "Relevant message"
```

**11.** Push the committed changes in your feature branch to your remote repo.

```
git push -u origin <your_branch_name>
```

**12.** To create a pull request, click on `compare and pull requests`.

**13.** Add appropriate title and description to your pull request explaining your changes and efforts done.

**14.** Click on `Create Pull Request`.
   
<br>

### Alternatively contribute using GitHub Desktop

1. **Open GitHub Desktop:**
   Launch GitHub Desktop and log in to your GitHub account if you haven't already.

2. **Clone the Repository:**
   - If you haven't cloned the story-spark-ai repository yet, you can do so by clicking on the "File" menu and selecting "Clone Repository."
   - Choose the story-spark-ai repository from the list of repositories on GitHub and clone it to your local machine.

3. **Switch to the Correct Branch:**
   - Ensure you are on the branch that you want to submit a pull request for.
   - If you need to switch branches, you can do so by clicking on the "Current Branch" dropdown menu and selecting the desired branch.

4. **Make Changes:**
   Make your changes to the code or files in the repository using your preferred code editor.

5. **Commit Changes:**
   - In GitHub Desktop, you'll see a list of the files you've changed. Check the box next to each file you want to include in the commit.
   - Enter a summary and description for your changes in the "Summary" and "Description" fields, respectively. Click the "Commit to <branch-name>" button to commit your changes to the local branch.

6. **Push Changes to GitHub:**
   After committing your changes, click the "Push origin" button in the top right corner of GitHub Desktop to push your changes to your forked repository on GitHub.

7. **Create a Pull Request:**
   - Go to the GitHub website and navigate to your fork of the story-spark-ai repository.
   - You should see a button to "Compare & pull request" between your fork and the original repository. Click on it.

8. **Review and Submit:**
   - On the pull request page, review your changes and add any additional information, such as a title and description, that you want to include with your pull request.
   - Once you're satisfied, click the "Create pull request" button to submit your pull request.

9. **Wait for Review:**
    Your pull request will now be available for review by the project maintainers. They may provide feedback or ask for changes before merging your pull request into the main branch of the story-spark-ai repository.

⭐️ Support the Project
If you find this project helpful, please consider giving it a star on GitHub! Your support helps to grow the project and reach more contributors.

## **Issue Report Process 📌**

1. Go to the project's issues.
2. Give proper description for the issues.
3. Don't spam to get the assignment of the issue 😀.
4. Wait until someone is looking into it ! 
5. Start working on issue only after you got assigned that issue 🚀.

<br>

However, it's important to adhere to strict regulations to maintain the integrity of our contributor records:

1. Only Add Your Details: You are allowed to add your own details to the ContributorsData.ts file. This helps us accurately attribute contributions to the right individuals.

2. Respect Others' Details: Modifying or tampering with existing contributor details is strictly prohibited. Any unauthorized changes may result in your PR not being merged or accepted.

We understand that open source collaboration is filled with excitement and fulfillment. Your contributions are invaluable, and we're committed to ensuring that your efforts are duly recognized and appreciated.

## **Pull Request Process 🚀**

1. Ensure that you have self reviewed your code 😀
2. Make sure you have added the proper description for the functionality of the code
3. Ensure you have commented your code, particularly in hard-to-understand areas.
4. Add screenshots — they help in the review process.
5. Submit your PR by giving the necessary information in PR template and hang tight we will review it really soon 🚀

<br>

# **Thank you for contributing💗** 
>>>>>>> upstream/main
