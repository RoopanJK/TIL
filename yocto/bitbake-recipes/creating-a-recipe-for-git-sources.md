1. Use the `devtool` to automatically create a new recipe.
```
devtool add *recipe-name* *source-link*
```
2. The source link can be a http / ftp / git source. This will determine which [[Fetcher]] bitbake will use.
3. If using a git source 
	1. Add a specific `SRCREV` using the -S switch . The SRCREV should be a complete commit id. (The complete commit id can be taken from the URL of the commit page)
	2. Add a specific version name which will be used in the recipe with the -V switch.
4. A recipe with the source, auto-generated recipe (.bb) and a bbappend file will be available in the workspace directory.
5. Use `devtool build *recipe-name*` command to test the recipe.
6. After achieving the required build, use `devtool finish *recipe-name* *dest-layer-dir` to store the recipe in the required layer.