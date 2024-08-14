# Versions
Each package has a version. 
All versions (should) follow the [semantic versioning specs](https://semver.org/lang/de/) rules.

___
*Since SemVer is used mostly in Context of NPM many developers do not follow the rules strctly it is gut möglich quite possible that there are breaking changes even if just the patch version increased.*
___

## In Short:
A version consists of 3 numbers:
1) Major
2) Minor
3) Patch

Example: **2.4.3** 
**2**: Major
**4**: Minor
**3**: Patch

## Installing Dependencies according to SemVer
### Caret 
Imagen following **Package.json**
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

Inside the dependencies field we have defined lodash as following:
- "lodash": "*^4.0.0*" - notice the: **^**
  - The **^** indicates **NPM** to take the highest possible version beginning with Major Version: *4*
  - It is comparable to *4.x.x* - which would mean: upgrade to the latest **Minor** and **Patch** version compatible with **Major version**: *4* 


### Tidal
Now imagen this **Package.json**:
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
    "lodash": "~4.0.0"
  }
}
```

We now have replaced the **^** with a tidal **~**.
This is comparable to: *4.0.x*. Meaning that this will use the latest **Patch** version but remains the **Major** and **Minor** version

### Fixed version
You can also set the Version to be fixed by neither using a **caret** not a **tidal**:
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
    "lodash": "4.0.0"
  }
}
```
This will install the exactly specified version.