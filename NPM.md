# Code

Type `document.body.contentEditable = true` in browser console to make the whole page editable and uses it then.

## Unable to install dependencies?

In case getting error of mkdir not allowed -13 use:

> `npm update --legacy-peer-deps` -- Bypass peer dependency check.

## Updated dependencies

Update minor version

> `npm outdated` -- Check outdated
> `npm update` -- Updates all to their latest minor versions
> `npm i lib1 lib2` -- update selected
> `npm uninstall lib1 lib2` -- uninstall

Update major version (not-recommended for big project)

> `npm install -g npm-check-updates` -- Install packeage globally
> `ncu` -- See all outdated
> `ncu -u` -- updated packages in package.json
> `npm install` -- install
> `npm outdated` or `ncu` -- Verify
