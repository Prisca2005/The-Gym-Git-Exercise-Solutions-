
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
