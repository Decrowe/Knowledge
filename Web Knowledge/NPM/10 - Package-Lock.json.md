# What does the Package-Lock.json contain?
The **Package-Lock.json** contains information about the version needed for you project.

# What is it for?
You may wonder: "Why do I need a package-lock.json since i have specified the versions in my package.json already?"

You may did. But when using:

``` shell
npm install
```

npm scans your **package.json** and installs the highest possible version of the packages you listed there.

Imagen this is your package.json:

``` json
{
  "name": "npm_learning",
  "version": "1.0.0",
  "description": "This package is only for learning purpose.",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "learning"
  ],
  "author": "Lukas Walter",
  "license": "ISC",
  "dependencies": {
    "lodash": "^4.0.0"
  }
}
```
We specified **lodash** version to be: **4.0.0**. When executing **npm install** now npm scans the package.json file, finds the lodash entry, checks the highest possible version which will not break any code and install it.

Doing this may ends up in installing **lodash**: 4.17.21 - since this should be the latest version which wont break our code.

However: Since **NPM** can not guarantee that there are no breaking changes it still can happen that developers updated the minor version incorrectly íncluding breaking changes.

And because of this we have the **Package-Lock.json** file. in this file the versions of our packages are locked and each time we execute **npm install** **NPM** scans the **Package-lock.json** file and takes the versions locked in there because doing this it can ensure that this versions wont have any unexpected impacts.