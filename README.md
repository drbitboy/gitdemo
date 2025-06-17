## Initialize Git repository, CHDIR into its top-level directory
```
% git init branching
Initialized empty Git repository in /home/drbitboy/tmp/branching/.git/

% cd branching
```

## Create new python script that prints Greatest Generation members
```
% vi family_.py

% cat family_.py
"""
Frank Conley
Marilyn Bush
John Carcich
Catherine Rerecich
"""

if "__main__" == __name__:
  for fammember in __doc__.strip().split('\n'):
    print(fammember)
```

## Exercise that script
```
% python family_.py
Frank Conley
Marilyn Bush
John Carcich
Catherine Rerecich
```

## Add and commit that script to this *current* **master** branch as the initial commit
```
% git add family_.py

% git commit -m initial.commit
[master (root-commit) f27ab44] initial.commit
 1 file changed, 10 insertions(+)
 create mode 100644 family_.py

% git log
commit f27ab44dbcfd06a3f08a1f27611e08baf0e85a12 (HEAD -> master)
Author: Brian Carcich <briantcarcich@gmail.com>
Date:   Sun Jun 15 08:27:55 2025 -0400

    initial.commit
```


## Make, and checkout, a new branch that is a copy of that current **master** branch
### New branch name is **next_gen**
```
% git checkout -b next_gen
Switched to a new branch 'next_gen'
```

## Show branches and log
### Asterisk is next to HEAD (current checked-out branch, **next_gen**)
```
% git branch
  master
* next_gen

% git log
commit f27ab44dbcfd06a3f08a1f27611e08baf0e85a12 (HEAD -> next_gen, master)
Author: Brian Carcich <briantcarcich@gmail.com>
Date:   Sun Jun 15 08:27:55 2025 -0400

    initial.commit
```

## Edit script to add Boomers, show edited content, run script
```
% vi family_.py

% cat family_.py
"""
Frank Conley
Marilyn Bush
John Carcich
Catherine Rerecich
Jessica Conley
Brian Carcich
"""

if "__main__" == __name__:
  for fammember in __doc__.strip().split('\n'):
    print(fammember)

% python family_.py
Frank Conley
Marilyn Bush
John Carcich
Catherine Rerecich
Jessica Conley
Brian Carcich
```


## Add, and then commit, updated script to *current* **next_gen** branch, then show log
* Note that only the **next_gen** name is associated with the new commit hash 03c0622...
  * The **master** branch is unchanged
    * The branch name **master** is still associated with commit hash f27ab44...
```
% git add family_.py

% git commit -m "1956 additions"
[next_gen 03c0622] 1956 additions
 1 file changed, 2 insertions(+)

% git log
commit 03c06228c8cd280ebb94cc49df6e8de1faea1122 (HEAD -> next_gen)
Author: Brian Carcich <briantcarcich@gmail.com>
Date:   Sun Jun 15 08:29:06 2025 -0400

    1956 additions

commit f27ab44dbcfd06a3f08a1f27611e08baf0e85a12 (master)
Author: Brian Carcich <briantcarcich@gmail.com>
Date:   Sun Jun 15 08:27:55 2025 -0400

    initial.commit
```



## Edit script to add Millenials, run script
```
% vi family_.py

% python family_.py
Frank Conley
Marilyn Bush
John Carcich
Catherine Rerecich
Jessica Conley
Brian Carcich
Gemma Carcich
Benjamin Anible
Benjamin Carcich
Laura Lohberger
Daniel Carcich
Alexandra Carcich
```


## Add, and then commit, updated script to *current* **next_gen** branch, then show log
```
% git add family_.py

% git commit -m "1980s additions"
[next_gen cbfb227] 1980s additions
 1 file changed, 6 insertions(+)

% git log
commit cbfb227431a4523dc4d40447315241aec926329b (HEAD -> next_gen)
Author: Brian Carcich <briantcarcich@gmail.com>
Date:   Sun Jun 15 08:30:41 2025 -0400

    1980s additions

commit 03c06228c8cd280ebb94cc49df6e8de1faea1122
Author: Brian Carcich <briantcarcich@gmail.com>
Date:   Sun Jun 15 08:29:06 2025 -0400

    1956 additions

commit f27ab44dbcfd06a3f08a1f27611e08baf0e85a12 (master)
Author: Brian Carcich <briantcarcich@gmail.com>
Date:   Sun Jun 15 08:27:55 2025 -0400

    initial.commit
```



## Edit script to add Kids, run script
```
% vi family_.py

% python family_.py
Frank Conley
Marilyn Bush
John Carcich
Catherine Rerecich
Jessica Conley
Brian Carcich
Gemma Carcich
Benjamin Anible
Benjamin Carcich
Laura Lohberger
Daniel Carcich
Alexandra Carcich
Georgi Carcich
Violet Carcich
Naomi Carcich
```



## Add, and then commit, updated script to *current* **next_gen** branch, then show log
```
% git add family_.py

% git commit -m "great grandchildren"
[next_gen 73ebd47] great grandchildren
 1 file changed, 3 insertions(+)

% git log
commit 73ebd470a4108c0e0b37a2db3b65a4cf1cb5da95 (HEAD -> next_gen)
Author: Brian Carcich <briantcarcich@gmail.com>
Date:   Sun Jun 15 08:31:51 2025 -0400

    great grandchildren

commit cbfb227431a4523dc4d40447315241aec926329b
Author: Brian Carcich <briantcarcich@gmail.com>
Date:   Sun Jun 15 08:30:41 2025 -0400

    1980s additions

commit 03c06228c8cd280ebb94cc49df6e8de1faea1122
Author: Brian Carcich <briantcarcich@gmail.com>
Date:   Sun Jun 15 08:29:06 2025 -0400

    1956 additions

commit f27ab44dbcfd06a3f08a1f27611e08baf0e85a12 (master)
Author: Brian Carcich <briantcarcich@gmail.com>
Date:   Sun Jun 15 08:27:55 2025 -0400

    initial.commit
```


## Show **--oneline --graph** log
```
% git log --all --decorate --color --oneline --graph
* 73ebd47 (HEAD -> next_gen) great grandchildren
* cbfb227 1980s additions
* 03c0622 1956 additions
* f27ab44 (master) initial.commit
```


## Create, add, and commit readme to the **next_gen** branch
```
% vi README.md

% git add README.md

% git commit -m add.readme
```


## A different person makes a small edit to the **master** branch
* Note that the **master** branch initially is still the f27ab44 **initial.commit**
```
% git checkout master
% vi family_.py
$ git add family_.py
$ git commit -m rename.variable
```

## Here is the difference between that **f27ab44 initial.commit** and the current **master** branch
```
% git diff f27ab44 master
diff --git a/family_.py b/family_.py
index e8bce82..a98ea25 100644
--- a/family_.py
+++ b/family_.py
@@ -6,5 +6,5 @@ Catherine Rerecich
 """

 if "__main__" == __name__:
-  for fammember in __doc__.strip().split('\n'):
-    print(fammember)
+  for family_member in __doc__.strip().split('\n'):
+    print(family_member)
```

## Show **--oneline --graph** log of the current state
* Note that there are ***two*** commit sequences starting from **f27ab44 initial.commit**
  * The left (vertical) sequence leads to commit **24b6d15 branch next_gen**
  * The right sequence leads to commit **bf19ace branch master**
```
% git log --all --decorate --color --oneline --graph
* 24b6d15 (origin/next_gen, next_gen) add.readme
* 73ebd47 great grandchildren
* cbfb227 1980s additions
* 03c0622 1956 additions
| * bf19ace (HEAD -> master, origin/master) rename.variable
|/
* f27ab44 initial.commit
```


## Checkout master branch, then merge next_gen branch into it
```
% git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.


% git merge next_gen
Auto-merging family_.py
Merge made by the 'recursive' strategy.
 README.md  | 384 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 family_.py |  11 +++
 2 files changed, 395 insertions(+)
 create mode 100644 README.md
```

































## Show **--oneline --graph** log
* Graph display illustrates how branches have been merged
```
% git log --all --decorate --color --oneline --graph
*   96c62fb (HEAD -> master) Merge branch 'next_gen' into master
|\
| * a15b3d4 (origin/next_gen, next_gen) add.readme
| * 73ebd47 great grandchildren
| * cbfb227 1980s additions
| * 03c0622 1956 additions
* | bf19ace (origin/master) rename.variable
|/
* f27ab44 initial.commit
```
