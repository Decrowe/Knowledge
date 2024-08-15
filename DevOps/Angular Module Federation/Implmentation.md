# Activation

**With package: angular-architects/module-federation**
```powershell
ng add @angular-architects/module-federation --project shell --port 4200 --type host
 ng add @angular-architects/module-federation --project mfe1 --port 4201 --type remote
```
**With NPM**
```powershell
npm i @angular-architects/module-federation -D 
 
 ng g @angular-architects/module-federation:init --project shell --port 4200 --type host
 ng g @angular-architects/module-federation:init --project mfe1 --port 4201 --type remote
```
This command does the following:
-   Generating skeleton of `webpack.config.js` for using module federation
	- Only partial config!
-   Installing custom builder making webpack within CLI use generated `webpack.config.js`.
-   Assigning new port for ng serve so that several projects can be served simultaneously

___

## The Shell
### Routes
Remotes can be lazy loaded. Therefor routes must be defined:
```typescript
export const APP_ROUTES: Routes = [
     {
       path: 'remote_name',
       loadChildren: () => import('mfe1/Module').then(m => m.FlightsModule)
     },
 ];
```
'mfe1/Module' does not exist, It is just a virtual path pointing to another project.

### Typescript Compiler
```typescript
// decl.d.ts
 declare module 'mfe1/Module';
```
### Webpack Config
```typescript
const { shareAll, withModuleFederationPlugin } = require('@angular-architects/module-federation/webpack');
 
 module.exports = withModuleFederationPlugin({
 
   remotes: {
     "mfe1": "http://localhost:4201/remoteEntry.js",
   },
 
   shared: {
     ...shareAll({ singleton: true, strictVersion: true, requiredVersion: 'auto' }),
   },
 
 });
```
**remotes**
- defines adress of entry points of **Micro Frontends**
**shared**
- defines libraries that are used by **Shell** and also **Micro Frontends**
	- shareAll(): shares all dependencies of package.json
	- singleton: true + strictVersion: true: Emits *error* at runtime if if **Shell** and **Micro Frontends** need different incompetible versions
	- singleton: false + strictVersion: true: Emits *warning* at runtime if if **Shell** and **Micro Frontends** need different incompetible versions
	- requiredVersion: 'auto': looks up used versions in package.json

____

## Micro Frontends (Remote)
Modules that should be load by the Shell must be configured:
```typescript
const { shareAll, withModuleFederationPlugin } = require('@angular-architects/module-federation/webpack');
 
 module.exports = withModuleFederationPlugin({
 
   name: 'mfe1',
 
   exposes: {
     './Module': './projects/mfe1/src/app/flights/flights.module.ts',
   },
 
   shared: {
     ...shareAll({ singleton: true, strictVersion: true, requiredVersion: 'auto' }),
   },
 
 });
```
### Exposing a module
'exposes': defines the public name under which the module is exposed

Remember that line of code? 
``` typescript
loadChildren: () => import('mfe1/Module')
```
- 'mfe1' links to the adress of the entry point of the *Micro Frontend* and is defined on the *Shell*
- 'Module' links to the exposed Module of the *Micro Frontend* and is designed on the *Micro Frontend* 
___

## Sharing Dependencies
In the first step all dependencies of package.json where shared.
In further steps you would only share certain dependencies to keep the bundle size low and the performance high.

Therefor we switch from the helper function: shareAll() to share().
```javascript
// Import share instead of shareAll:
 const { share, withModuleFederationPlugin } = require('@angular-architects/module-federation/webpack');
 
 module.exports = withModuleFederationPlugin({
 
     // Explicitly share packages:
     shared: share({
         "@angular/core": { singleton: true, strictVersion: true, requiredVersion: 'auto' }, 
         "@angular/common": { singleton: true, strictVersion: true, requiredVersion: 'auto' }, 
         "@angular/common/http": { singleton: true, strictVersion: true, requiredVersion: 'auto' },                     
         "@angular/router": { singleton: true, strictVersion: true, requiredVersion: 'auto' },
     }),
 
 });
```
Using this we can define exactly which dependency we would like to share and can configure them seperately.