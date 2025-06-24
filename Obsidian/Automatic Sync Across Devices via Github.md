##### 1. Setup auto commit and sync in the [`obsidian-git`](https://github.com/Vinzent03/obsidian-git) community plugin:
- Install the obsidian git plugin in the community plugins window of obsidian. (The plugin is named as just **git** in it. So verify the author of the plugin w.r.t the above linked repository)
- The plugin should automatically detect a git repository and start parsing the source tree for changes. 
- If a git repository is not initialised already. Initialise a new repository.
- We are going to rely on the commit and sync feature of this plugin which does three things
	- `Commit the changes -> Pull latest changes -> Push commited changes`
- In order for the commit and sync to act automatically, we need to [[Setup Git Credential Helper]] to avoid inputting our git credentials each time commit and sync takes place.
