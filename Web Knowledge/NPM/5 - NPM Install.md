# Installing A New Package
When you want to install a new package to your project you use:

``` shell
npm install "package-name"
```

This will result in the following:
1) **package.json** is updated
2) **package-lock.json** is updated
3) New package is added to the **node_modules** folder

## Under The Hood
When using:

``` shell
npm install "package-name"
```

NPM does actually following steps:
1) Looks up metadata of package. Most importantly:
	1) tarball file (Includes all package files packed into one single file (.tar) and compressed (.gz): .tgz)
	2) shasum
2) Gets tarball
3) Compares the shasum (metadata and actual download) 
4) Unzips and unpacks tarball
5) Adds files to **node_modules**

You can see the package metadata using this command:

``` shell
npm view "package-name"
```