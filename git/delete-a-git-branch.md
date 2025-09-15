# Delete a Git Branch

### Local Branch
- Branches that exist on just the local machine.
- In order to view the list of local branches use the following command.
```
	git branch -l
```
- In order to delete a local git branch.
```
	git branch -d `branch_name`
```

### Remote Branch
- Remote branches are `local` branches that exist in the remote repository. 
- In order to update the list of remote branches
```
	git fetch
```
- This will fetch any new branches from the remote and setup a remote branch in the local repository.
- In order to delete a remote branch
```
	git push origin --delete `branch_name`
```
-  By default, `git fetch` does not remove any branch that does no longer exist on the remote. In order to do that, we need to explicitly `prune` the list of remote branches.