
In the [[What is a branch in git?]]  section we saw what is a branch in git.
Here we learn how to merge branches ?

### How to merge branches ? 

Suppose  you have two branches : 
- master 
- authFeature

Now what you want is to merge these branches so that auth feature is added to your project well you can merge them .

simply write : 
```bash
git checkout master ##It's important to know which branch you are merging to 
git branch 
	*master
	authFeature
git merge authFeature
```

if there are no merge conflicts and the process executes smoothly then , 
after the executing above command your authFeature branch would be merge into master 

and now you can delete the old branch 
```bash
git branch -d authFeature
```

---

### Merge Conflicts 

When during merge if commits of the two branches changes the same part of the file or the line then a merge conflict is issued by git. 

During merge conflict git is unable to merge the branches , and has paused the merge process while you resolve the conflict , 

if you want to check which file are unmerged after a merge conflict you can run : 
```bash
$ git status 
On branch master
You have unmerged paths.
(fix conflicts and run "git commit") 
Unmerged paths:
	(use "git add ..." to mark resolution) 
	 both modified: index.html 
	 no changes added to commit (use "git add" and/or "git commit -a")
```

**Anything that has merge conflicts and isn't resolved is an  unmerged path** 

Git adds standard conflict-resolution markers to the files that have conflicts, so you can open them manually and resolve those conflicts. Your file contains a section that looks something like this:
```
<<<<<<< HEAD:index.html

contact : email.support@github.com

=======

 please contact us at support@github.com

>>>>>>> iss53:index.html
```

This means the version in HEAD (your master branch, because that was what you had checked out when you ran your merge command) is the top part of that block (everything above the   ===== ), while the version in your feature branch looks like everything in the bottom part. In order to resolve the conflict, you have to either choose one side or the other or merge the contents yourself. For instance, you might resolve this conflict by replacing the entire block with this:

Either remove the part above === to area below one and <<< >>> symbols and run 
``git add`` to mark each file as resolved.

Staging the file mark it as resolved in git.

---

### Fast Forward Merge 

If during merge process there is no additional commit after the ``HEAD`` then git performs the fast forward merge in which it sets the pointer of the merged branch to the pointer of the branch being merged. 

