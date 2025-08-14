# Undo Commits - Git Reset

```
git reset HEAD~<N>
```
- N is number of commits to move back.

```
git reset --soft <commit>
```
- `--soft` switch can be used to keep the files staed and move the HEAD to previous commit.

```
git reset --mixed <commit>
```
- `--mixed` (default) switch can be used to unstage all files and move the HEAD to commit.

```
git reset --hard <commit>
```
- `--hard` switch can be used to discard all changes to files and move the HEAD to the commit.

```
git reset <file>
```
- Unstage a file.