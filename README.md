
# Git challenges
## Part1: Refining Git History
### Missing File Fix
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/Git lea      
$ git status && git log
On branch main
Untracked files:
  (use "git add <file>..." to include in what       
        test4.md

nothing added to commit but untracked files prrack) 
commit ba3206645881044faa8cf9bec478b73ae6db3ba      
commit ba3206645881044faa8cf9bec478b73ae6db3ba      
Author: prisca <priscamasereli@gmail.com>
Date:   Fri Feb 28 11:07:42 2025 +0200

    chore: Create third and fourth files


user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)                                 s   
$ git add test4.md


user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ git commit --amend -m "chore: Create third and fourth files"
[main 534fc44] chore: Create third and fourth files 
 Date: Fri Feb 28 12:24:04 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)   
 create mode 100644 README.md
 create mode 100644 test4.md
```

### Editing Commit History
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git rebase -i HEAD~6
[detached HEAD 86ef08b] chore: Create second file
 Date: Fri Feb 28 12:19:34 2025 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git push origin main --force-with-lease
Enumerating objects: 14, done.
Counting objects: 100% (14/14), done.
Delta compression using up to 4 threads
Compressing objects: 100% (13/13), done.
Writing objects: 100% (13/13), 1.74 KiB | 444.00 KiB/s, done.
Total 13 (delta 6), reused 0 (delta 0), pack-reused 0 (from 0)
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.
```

### Keeping History Tidy - Squashing Commits
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)$ git rebase -i --root
[detached HEAD 4528dfb] chore: Combine initial and second files
 Date: Fri Feb 28 12:19:34 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)$ git push --force     
Enumerating objects: 14, done.
Counting objects: 100% (14/14), done.
Delta compression using up to 4 threads
Compressing objects: 100% (13/13), done.
Writing objects: 100% (14/14), 1.98 KiB | 203.00 KiB/s, done.
Total 14 (delta 5), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (5/5), done.
To https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-.git
 + 5be5bd9...b58b1b3 main -> main (forced update)

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
```

### Splitting a commit
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)        
$ git rebase -i HEAD~5
Stopped at 6bc01f8...  chore: Create third and fourth files
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue

  user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main|REBASE 1/5)
$ git reset HEAD~

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main|REBASE 1
learning (main|REBASE 1/5)
$ git add test3.md

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main|REBASE 1
learning (main|REBASE 1/5)
$ git commit -m "Create Third File"
[detached HEAD 574cc37] Create Third File
 1 file changed, 0 insertions(+), 0 deletions(-)    
 create mode 100644 test3.md

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main|REBASE 1
learning (main|REBASE 1/5)
$ git add test4.md

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main|REBASE 1
learning (main|REBASE 1/5)
$ git commit -m "Create Fourth File"
[detached HEAD 3648f25] Create Fourth File
 1 file changed, 0 insertions(+), 0 deletions(-)    
 create mode 100644 test4.md

 user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main|REBASE 6/6)
$ git rebase --continue
[detached HEAD f032faa] chore: split the commit message
 1 file changed, 2 insertions(+), 6 deletions(-)
Successfully rebased and updated refs/heads/main.
```

### Advanced Squashing
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)        
$ git rebase -i HEAD~7
[detached HEAD 1d6cf13] Create third and fourth files
 Date: Tue Mar 4 16:39:25 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)        
$ git log --oneline
1eb24ad (HEAD -> main) feat:Splitting a Commit
8c4ce62 chore: split the commit message
7622a76 Restore README.md content
f385a98 Restored README.md from previous commit
726471c feat: 1.missing file fix
1d6cf13 Create third and fourth files
4528dfb chore: Combine initial and second files
```
### Dropping a commit
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)                                     learning (main)        
$ git add unwanted.txt

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ git commit -m "Unwanted commit"
[main 5c45fc0] Unwanted commit
 1 file changed, 1 insertion(+)
 create mode 100644 unwanted.txt

 user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 294 bytes | 294.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-.git
   248ba26..5c45fc0  main -> main

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ git log --oneline
5c45fc0 (HEAD -> main, origin/main) Unwanted commit 
248ba26 feat: Advanced Squashing
1eb24ad feat:Splitting a Commit
8c4ce62 chore: split the commit message
7622a76 Restore README.md content
f385a98 Restored README.md from previous commit     
726471c feat: 1.missing file fix
1d6cf13 Create third and fourth files
4528dfb chore: Combine initial and second files     

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ git rebase -i HEAD~3
Successfully rebased and updated refs/heads/main.   

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ git log --oneline
248ba26 (HEAD -> main) feat: Advanced Squashing
1eb24ad feat:Splitting a Commit
8c4ce62 chore: split the commit message
7622a76 Restore README.md content
f385a98 Restored README.md from previous commit     
726471c feat: 1.missing file fix
1d6cf13 Create third and fourth files
4528dfb chore: Combine initial and second files     

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ ls
README.md  test1.md  test2.md  test3.md  test4.md
```
### Cherry-picking Commits
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/branch)   
$ touch test5.md

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/branch)   
$ echo "This is test 5" > test5.md
warning: in the working copy of 'test5.md', LF will 
be replaced by CRLF the next time Git touches it    learning (ft/branch)
<<<<<<< HEAD

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands be replaced by CRLF the
learning (ft/branch)
$ git commit -m "Implemented test 5"
[ft/branch e957c98] Implemented test 5              learning (ft/branch)   
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (ft/branch)
$ git checkout main                                 learning (ft/branch)   
Switched to branch 'main'
Your branch is up to date with 'origin/main'.       

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ git log --oneline
a76c677 (HEAD -> main, origin/main) Dropping a Commit
248ba26 feat: Advanced Squashing
1eb24ad feat:Splitting a Commit
8c4ce62 chore: split the commit message
7622a76 Restore README.md content
f385a98 Restored README.md from previous commit     
726471c feat: 1.missing file fix
1d6cf13 Create third and fourth files
4528dfb chore: Combine initial and second files     

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ ls
README.md  test1.md  test2.md  test3.md  test4.md

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ git checkout ft/branch
Switched to branch 'ft/branch'

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (ft/branch)
$ ls
README.md  test2.md  test4.md
test1.md   test3.md  test5.md

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (ft/branch)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.       

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ git checkout ft/branch
Switched to branch 'ft/branch'

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (ft/branch)
$ git log --oneline
e957c98 (HEAD -> ft/branch) Implemented test 5
a76c677 (origin/main, main) Dropping a Commit       
248ba26 feat: Advanced Squashing
1eb24ad feat:Splitting a Commit
8c4ce62 chore: split the commit message
7622a76 Restore README.md content
f385a98 Restored README.md from previous commit     
726471c feat: 1.missing file fix
1d6cf13 Create third and fourth files
4528dfb chore: Combine initial and second files     

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (ft/branch)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.       

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ git cherry-pick e957c98
[main ef1f445] Implemented test 5
 Date: Tue Mar 4 18:39:53 2025 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ git log --oneline
ef1f445 (HEAD -> main) Implemented test 5
a76c677 (origin/main) Dropping a Commit
248ba26 feat: Advanced Squashing
1eb24ad feat:Splitting a Commit
8c4ce62 chore: split the commit message
7622a76 Restore README.md content
f385a98 Restored README.md from previous commit     
726471c feat: 1.missing file fix
1d6cf13 Create third and fourth files
4528dfb chore: Combine initial and second files     

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ ls
README.md  test2.md  test4.md
test1.md   test3.md  test5.md

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ cat test5.md
This is test 5

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands 
learning (main)
$ git checkout ft/branch
Switched to branch 'ft/branch'

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/branch)   
$ git log --oneline
e957c98 (HEAD -> ft/branch) Implemented test 5
a76c677 (origin/main) Dropping a Commit
248ba26 feat: Advanced Squashing
1eb24ad feat:Splitting a Commit
8c4ce62 chore: split the commit message
7622a76 Restore README.md content
f385a98 Restored README.md from previous commit
726471c feat: 1.missing file fix
1d6cf13 Create third and fourth files
4528dfb chore: Combine initial and second files

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/branch)   
$
```
### Visualizing Commit History (Bonus)
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/branch)   
$ git log --graph
|
* commit e957c989eb1d3a026051ca786b0f5187fe3ab630
| Author: prisca <priscamasereli@gmail.com>
|     Dropping a Commit
:...skipping...
* commit e7cbfba202e1c38a7238a0855b1aa5e505228210 (HEAD -> ft/branch, origin/ft/branch)
* commit e957c989eb1d3a026051ca786b0f5187fe3ab630
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 18:39:53 2025 +0200
|
|     Implemented test 5
|
* commit a76c6778e56443b3d3dbb998f21bd66e133300c6
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 18:01:39 2025 +0200
|
|     Dropping a Commit
|
:...skipping...
* commit e7cbfba202e1c38a7238a0855b1aa5e505228210 (HEAD -> ft/branch, origin/ft/branch)
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 18:56:24 2025 +0200
|
|     feat: Cherry-Picking Commits
|
* commit e957c989eb1d3a026051ca786b0f5187fe3ab630
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 18:39:53 2025 +0200
|
|     Implemented test 5
|
* commit a76c6778e56443b3d3dbb998f21bd66e133300c6
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 18:01:39 2025 +0200
|
|     Dropping a Commit
|
* commit 248ba26839c8615838ba71d95907fdb8af9422a5
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 17:45:00 2025 +0200
|
|     feat: Advanced Squashing
:...skipping...
* commit e7cbfba202e1c38a7238a0855b1aa5e505228210 (HEAD -> ft/branch, origin/ft/branch)
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 18:56:24 2025 +0200
|
|     feat: Cherry-Picking Commits
|
* commit e957c989eb1d3a026051ca786b0f5187fe3ab630
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 18:39:53 2025 +0200
|
|     Implemented test 5
|
* commit a76c6778e56443b3d3dbb998f21bd66e133300c6
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 18:01:39 2025 +0200
|
|     Dropping a Commit
|
* commit 248ba26839c8615838ba71d95907fdb8af9422a5
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 17:45:00 2025 +0200
|
|     feat: Advanced Squashing
|
* commit 1eb24ad5a6882df3b13ab69bb265e250a2e79208
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 17:31:05 2025 +0200
:...skipping...
* commit e7cbfba202e1c38a7238a0855b1aa5e505228210 (HEAD -> ft/branch, origi
n/ft/branch)
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 18:56:24 2025 +0200    
|
|     feat: Cherry-Picking Commits
|
* commit e957c989eb1d3a026051ca786b0f5187fe3ab630
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 18:39:53 2025 +0200
|
|     Implemented test 5
| 
* commit a76c6778e56443b3d3dbb998f21bd66e133300c6
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 18:01:39 2025 +0200
|
|     Dropping a Commit
|
* commit 248ba26839c8615838ba71d95907fdb8af9422a5
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 17:45:00 2025 +0200
|
|     feat: Advanced Squashing
|
* commit 1eb24ad5a6882df3b13ab69bb265e250a2e79208
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 17:31:05 2025 +0200
|
|     feat:Splitting a Commit
|
* commit 8c4ce62988424f1d1c0a79fc9652c0fe57649459
| Author: prisca <priscamasereli@gmail.com>
| Date:   Mon Mar 3 11:56:52 2025 +0200
|
|     chore: split the commit message
|
* commit 7622a76a8eda8ba0f3bdf9ae1049f7315053547a
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 17:08:23 2025 +0200
|
|     Restore README.md content
|
* commit f385a98fa0ae6598238013acea105899230c801f
| Author: prisca <priscamasereli@gmail.com>
| Date:   Fri Feb 28 14:39:18 2025 +0200
|
|     Restored README.md from previous commit
|
* commit 726471c5a773239d03050fcab1aae898dc38907d
| Author: prisca <priscamasereli@gmail.com>
| Date:   Fri Feb 28 12:34:59 2025 +0200
|
|     feat: 1.missing file fix
|
* commit 1d6cf135bda7fae60edb7dc2c814d441ee0a8b20
| Author: prisca <priscamasereli@gmail.com>
| Date:   Tue Mar 4 16:39:25 2025 +0200
|
|     Create third and fourth files
|
* commit 4528dfba1c85f628d8b5b421895a2ae8a9cf59e7
  Author: prisca <priscamasereli@gmail.com>
  Date:   Fri Feb 28 12:19:34 2025 +0200

      chore: Combine initial and second files

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/branch)   
$ git log --graph --oneline --all
* e7cbfba (HEAD -> ft/branch, origin/ft/branch) feat: Cherry-Picking Commits
* e957c98 Implemented test 5
| * ef1f445 (origin/main, main) Implemented test 5
|/
* a76c677 Dropping a Commit
* 248ba26 feat: Advanced Squashing
* 1eb24ad feat:Splitting a Commit
* 8c4ce62 chore: split the commit message
* 7622a76 Restore README.md content
* f385a98 Restored README.md from previous commit
* 726471c feat: 1.missing file fix
* 1d6cf13 Create third and fourth files
* 4528dfb chore: Combine initial and second files

user@PRISCA-DESKTOP MINGW64 /f/TH
E GYM/git commands learning (ft/branch)   
$
```
### Understanding Reflogs
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/branch)
$ git reflog
Commits
e957c98 HEAD@{4}: checkout: moving from main to ft/branch
ef1f445 (origin/main, main) HEAD@{5}: cherry-pick: Implemented test 5      
a76c677 HEAD@{6}: checkout: moving from ft/branch to main
e957c98 HEAD@{7}: checkout: moving from main to ft/branch
a76c677 HEAD@{8}: checkout: moving from ft/branch to main
e957c98 HEAD@{9}: checkout: moving from main to ft/branch
a76c677 HEAD@{10}: checkout: moving from ft/branch to main
e957c98 HEAD@{11}: commit: Implemented test 5
a76c677 HEAD@{12}: checkout: moving from main to ft/branch
a76c677 HEAD@{13}: rebase (abort): returning to refs/heads/main
1d6cf13 HEAD@{14}: rebase (start): checkout HEAD~7
a76c677 HEAD@{15}: rebase (abort): returning to refs/heads/main
726471c HEAD@{16}: rebase (start): checkout HEAD~6
a76c677 HEAD@{17}: commit: Dropping a Commit
248ba26 HEAD@{18}: rebase (finish): returning to refs/heads/main
248ba26 HEAD@{19}: rebase (start): checkout HEAD~3
5c45fc0 HEAD@{20}: commit: Unwanted commit
248ba26 HEAD@{21}: commit: feat: Advanced Squashing
1eb24ad HEAD@{22}: rebase (finish): returning to refs/heads/main
1eb24ad HEAD@{23}: rebase (pick): feat:Splitting a Commit
8c4ce62 HEAD@{24}: rebase (pick): chore: split the commit message
7622a76 HEAD@{25}: rebase (pick): Restore README.md content
f385a98 HEAD@{26}: rebase (pick): Restored README.md from previous commit  
726471c HEAD@{27}: rebase (pick): feat: 1.missing file fix
1d6cf13 HEAD@{28}: rebase (squash): Create third and fourth files

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/branch)
```
## Part 2: Branching Basics
### Feature Branching creation
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/branch)   
$ git checkout -b ft/new-feature
Switched to a new branch 'ft/new-feature'

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-feature)
$ git branch
  ft/branch
* ft/new-feature
  main

```
### Working on the Feature Branch
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-feature)
$ touch feature.txt

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-feature)
$ echo "This is the core functionality for the new feature" > feature.txt

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-feature)
$ git add feature.txt
warning: in the working copy of 'feature.txt', LF will be replaced by CRLF 
the next time Git touches it

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-feature)
$ git commit -m "Implemented core functionality for new feature"
[ft/new-feature 75eef11] Implemented core functionality for new feature
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-feature)
```

### Switching Back and Making More Changes
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-featurSwitched to branch 'main'
Your branch is up to date with 'origin/main'.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)        
$ touch readme.txt
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)        
$ echo "Welcome to the project! This is the readme file." > readme.txt     

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)        
$ git add readme.txt
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)        
$ git commit -m "Updated project readme"
[main ed98f03] Updated project readme
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)        
$ git log --oneline
ed98f03 (HEAD -> main) Updated project readme
ef1f445 (origin/main) Implemented test 5
a76c677 Dropping a Commit
248ba26 feat: Advanced Squashing
1eb24ad feat:Splitting a Commit
8c4ce62 chore: split the commit message
7622a76 Restore README.md content
f385a98 Restored README.md from previous commit
726471c feat: 1.missing file fix
1d6cf13 Create third and fourth files
4528dfb chore: Combine initial and second files

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
```

### Local vs. Remote Branches:
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git push origin main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 3.47 KiB | 1.16 MiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-.git
   ed98f03..c288a80  main -> main

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git pull origin main
From https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-
 * branch            main       -> FETCH_HEAD
Already up to date.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
```

### Branch Deletion

```bash

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git merge ft/new-feature
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main|MERGING)    
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
        new file:   feature.txt

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   README.md


user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main|MERGING)    
$ git add README.md
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main|MERGING)    
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
        modified:   README.md
        new file:   feature.txt


user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main|MERGING)    
$ git add .

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main|MERGING)    
$ git commit -m "chore: merge ft/new-feature into main"
[main 716ff1c] chore: merge ft/new-feature into main

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git merge ft/new-feature
Already up to date.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git branch -d ft/new-feature
Deleted branch ft/new-feature (was a5a4f7b).

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git push
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 4 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 1.13 KiB | 290.00 KiB/s, done.
Total 6 (delta 4), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (4/4), completed with 2 local objects.
To https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-.git
   c288a80..716ff1c  main -> main

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git push origin --delete ft/new-feature
To https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-.git
 - [deleted]         ft/new-feature

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git branch -a
  ft/branch
* main
  remotes/origin/ft/branch
  remotes/origin/main

```

### Creating a Branch from a Commit
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git log --oneline
716ff1c (HEAD -> main, origin/main) chore: merge ft/new-feature into main
c2af31d feat:Local vs. Remote Branches


user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git checkout -b ft/new-branch-from-commit c2af31d
Switched to a new branch 'ft/new-branch-from-commit'

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-branch-from-commit)
$ git log --oneline
c2af31d (HEAD -> ft/new-branch-from-commit) feat:Local vs. Remote Branches
c288a80 feat:Switching Back and Making More Changes

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-branch-from-commit)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git push 
Everything up-to-date

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'


user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-branch-from-commit)
$ git push origin ft/new-branch-from-commit
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
remote:
remote: Create a pull request for 'ft/new-branch-from-commit' on GitHub by visiting:
remote:      https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-/pull/new/ft/new-branch-from-commit
remote:
To https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-.git
 * [new branch]      ft/new-branch-from-commit -> ft/new-branch-from-commit
```
### Branch Merging
```bash 
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-branch-fro
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git merge ft/new-branch-from-commit
Auto-merging README.md
ning (main|MERGING)
$ git merge ft/new-branch-from-commit                   e result.
Already up to date.
$ git merge ft/new-branch-from-commit                   ning (main|MERGING)
Already up to date.
Already up to date.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)ning (main)
$ git add README.md

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git commit -m "feat: Creating a Branch from a Commit"
[main bc8f757] feat: Creating a Branch from a Commit
 1 file changed, 42 insertions(+)

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$
```
### Branch Renamin
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-branch-from-commit)
$ git branch -m ft/improved-branch-name

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/improved-branch-name)
$ git branch
  ft/branch
* ft/improved-branch-name
  main

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/improved-branch-name)
$ git push origin --delete ft/new-branch-from-commit
To https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-.git
 - [deleted]         ft/new-branch-from-commit

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/improved-branch-name)
$ git push origin ft/improved-branch-name
Enumerating objects: 19, done.
Counting objects: 100% (19/19), done.
Delta compression using up to 4 threads
Compressing objects: 100% (15/15), done.
Writing objects: 100% (15/15), 2.47 KiB | 505.00 KiB/s, done.
Total 15 (delta 10), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (10/10), completed with 2 local objects.        
remote:
remote: Create a pull request for 'ft/improved-branch-name' on GitHub by visiting:
remote:      https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-/pull/new/ft/improved-branch-name
remote:
To https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-.git
 * [new branch]      ft/improved-branch-name -> ft/improved-branch-name        

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/improved-branch-name)
$
```

### Checking Out Detached HEAD
```Bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning ((6d3e630...))
$ touch experimental-file.txt

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning ((6d3e630...))
$ echo "This is an experimental change" > experimental-file.txt

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning ((6d3e630...))
$ git add experimental-file.txt
warning: in the working copy of 'experimental-file.txt', LF will be replaced by CRLF the next time Git touches it

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning ((6d3e630...))
$ git commit -m "Experimental change in detached HEAD"  
HEAD detached from aa354a3
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning ((6d3e630...))    
$ git checkout -b new-branch
Switched to a new branch 'new-branch'

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (new-branch)      
$

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (new-branch)      
$ git checkout main
error: Your local changes to the following files would be overwritten by checkout:
        README.md
Please commit your changes or stash them before you switch branches.
Aborting

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (new-branch)      
$ git add README.md

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (new-branch)
$ git commit -m "feat: Renaming Branches"
[new-branch 283f4a0] feat: Renaming Branches
 1 file changed, 1 insertion(+)

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (new-branch)      
$
```



### Branch Rebasing
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-branch-from-commit)
$ git rebase main
Successfully rebased and updated refs/heads/ft/new-branch-from-commit.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/new-branch-from-commit)
$ git log --oneline
2ec0217 (HEAD -> ft/new-branch-from-commit, main) feat: Branch merging
bc8f757 feat: Creating a Branch from a Commit
239e621 Merge branch 'ft/new-branch-from-commit'
d99c0e7 feat: Branch Deletion
e4af6a7 feat: Branch Deletion
716ff1c (origin/main) chore: merge ft/new-feature into main
c2af31d (origin/ft/new-branch-from-commit) feat:Local vs. Remote Branches      
c288a80 feat:Switching Back and Making More Changes
ed98f03 Updated project readme
a5a4f7b feat: Working on the Feature branch
75eef11 Implemented core functionality for new feature
b2d6831 feat: Feature Branch Creation
759fdf2 (origin/ft/branch, ft/branch) feat: Understanding Reflogs
bbc4d33 feat: Visualizing Commit History
e7cbfba feat: Cherry-Picking Commits
ef1f445 Implemented test 5
e957c98 Implemented test 5
a76c677 Dropping a Commit
248ba26 feat: Advanced Squashing
1eb24ad feat:Splitting a Commit
8c4ce62 chore: split the commit message
7622a76 Restore README.md content
f385a98 Restored README.md from previous commit
726471c feat: 1.missing file fix
1d6cf13 Create third and fourth files
4528dfb chore: Combine initial and second files

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$
```

## Part3: Advanced Workflows

### Stashing Changes
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)      
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")        

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)      
$ git stash
Saved working directory and index state WIP on main: c79ca3d chore: resolve merge conflicts

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)      
$ git stash list
stash@{0}: WIP on main: c79ca3d chore: resolve merge conflicts

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)      
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```
### Retrieving Stashed Changes

```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)      
$ git stash pop
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)  
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")        
Dropped refs/stash@{0} (77bba6396e8e5b09bd3870f93b5c67c0c4127768)        

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)      
$
```
### Branch Merging Conflicts (Continued)
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)      
$ git checkout -b ft/conflict-branch
Switched to a new branch 'ft/conflict-branch'

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/conflict-branch)
$ echo "This is the feature branch change" > conflict.txt

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/conflict-branch)
$ git add conflict.txt
warning: in the working copy of 'conflict.txt', LF will be replaced by CRLF the next time Git touches it

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/conflict-branch)
$ git commit -m "Add feature branch changes to conflict.txt"
[ft/conflict-branch cf67c45] Add feature branch changes to conflict.txt
 1 file changed, 1 insertion(+)
 create mode 100644 conflict.txt

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (ft/conflict-branch)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$ echo "This is the main branch change" > conflict.txt

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$ git add conflict.txt
warning: in the working copy of 'conflict.txt', LF will be replaced by CRLF the next time Git touches it

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$ git commit -m "Add main branch changes to conflict.txt"
[main f882212] Add main branch changes to conflict.txt
 1 file changed, 1 insertion(+)
 create mode 100644 conflict.txt

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$ git merge ft/conflict-branch
Auto-merging conflict.txt
CONFLICT (add/add): Merge conflict in conflict.txt
Automatic merge failed; fix conflicts and then commit the result.    

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main|MERGING)
$ git status

You have unmerged paths.                      mit.
  (fix conflicts and run "git commit")        s)
  (use "git merge --abort" to abort the merge)


Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both added:      conflict.txt

no changes added to commit (use "git add" and/or "git commit -a")                           or "git commit -a")

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git add conflict.txt

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git commit -m "feat: resolving merge conflicts"
[main 0b92bd8] feat: resolving merge conflicts 1 file changed, 3 insertions(+), 3 deletions(-)

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git log --oneline
0b92bd8 (HEAD -> main) feat: resolving merge conflicts
ea66364 Merge branch 'ft/conflict-branch'     
f882212 Add main branch changes to conflict.txt
cf67c45 (ft/conflict-branch) Add feature branch changes to conflict.txt
9bdf4d7 (origin/main) feat: Retrieving Stashed Changes
98e1e3a feat: Stashing Changes
c79ca3d chore: resolve merge conflicts
ef04258 Merge new-branch with main
0827fbd Merge ft/improved-branch-name into main
09f5229 (origin/new-branch, new-branch) feat: 
Checking Out Detached HEAD

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git push origin main
Enumerating objects: 13, done.
Counting objects: 100% (13/13), done.
Delta compression using up to 4 threads       
Compressing objects: 100% (10/10), done.
Writing objects: 100% (12/12), 1.12 KiB | 229.00 KiB/s, done.
Total 12 (delta 5), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (5/5), completed with 1 local object.
To https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-.git
   9bdf4d7..0b92bd8  main -> main

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$
```
### Understanding Detached HEAD state
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$ git checkout 6d3e630
Note: switching to '6d3e630'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in 
this
state without impacting any branches by switching back to a branch.  

If you want to create a new branch to retain commits you create, you 
may
do so (now or later) by using -c with the switch command. Example:   

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 6d3e630 Experimental change in detached HEAD

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning ((6d3e630...))
$ git checkout main
Previous HEAD position was 6d3e630 Experimental change in detached HEAD
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$
```
### Ignoring Files/Directories
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git add .gitignore

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git commit -m "Added .gitignore to exclude temp files"
[main 99d1583] Added .gitignore to exclude tem$ git add .gitignore

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git commit -m "Added .gitignore to exclude temp files"
[main 99d1583] Added .gitignore to exclude temmands learning (main)
$ git commit -m "Added .gitignore to exclude temp files"
[main 99d1583] Added .gitignore to exclude tem$ git commit -m "Added .gitignore to exclude temp files"
[main 99d1583] Added .gitignore to exclude tem[main 99d1583] Added .gitignore to exclude temp files
 1 file changed, 2 insertions(+)
 create mode 100644 .gitignore

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$
```
### Working with tags
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$ git tag v1.0

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$ git tag
v1.0

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git show v1.0
commit 2d0f3704680877f6021ac2ac9a12167331f99aa3 (HEAD -> main, tag: v1.0)
Author: prisca <priscamasereli>
Date:   Tue Mar 11 23:12:48 2025 +0200

Author: prisca <priscamasereli>
Date:   Tue Mar 11 23:12:48 2025 +0200

    feat: Ignoring Files/Directories

diff --git a/README.md b/README.md
index 604d304..c8ca019 100644
--- a/README.md
+++ b/README.md
@@ -1099,6 +1099,27 @@ Switched to branch 'main'
 Your branch is ahead of 'origin/main' by 2 commits.
   (use "git push" to publish your local commits)

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$
```
### Listing and Deleting Tags
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)
$ git tag
v1.0

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$ git tag -n
v1.0            feat: Ignoring Files/Directories

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$ git tag -d v1.0
Deleted tag 'v1.0' (was 2d0f370)

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$ git tag

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$
```
### Pushing Local Work to Remote Repositories

```bash 
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$ git push origin main
Enumerating objects: 24, done.
Counting objects: 100% (24/24), done.
Delta compression using up to 4 threads
Compressing objects: 100% (18/18), done.
Writing objects: 100% (21/21), 2.69 KiB | 183.00 KiB/s, done.
Total 21 (delta 11), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (11/11), completed with 2 local objects.
To https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-.git 
   9c15737..77aca2e  main -> main

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$
```
### Pulling Changes from Remote Repositories
```bash
user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$ git pull origin main
From https://github.com/Prisca2005/The-Gym-Git-Exercise-Solutions-
 * branch            main       -> FETCH_HEAD
Already up to date.

user@PRISCA-DESKTOP MINGW64 /f/THE GYM/git commands learning (main)  
$
```