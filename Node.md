# NodeJs

Run app:

1. Simple: `npm run start` or `npm start`
2. with devtool - hot reload: `npx nodemon ./mainFile.js`

## Not able to run

Issue on: `npm install`

    npm  : File C:\Program Files\nodejs\npm.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at https:/go.microsoft.com/fwlink/?LinkID=135170.

    At line:1 char:1
    + npm install
    + ~~~
        + CategoryInfo          : SecurityError: (:) [], PSSecurityException
        + FullyQualifiedErrorId : UnauthorizedAccess

Steps to Fix the Issue

    1. Run PowerShell or Windows Terminal as Administrator
    2. Check Current Execution Policy:
        Run: `Get-ExecutionPolicy`
        If it returns Restricted, that means script execution is disabled.
    3. Set Execution Policy:
        To allow script execution, you can change the execution policy.
        Recommended: RemoteSigned
        Run: `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`
    4. Verify with step 2

## save dependencies

You should use `--save-dev` when installing packages like sass because these are development dependencies-they are only needed while you are developing your application, not when it is running in production.

**Cleaner production builds**: Packages in devDependencies are not installed when you deploy your app with npm install --production or when the environment variable NODE_ENV is set to production. This keeps your production environment smaller and more secure

### Updated dependencies

Update minor version

> `npm outdated` -- Check outdated
> `npm update` -- Updates all to their latest minor versions
> `npm i lib1 lib2` -- update selected
> `npm uninstall lib1 lib2` -- uninstall

Update major version (not-recommended for big project)

> `npm install -g npm-check-updates` -- Install package globally
> `ncu` -- See all outdated
> `ncu -u` -- update packages in package.json
> `npm install` -- install
> `npm outdated` or `ncu` -- Verify

## Code

Type `document.body.contentEditable = true` in browser console to make the whole page editable and uses it then.

### Unable to install dependencies?

In case getting error of mkdir not allowed -13 use:

> `npm update --legacy-peer-deps` -- Bypass peer dependency check.


