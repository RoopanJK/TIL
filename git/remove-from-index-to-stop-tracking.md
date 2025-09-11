# Remove from index to stop tracking

- Even though files are added to `.gitignore`. Git will still track the file if it's been already tracked.
- In order to stop Git from tracking the file, the file has to removed from its index.
```
	git rm --cached <file>
```

- In order to stop Git from tacking a folder
```
	git rm -r --cached <folder>
```
