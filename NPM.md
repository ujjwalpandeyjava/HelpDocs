Version: ^1.6.2 (major.patch.minor)
Caret version range: The ^ symbol indicates that any version within the major version 1 (1.x.x) is acceptable
Allowed:
	1.6.2: the minimum specified version
	1.6.3, 1.6.4, 1.6.5, ... (any patch updates within 1.6.x)
	1.7.0, 1.8.0, 1.9.0, ... (any minor updates within 1.x.x)
Not allowed:
2.0.0 or higher (major version updates are excluded)


# Update dependencies used in projects

Using package [npm-check-updates](https://www.npmjs.com/package/npm-check-updates)

To update all dependencies in your React application to their latest versions, you can follow these steps:

0. Check list of outdated dependencies
	```
	npm outdated
	```

1. **Install `npm-check-updates` globally**:
	```bash
	npm install -g npm-check-updates
	
	```
	in case getting error of mkdir not allowed -13 use:
	```
	npm i npm-check-updates
	```

2. **Run `npm-check-updates` to update the `package.json` file**:
	```bash
	npx npm-check-updates -u
	```

3. **Install the updated dependencies**:
	```bash
	npm install
	```

These commands will update your `package.json` file with the latest versions of all dependencies and then install them

> npm outdated

Check list of outdated libraries used in project

> npm update
Updates all packages to their latest versions

> npm i <Library> [<Library2> ... ]
Install libraries

> npm unstall <Library> [<Library2> ... ]
Uninstall libraries








+++++++++++++ Update all libraries to latest (not-recommanded for big project)
Update to latest major versions (aggressive way):
 > npm install -g npm-check-updates
Install the npm-check-updates package globally.
 > ncu -u
Updates the version numbers in your package.json file to the latest major versions.
 > npm install
Installs the updated packages