<div align="center" style="display: flex; align-items: center; justify-content: center; gap: 15px;">
  <h1 style="margin: 0;">GitLab Basics – Hands-On Workflow Guide</h1>
</div>

<p align="center">
  This document explains the **basic Git + GitLab workflow** using a real example.
It covers repositories, commits, branches, merge requests, and synchronization
between local and remote repositories.

</p>


## 1. What Is Git vs GitLab?

### Git
- **Git** is a **distributed version control system**
- Runs locally on your machine
- Tracks file changes via **commits**
- Supports **branching**, **merging**, and **history**

### GitLab
- **GitLab** is a **remote Git hosting platform**
- Stores repositories on a server
- Adds collaboration features:
  - Remote repositories (`origin`)
  - Branch protection
  - Merge Requests (MRs)
  - CI/CD (not covered here)

> Think of Git as the engine, and GitLab as the collaboration hub.

---

## 2. Repository Structure

After cloning or creating a repository, you typically see:

```bash
mc1862@cell11-cse:~/demo$ ls -al
total 16
drwxr-xr-x 4 mc1862 domain^users 4096 Feb  7 23:43 .
drwx------ 7 mc1862 domain^users 4096 Feb  8 00:30 ..
drwxr-xr-x 3 mc1862 domain^users 4096 Feb  7 23:43 demo
drwxr-xr-x 7 mc1862 domain^users 4096 Feb  7 23:36 .git  # Git metadata (history, branches, config)
```
- `.git/` must never be deleted
- Everything else is project content
---

## 3. Basic Git Lifecycle
### 3.1 Create or Modify Files
```bash
mc1862@cell11-cse:~/demo$ cd demo
mc1862@cell11-cse:~/demo/demo$ touch index.html app.css
```
## 3.2 Stage Changes

```bash
mc1862@cell11-cse:~/demo/demo$ git add .
```
- Moves changes into the staging area.

## 3.3 Commit Changes

```bash
mc1862@cell11-cse:~/demo/demo$ git commit -m 'add html and css files'
[master c28021f] add html and css files
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 app.css
 create mode 100644 index.html
```
- Creates a snapshot of the project at that moment.
---
## 4. Deleting and Renaming Files (Git Is Smart)
```bash
mc1862@cell11-cse:~/demo/demo$ rm index.html 
mc1862@cell11-cse:~/demo/demo$ touch app.js
```
- Show the changes.
```bash
mc1862@cell11-cse:~/demo/demo$ ls
app.css  app.js  README.md
```
- Moves changes into the staging area and commit it.
```bash
mc1862@cell11-cse:~/demo/demo$ git add .
mc1862@cell11-cse:~/demo/demo$ git commit -m 'delete html and add app.js'
[master d37a632] delete html and add app.js
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename index.html => app.js (100%)
```
---
### 5. Viewing History
```bash
mc1862@cell11-cse:~/demo/demo$ git log
commit d37a632b63fe1665df95a8fb84f0fc8a8e67a8d2 (HEAD -> master)
Author: Mav <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 01:07:17 2026 -0600

    delete html and add app.js

commit c28021ffcdb6ac73db0d022a9688128a27c85b83    ## Let us move to this snapshot. copy commit ID: c28021ffcdb6ac73db0d022a9688128a27c85b83
Author: Mav <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 01:05:12 2026 -0600

    add html and css files

commit 106f816178769aebbd7fbb9310056cff9fa3dccb (origin/master, origin/HEAD)
Author: Cheung, Maverick <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 05:33:12 2026 +0000

    Initial commit

```
---
## 6. Detached HEAD (Important Concept)
```bash
mc1862@cell11-cse:~/demo/demo$ git checkout c28021ffcdb6ac73db0d022a9688128a27c85b83  #git checkout commit ID we just copied
Note: switching to 'c28021ffcdb6ac73db0d022a9688128a27c85b83'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at c28021f add html and css files

```
- This puts you in detached HEAD state:
    - You are viewing an old snapshot
    - You are not on a branch
    - Commits made here can be lost

> Verify if everything went back to the snapshot we commit.
```bash
mc1862@cell11-cse:~/demo/demo$ ls
app.css  index.html  README.md
```
Check out log again
```bash
mc1862@cell11-cse:~/demo/demo$ git log
commit c28021ffcdb6ac73db0d022a9688128a27c85b83 (HEAD)
Author: Mav <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 01:05:12 2026 -0600

    add html and css files

commit 106f816178769aebbd7fbb9310056cff9fa3dccb (origin/master, origin/HEAD)
Author: Cheung, Maverick <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 05:33:12 2026 +0000

    Initial commit
```
> QUESTION: Can We still go back to the newest snapshot we commit?

```bash
mc1862@cell11-cse:~/demo/demo$ git checkout d37a632b63fe1665df95a8fb84f0fc8a8e67a8d2
Previous HEAD position was c28021f add html and css files
HEAD is now at d37a632 delete html and add app.js
mc1862@cell11-cse:~/demo/demo$ ls
app.css  app.js  README.md  #Yes, we can!
```
---
## 7. Branches
### 7.1 List Branches
```bash
mc1862@cell11-cse:~/demo/demo$ git branch
* (HEAD detached at c28021f)
  master
```
> Push everything under git repo to remote origin.
```bash
mc1862@cell11-cse:~/demo/demo$ git push origin master 
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 2 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 508 bytes | 508.00 KiB/s, done.
Total 5 (delta 1), reused 0 (delta 0), pack-reused 0
To csegitlab.engineering.unt.edu:mc1862/demo.git
   106f816..d37a632  master -> master
```
![alt text](<Screenshot git push.png>)

### 7.2 Create and Switch to a Branch
```bash
mc1862@cell11-cse:~/demo/demo$ git checkout -b backend
Switched to a new branch 'backend'

mc1862@cell11-cse:~/demo/demo$ git branch
* backend
  master

mc1862@cell11-cse:~/demo/demo$ git log
commit c28021ffcdb6ac73db0d022a9688128a27c85b83 (HEAD -> backend)    ## Now we can see the HEAD is on 'backend' branch
Author: Mav <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 01:05:12 2026 -0600

    add html and css files

commit 106f816178769aebbd7fbb9310056cff9fa3dccb
Author: Cheung, Maverick <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 05:33:12 2026 +0000

    Initial commit

```

Now:
- backend branch diverges from master
- Safe place to develop new features

## 8. Working on a Feature Branch

```bash
mc1862@cell11-cse:~/demo/demo$ touch app.py
```
```bash
mc1862@cell11-cse:~/demo/demo$ ls
app.css  app.py  index.html  README.md
```
```bash
mc1862@cell11-cse:~/demo/demo$ git add .
mc1862@cell11-cse:~/demo/demo$ git commit -m 'add app.py on backend branch'
[backend 48b8eee] add app.py on backend branch
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 app.py
mc1862@cell11-cse:~/demo/demo$ git log
commit 48b8eeeac4bfe22f56c0bfa5212e1ccd1eadca06 (HEAD -> backend)
Author: Mav <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 01:27:49 2026 -0600

    add app.py on backend branch

commit c28021ffcdb6ac73db0d022a9688128a27c85b83
Author: Mav <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 01:05:12 2026 -0600

    add html and css files

commit 106f816178769aebbd7fbb9310056cff9fa3dccb
Author: Cheung, Maverick <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 05:33:12 2026 +0000

    Initial commit
```
This commit exists only on `backend`.
---
## 9. Pushing to GitLab

Push a new branch
```bash
mc1862@cell11-cse:~/demo/demo$ git push origin backend 
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 2 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 240 bytes | 240.00 KiB/s, done.
Total 2 (delta 1), reused 0 (delta 0), pack-reused 0
remote: 
remote: To create a merge request for backend, visit:
remote:   https://csegitlab.engineering.unt.edu/mc1862/demo/-/merge_requests/new?merge_request%5Bsource_branch%5D=backend
remote: 
To csegitlab.engineering.unt.edu:mc1862/demo.git
 * [new branch]      backend -> backend
```
GitLab now knows about:
- `master`
- `backend`





## 10. Merge Requests (GitLab Feature)

A **Merge Request (MR)** in GitLab is used to merge changes from one branch
(e.g., `backend`) into another branch (usually `master`).  
This allows review, comparison, and controlled integration of code.

---

### 10.1 Viewing Multiple Branches

After pushing the `backend` branch to GitLab, the repository now contains
**two branches**.

![alt text](<images/Screenshot newbranch.png>)

> This page shows all branches currently available in the repository.

![alt text](<images/Screenshot newbranch2.png>)

> Here we can clearly see the `backend` branch in addition to the main branch
> (`master`).

This indicates that development work is happening on a separate branch,
which is the recommended Git workflow.

---

### 10.2 Creating a Merge Request

To merge the `backend` branch into `master`, we create a **Merge Request**.

- Click the **`Compare`** button next to the `backend` branch.

![alt text](<images/Screenshot newbranch3.png>)

GitLab automatically prepares a comparison view.

![alt text](<images/Screenshot newbranch4.png>)

- **Source branch:** `backend`
- **Target branch:** `master`
- The file `app.py` is listed, showing that this file is the change introduced
  by the `backend` branch.

This comparison allows us to verify exactly **what will change** before merging.

---

### 10.3 Submitting the Merge Request

- Click **`Create merge request`**.

![alt text](<images/Screenshot newbranch5.png>)

- Add a **title** and **description** explaining:
  - What changes were made
  - Why the changes were made
  - Any relevant implementation details

- Click **`Create merge request`** again to submit it.

![alt text](<images/Screenshot newbranch6.png>)

At this point, the Merge Request is open and ready to be merged.

---

### 10.4 Merging the Branch

- Click **`Merge`** to merge `backend` into `master`.

>This creates a **merge commit** with the message:

![alt text](<images/Screenshot newbranch7.png>)

Once completed, GitLab confirms that the merge was successful.



---

### 10.5 Visualizing the Merge

GitLab provides a graphical representation of the branch history.

- Navigate to **Repository → Graph**

![alt text](<images/Screenshot newbranch8.png>)

This graph shows:
- Where the `backend` branch diverged from `master`
- Where it was merged back into `master`

---

### 10.6 Final Repository State

After the merge:
- Only one active branch remains: `master`
- The changes from `backend` are now part of `master`
- The `backend` branch is no longer needed

![alt text](<images/Screenshot newbranch9.png>)
This confirms that the feature development process is complete and
successfully integrated.

---
## 11. Pulling Updates After a Merge

If GitLab merges branches remotely, your local repo must sync:
```bash
mc1862@cell11-cse:~/demo/demo$ git pull origin master 
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 2 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (2/2), 298 bytes | 18.00 KiB/s, done.
From csegitlab.engineering.unt.edu:mc1862/demo
 * branch            master     -> FETCH_HEAD
   d37a632..5434d2f  master     -> origin/master
Updating 48b8eee..5434d2f
Fast-forward
 index.html => app.js | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename index.html => app.js (100%)

```
This:
- Updates local `master`
- Fast-forwards history
- Brings merged files (e.g., `app.py`)

### 11.1 Verify 
```bash
mc1862@cell11-cse:~/demo/demo$ git log
commit 5434d2f1274b0709577fc96ceb0b731a0f01b9d1 (HEAD -> backend, origin/master, origin/HEAD)
Merge: d37a632 48b8eee
Author: Cheung, Maverick <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 07:41:59 2026 +0000

    Merge branch 'backend' into 'master'
    
    add app.py on backend branch
    
    See merge request mc1862/demo!1

commit 48b8eeeac4bfe22f56c0bfa5212e1ccd1eadca06 (origin/backend)
Author: Mav <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 01:27:49 2026 -0600

    add app.py on backend branch

commit d37a632b63fe1665df95a8fb84f0fc8a8e67a8d2 (master)
Author: Mav <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 01:07:17 2026 -0600

    delete html and add app.js

commit c28021ffcdb6ac73db0d022a9688128a27c85b83
Author: Mav <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 01:05:12 2026 -0600

    add html and css files

commit 106f816178769aebbd7fbb9310056cff9fa3dccb
Author: Cheung, Maverick <maverickcheung@my.unt.edu>
Date:   Sun Feb 8 05:33:12 2026 +0000

    Initial commit
```
And we see we are still on the `backend` Branch locally
```bash
mc1862@cell11-cse:~/demo/demo$ git branch 
* backend
  master
```
And we switch back to `master`
```bash
mc1862@cell11-cse:~/demo/demo$ git checkout master 
Switched to branch 'master'
Your branch is behind 'origin/master' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)
mc1862@cell11-cse:~/demo/demo$ git pull origin master 
From csegitlab.engineering.unt.edu:mc1862/demo
 * branch            master     -> FETCH_HEAD
Updating d37a632..5434d2f
Fast-forward
 app.py | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 app.py
mc1862@cell11-cse:~/demo/demo$ ls
app.css  app.js  app.py  README.md
```
## 12. Understanding the Final State
```bash
mc1862@cell11-cse:~/demo/demo$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```
This means:
- You are on master
- Local and remote are synchronized
- No pending changes