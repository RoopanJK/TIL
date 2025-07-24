# Patching Source of a Recipe using Devtool

devRef: https://wiki.yoctoproject.org/wiki/TipsAndTricks/Patching_the_source_for_a_recipe

1. Use devtool to modify the required recipe.
	```
	devtool modify <recipe-name>
	```
	- This fetches the sources and places it into `workspace/sources/recipe-name` for modification.
	- This also initialises it as a git repository if it isn't already one.
2. Make required changes to the source and test it using
	```
	devtool build <recipe-name>
	```
	- Changes in recipe of the source will affect this build, so make necessary changes on both source and recipe to result in a successful build.
3. Once you have reached you required result. Do necessary git commit to the repository.
4. After you've commited. Create a patch file which will be used by the .bbappend of the recipe.
```
	git format-patch HEAD~1
```
5. Use the devtool to automatically generate `.bbappend` and patch files.
	```
	devtool update-recipe -a <layer-path> <recipe-name>
	```
	- The above command will generate the required recipe and place it in your meta-layer.
6. Once completed the above steps, this temp source folder can be deleted using 
	```
	devtool reset <recipe-name>
	```
7. Delete the preserved source if required.