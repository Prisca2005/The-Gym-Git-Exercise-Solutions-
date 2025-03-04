
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


