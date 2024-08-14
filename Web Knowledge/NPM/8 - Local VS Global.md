# What For?
The idea of NPM packages is that you have the nesseccary packages/dependencies needed by your project very close to it.

This ensures that wherever and whenever you run npm install inside the project the result is always the same. You do not have to worry about the environment too much.

## Local Packages
Local packages are packages needed by your project. These can be e.g.: libs for building or testing your applciaiton.

## Global Packages
Global packages however are packages which are not needed by a certain project. 
Global packages can be accessed globally from the cli.

For example, you would like to create a new angular Application. Therefore you would first install the Angular CLI globally and afterwards call the Angular CLI in your terminal:

``` shell
# Install Angular CLI globally (-g)
npm install -g @angular/cli

# Call the globally installed package
ng new "application-name"
```

## Global Packages Location

To get the location of the folder where your global packages are saved call:

``` shell
npm root -g
```

Inside this folder you will find you globally installed packages.