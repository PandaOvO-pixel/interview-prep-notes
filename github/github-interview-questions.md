# GitHub & Git Interview Questions & Answers

## 1. What is Git?

**Answer:** Git is a distributed version control system for tracking changes in source code during software development.

**Key Features:**
- **Distributed:** Every developer has full repository copy
- **Fast:** Local operations are quick
- **Branching:** Easy branch creation and merging
- **Data Integrity:** SHA-1 hash ensures data integrity
- **Free & Open Source**

**Why Git:**
- Collaboration
- Version tracking
- Branching and merging
- Backup and restore

---

## 2. What is the difference between Git and GitHub?

**Answer:**

| Feature | Git | GitHub |
|---------|-----|--------|
| Type | Version control system | Hosting service |
| Purpose | Track code changes | Store and share repositories |
| Location | Local computer | Cloud (web-based) |
| Installation | Requires installation | Web browser access |
| Competition | Mercurial, SVN | GitLab, Bitbucket |
| Functionality | Command-line tool | GUI + collaboration features |

**Interview Tip:** Git is the tool, GitHub is the platform that hosts Git repositories.

---

## 3. What are the basic Git commands?

**Answer:**

**Configuration:**
- `git config --global user.name "Name"` - Set name
- `git config --global user.email "email"` - Set email

**Repository:**
- `git init` - Initialize repository
- `git clone <url>` - Clone remote repository

**Changes:**
- `git status` - Check status
- `git add <file>` - Stage file
- `git add .` - Stage all files
- `git commit -m "message"` - Commit changes

**Remote:**
- `git push` - Upload to remote
- `git pull` - Download from remote
- `git fetch` - Download without merging

**Branching:**
- `git branch` - List branches
- `git branch <name>` - Create branch
- `git checkout <branch>` - Switch branch
- `git merge <branch>` - Merge branch

---

## 4. What is the difference between git pull and git fetch?

**Answer:**

**git fetch:**
- Downloads changes from remote
- Doesn't merge automatically
- Safe (doesn't modify working directory)
- Review before merging

**git pull:**
- Downloads + merges automatically
- `git pull = git fetch + git merge`
- Direct update to working directory
- Can cause merge conflicts

**Interview Tip:** Use fetch to review changes, pull when you want automatic merge.

---

## 5. What is the difference between git merge and git rebase?

**Answer:**

**git merge:**
- Combines branches with merge commit
- Preserves complete history
- Non-destructive
- Creates merge commit
- Better for public branches

**git rebase:**
- Re-applies commits on top of another branch
- Linear history
- Rewrites commit history
- No merge commit
- Better for feature branches

**Interview Tip:** Never rebase public/shared branches; use for local feature branches only.

---

## 6. What are Git branches?

**Answer:** Branches are independent lines of development in repository.

**Purpose:**
- Parallel development
- Isolate features
- Experiment safely
- Maintain stable releases

**Common Branches:**
- **main/master:** Production-ready code
- **develop:** Integration branch
- **feature:** New features
- **hotfix:** Emergency fixes
- **release:** Prepare releases

**Benefits:**
- Safe experimentation
- Team collaboration
- Multiple versions

---

## 7. What is the difference between git reset and git revert?

**Answer:**

**git reset:**
- Moves HEAD to specific commit
- Rewrites history
- Dangerous on shared branches
- Types: --soft, --mixed, --hard
- Use for local changes

**git revert:**
- Creates new commit that undoes changes
- Preserves history
- Safe for shared branches
- Doesn't rewrite history
- Use for published commits

**Interview Tip:** Reset for local mistakes, revert for published changes.

---

## 8. What is git stash?

**Answer:** Git stash temporarily saves changes without committing, allowing you to work on something else.

**Commands:**
- `git stash` - Save changes
- `git stash list` - List stashes
- `git stash pop` - Apply and remove first stash
- `git stash apply` - Apply without removing
- `git stash drop` - Delete stash
- `git stash clear` - Remove all stashes

**Use Cases:**
- Switch branches without committing
- Pull latest changes
- Experiment without losing work

---

## 9. What is a merge conflict and how to resolve it?

**Answer:** Merge conflict occurs when Git can't automatically merge changes from different branches.

**Causes:**
- Same line modified in both branches
- File deleted in one branch, modified in another
- Different changes to same file

**Resolution Steps:**
1. Identify conflicted files (`git status`)
2. Open files and find conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
3. Edit file to resolve conflict
4. Remove conflict markers
5. Stage resolved files (`git add`)
6. Commit merge (`git commit`)

**Interview Tip:** Communication prevents many conflicts; pull frequently, commit often.

---

## 10. What is .gitignore file?

**Answer:** .gitignore specifies files and directories that Git should ignore.

**Common Entries:**
- Build outputs (`/dist`, `/build`)
- Dependencies (`node_modules/`, `venv/`)
- IDE files (`.vscode/`, `.idea/`)
- OS files (`.DS_Store`, `Thumbs.db`)
- Environment files (`.env`)
- Log files (`*.log`)

**Patterns:**
- `*.txt` - All .txt files
- `folder/` - Entire folder
- `!important.txt` - Exception (don't ignore)

**Interview Tip:** Add .gitignore before first commit to avoid tracking unwanted files.

---

## 11. What is git cherry-pick?

**Answer:** Cherry-pick applies specific commit from one branch to another.

**Syntax:** `git cherry-pick <commit-hash>`

**Use Cases:**
- Apply bug fix to multiple branches
- Recover specific changes
- Move commit to different branch

**vs Merge:**
- Cherry-pick: Specific commits
- Merge: All commits from branch

---

## 12. What are Git tags?

**Answer:** Tags mark specific points in Git history, typically for releases.

**Types:**

**Lightweight Tag:**
- Just a pointer to commit
- `git tag v1.0`

**Annotated Tag:**
- Full object with metadata
- `git tag -a v1.0 -m "Version 1.0"`
- Recommended for releases

**Commands:**
- `git tag` - List tags
- `git tag <name>` - Create tag
- `git push origin <tag>` - Push specific tag
- `git push origin --tags` - Push all tags

---

## 13. What is HEAD in Git?

**Answer:** HEAD is a pointer to current branch reference, indicating where you are in repository.

**States:**

**Normal (Attached HEAD):**
- Points to branch
- `HEAD -> main`

**Detached HEAD:**
- Points directly to commit
- Not on any branch
- Changes not saved without creating branch

**Usage:**
- `HEAD` - Current commit
- `HEAD~1` - One commit back
- `HEAD~2` - Two commits back
- `HEAD^` - Parent commit

---

## 14. What is git blame?

**Answer:** Git blame shows who last modified each line of a file and when.

**Syntax:** `git blame <file>`

**Purpose:**
- Find who wrote specific code
- Understand code history
- Track when changes made
- Not for blaming, for understanding!

**Interview Tip:** Despite the name, it's for investigation, not accusation.

---

## 15. What is git log?

**Answer:** Git log displays commit history.

**Useful Options:**
- `git log` - Full history
- `git log --oneline` - Compact view
- `git log --graph` - Visual branch graph
- `git log --author="Name"` - Filter by author
- `git log --since="2 weeks ago"` - Filter by date
- `git log -n 5` - Last 5 commits
- `git log <file>` - History of specific file

---

## 16. What is the difference between fork and clone?

**Answer:**

**Fork:**
- Creates copy on GitHub (remote)
- Used for contributing to others' projects
- Creates independent repository
- Can create pull requests
- Server-side operation

**Clone:**
- Creates copy on local machine
- Downloads existing repository
- Connected to original remote
- Local operation

**Workflow:** Fork (remote copy) → Clone (local copy) → Make changes → Push → Pull Request

---

## 17. What is a Pull Request?

**Answer:** Pull Request (PR) is a request to merge changes from one branch into another.

**Purpose:**
- Code review
- Discussion
- Quality control
- Documentation

**Workflow:**
1. Create feature branch
2. Make changes and commit
3. Push to remote
4. Create pull request
5. Review and discussion
6. Approve and merge

**Interview Tip:** PRs facilitate collaboration and maintain code quality through review.

---

## 18. What is the difference between origin and upstream?

**Answer:**

**origin:**
- Your remote repository
- Your fork (if forked)
- Default remote name
- Where you push changes

**upstream:**
- Original repository (if forked)
- Source of your fork
- Fetch updates from here
- Keep fork synchronized

**Setup upstream:**
`git remote add upstream <original-repo-url>`

---

## 19. What is git reflog?

**Answer:** Reflog (reference log) records all reference updates in local repository.

**Purpose:**
- Recover lost commits
- Find deleted branches
- Undo mistakes
- Safety net

**Usage:**
- `git reflog` - View history
- `git reset --hard HEAD@{2}` - Go back to specific state

**Interview Tip:** Reflog can save you from almost any Git mistake.

---

## 20. What are Git workflows?

**Answer:** Git workflows are branching strategies for collaboration.

**Common Workflows:**

**1. Centralized:**
- Single main branch
- Everyone commits to main
- Simple, small teams

**2. Feature Branch:**
- New branch for each feature
- Merge when complete
- Most common

**3. Gitflow:**
- main, develop, feature, release, hotfix branches
- Structured release management
- Larger projects

**4. Forking:**
- Fork repository
- Make changes in fork
- Pull request to original
- Open source projects

**5. Trunk-Based:**
- Short-lived branches
- Frequent commits to main
- Continuous integration

---

## 21. What is GitHub Actions?

**Answer:** GitHub Actions is CI/CD platform for automating workflows.

**Use Cases:**
- Run tests automatically
- Build and deploy applications
- Code linting
- Release automation
- Notifications

**Components:**
- **Workflow:** Automated process
- **Event:** Trigger (push, pull request)
- **Job:** Set of steps
- **Runner:** Server executing jobs

**File:** `.github/workflows/name.yml`

---

## 22. What is the difference between public and private repository?

**Answer:**

**Public Repository:**
- Visible to everyone
- Anyone can clone/fork
- Open source projects
- Free unlimited

**Private Repository:**
- Visible only to you and collaborators
- Controlled access
- Proprietary code
- Free with limitations

**When to use:**
- Public: Open source, portfolio, learning
- Private: Commercial, sensitive data, work in progress

---

## 23. What is git bisect?

**Answer:** Git bisect helps find specific commit that introduced a bug using binary search.

**How it works:**
1. `git bisect start`
2. `git bisect bad` - Mark current as bad
3. `git bisect good <commit>` - Mark known good commit
4. Test current commit
5. Mark as good or bad
6. Repeat until bug found

**Interview Tip:** Efficiently finds problematic commit in large history.

---

## 24. What are Git hooks?

**Answer:** Git hooks are scripts that run automatically at specific Git events.

**Types:**

**Client-Side:**
- pre-commit: Before commit
- prepare-commit-msg: Before commit message
- commit-msg: After commit message
- post-commit: After commit
- pre-push: Before push

**Server-Side:**
- pre-receive: Before accepting push
- update: Per branch
- post-receive: After accepting push

**Use Cases:**
- Code linting
- Run tests
- Enforce commit message format
- Prevent sensitive data commits

**Location:** `.git/hooks/`

---

## 25. What is git diff?

**Answer:** Git diff shows differences between commits, branches, or working directory.

**Common Usage:**
- `git diff` - Unstaged changes
- `git diff --staged` - Staged changes
- `git diff HEAD` - All changes since last commit
- `git diff branch1 branch2` - Between branches
- `git diff commit1 commit2` - Between commits

**Interview Tip:** Essential for reviewing changes before committing.

---

## 26. What is the .git folder?

**Answer:** .git folder contains all repository metadata and Git database.

**Contents:**
- **HEAD** - Current branch pointer
- **config** - Repository configuration
- **hooks/** - Git hooks scripts
- **objects/** - Git objects (commits, trees, blobs)
- **refs/** - References (branches, tags)
- **index** - Staging area

**Interview Tip:** Deleting .git folder removes all Git history (be careful!).

---

## 27. What is git clean?

**Answer:** Git clean removes untracked files from working directory.

**Options:**
- `git clean -n` - Dry run (preview)
- `git clean -f` - Force clean
- `git clean -fd` - Remove directories too
- `git clean -fx` - Include ignored files

**Use Case:** Remove build artifacts, temporary files

**Caution:** Cannot undo! Preview first with -n.

---

## 28. What is the difference between git rm and rm?

**Answer:**

**git rm:**
- Removes file from Git and working directory
- Stages deletion
- Git tracked operation

**rm (or delete manually):**
- Only removes from working directory
- Need to stage separately (`git add`)
- OS level operation

**Interview Tip:** Use `git rm` to properly remove tracked files.

---

## 29. What is a detached HEAD state?

**Answer:** Detached HEAD occurs when HEAD points directly to commit instead of branch.

**Causes:**
- Checking out specific commit
- Checking out tag
- `git checkout <commit-hash>`

**Risks:**
- Changes can be lost
- Not on any branch

**Fix:**
1. Create branch: `git checkout -b new-branch`
2. Or discard changes: `git checkout main`

---

## 30. What are best practices for Git commit messages?

**Answer:**

**Format:**
- First line: Short summary (50 chars)
- Blank line
- Detailed description (if needed)

**Guidelines:**
- Use imperative mood ("Add feature" not "Added feature")
- Capitalize first letter
- No period at end of subject
- Explain what and why, not how
- Reference issues/tickets

**Good Examples:**
- "Fix login bug for mobile users"
- "Add user authentication module"
- "Update dependencies to latest versions"

**Bad Examples:**
- "fix stuff"
- "WIP"
- "asdf"

**Interview Tip:** Clear commit messages are documentation for future you and teammates.

---
## 31. What is a Git tag?

**Answer:** Tag is reference to specific point in Git history, typically used for releases.

**Types:**
- **Lightweight:** Simple pointer to commit
- **Annotated:** Full object with tagger info, date, message (recommended)

**Use Cases:**
- Mark release versions (v1.0, v2.0)
- Important milestones
- Stable points

**Commands:**
- Create: `git tag v1.0`
- Push: `git push origin v1.0`
- List: `git tag`

---

## 32. What is Git bisect?

**Answer:** Git bisect uses binary search to find commit that introduced bug.

**How it works:**
1. Start bisect: `git bisect start`
2. Mark bad commit: `git bisect bad`
3. Mark good commit: `git bisect good <commit>`
4. Git checks out middle commit
5. Test and mark as good/bad
6. Repeat until bug found

**Benefit:** Efficiently find problematic commit in large history

---

## 33. What is the difference between `git pull` and `git fetch`?

**Answer:**

**git fetch:**
- Downloads changes from remote
- Doesn't merge
- Safe operation
- Updates remote tracking branches

**git pull:**
- Fetches + merges
- `git pull = git fetch + git merge`
- Can cause conflicts
- Updates working directory

**Best Practice:** Use fetch to review changes before merging

---

## 34. What is GitHub Actions?

**Answer:** GitHub Actions is CI/CD platform that automates workflows.

**Features:**
- Trigger on events (push, PR, schedule)
- Run tests automatically
- Deploy applications
- Custom workflows
- Matrix builds

**Components:**
- **Workflows:** Automated processes
- **Jobs:** Steps that run on same runner
- **Actions:** Reusable units of code

**Use Cases:** Testing, building, deploying, notifications

---

## 35. What is a Git hook?

**Answer:** Git hooks are scripts that run automatically on certain Git events.

**Client-side Hooks:**
- pre-commit: Before commit
- prepare-commit-msg: Before commit message editor
- commit-msg: Validate commit message
- post-commit: After commit

**Server-side Hooks:**
- pre-receive: Before push accepted
- update: Like pre-receive per branch
- post-receive: After push accepted

**Use Cases:** Linting, testing, message validation, notifications

---

## 36. What is Git reflog?

**Answer:** Reflog records when branch tips and HEAD were updated.

**Purpose:**
- Recover lost commits
- Undo mistakes
- See local history

**Use Cases:**
- Recover after reset
- Find "lost" commits
- Restore deleted branches

**Command:** `git reflog`
**Note:** Local only, expires after 90 days (default)

---

## 37. What is Cherry-picking?

**Answer:** Cherry-picking applies specific commit from one branch to another.

**Command:** `git cherry-pick <commit-hash>`

**Use Cases:**
- Apply bug fix to multiple branches
- Port specific feature
- Include specific changes without merging entire branch

**Caution:** Creates duplicate commits, prefer merging when possible

---

## 38. What is .gitignore?

**Answer:** .gitignore specifies files Git should ignore.

**Common Ignores:**
- Build outputs (`/dist`, `/build`)
- Dependencies (`node_modules/`)
- IDE files (`.vscode/`, `.idea/`)
- Environment files (`.env`)
- Log files (`*.log`)
- OS files (`.DS_Store`)

**Patterns:**
- `*.txt`: All txt files
- `!important.txt`: Exception
- `folder/`: Entire directory

**Note:** Already tracked files not affected

---

## 39. What is a Pull Request (PR)?

**Answer:** Pull Request proposes changes from one branch to another for review and merge.

**Purpose:**
- Code review
- Discussion
- Quality assurance
- Collaboration

**Workflow:**
1. Create feature branch
2. Make changes
3. Open PR
4. Review and discuss
5. Approve and merge

**Best Practices:** Small PRs, clear description, link issues, respond to feedback

---

## 40. What is Git workflow?

**Answer:** Git workflow is branching strategy for collaboration.

**Common Workflows:**

**Git Flow:**
- master, develop, feature, release, hotfix branches
- Structured, good for releases

**GitHub Flow:**
- main branch + feature branches
- Simple, continuous deployment

**GitLab Flow:**
- Environment branches (staging, production)
- Issue tracking integration

**Trunk-Based:**
- Short-lived branches
- Frequent integration

---

## 41. What is Git blame?

**Answer:** Git blame shows who last modified each line of file.

**Purpose:**
- Find who changed line
- Understand change history
- Contact author for questions

**Command:** `git blame <file>`

**Alternative:** Use `git log -p` for detailed history

**Use Responsibly:** Focus on understanding, not blaming

---

## 42. What is a Git submodule?

**Answer:** Submodule is repository embedded inside another repository.

**Use Cases:**
- Include external libraries
- Share code between projects
- Manage dependencies

**Commands:**
- Add: `git submodule add <url>`
- Init: `git submodule init`
- Update: `git submodule update`

**Drawbacks:** Complex workflow, easier alternatives exist (npm, pip)

---

## 43. What is the difference between `git reset` and `git revert`?

**Answer:**

**git reset:**
- Moves branch pointer backward
- Rewrites history
- Use for local commits
- Three modes: soft, mixed, hard

**git revert:**
- Creates new commit undoing changes
- Preserves history
- Safe for shared branches
- Best for public commits

**Rule:** Reset private history, revert public history

---

## 44. What is Git squash?

**Answer:** Squashing combines multiple commits into single commit.

**Benefits:**
- Clean history
- Logical commits
- Easier to review
- Remove work-in-progress commits

**Methods:**
- Interactive rebase: `git rebase -i`
- Squash merge: GitHub/GitLab option

**When:** Before merging feature branch to main

---

## 45. What is force push?

**Answer:** Force push overwrites remote branch with local branch, ignoring conflicts.

**Command:** `git push --force` or safer `git push --force-with-lease`

**When to Use:**
- After rebasing
- After amending commits
- Cleaning up history

**Dangers:**
- Overwrites others' work
- Loses commits
- Breaks collaborators' branches

**Rule:** Never force push to shared branches (main, develop)

---