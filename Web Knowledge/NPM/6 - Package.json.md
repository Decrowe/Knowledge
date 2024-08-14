# The File Itself
The package.json contains many important information about your NPM package, including:
- **Metadata** about your package
- The main **entry point** if your package
- **Scripts** that can be run by NPM 
- **Dependencies**
# Initialize
To create a new **package.json** inside your project you can call

``` shell
npm init
```

After following some prompts and entering values you will get a a package.json which looks similar to this:

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
  "license": "ISC"
}
```

## Adding Packages (Dependencies)
Adding new packages will cause NPM to add a new field: **dependencies**:

``` shell
# Install a new package
npm install "lodash"
```

Results in:

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

//Added a new field:
  "dependencies": {
    "lodash": "^4.17.21"
  }
}
```

