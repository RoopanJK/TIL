# Remove Submodule From Repository

1. git submodule deinit -f `submodule-path`
2. rm -rf .git/modules/`path-to-submodule`
3. git rm -f `path-to-submodule`