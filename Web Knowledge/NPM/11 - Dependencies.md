# Dependenciy Kinds
- dependencies
- devDependencies
- peerDependencies

By default each new installed dependency is installed inside the dependencies field inside the **package.json**.

## Dependcies
In this field you will list all dependencies which are abslutely required to run your application. 

Example:
When you use Lodash inside your project you must list it inside the dependencies field since your javascript would throw an error without it.
___
## DevDependencies
In this field you list dependencies which are relevant in order to develop your project. 

Exmaples:
- Babel
- Typescript
- Babel

When you run: 
```shell
npm install
```
in production mode dependencies inside the **devDependencies** field are not installed.
___
## PeerDependencies
A **PeerDependency** is not installed automatically by **NPM**. A dependency has to be installed manually.

Of course **NPM** checks the peerDependencies field inside your **package.json** and will give you warnings if there is a **PeerDependency** listed that is not installed.
