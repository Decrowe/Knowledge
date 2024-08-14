# Dynamic Module Federation

- There are 2 ways of including *Micro Frondends* to the *Shell*

1) **Static** declaration of *Micro Frontends* via JSON-File
2) **Dynamic** declaration using a Web API

The static approach forces the shell to know which *Micro Frontends* will be used at compile time.
That means you can only load *Micro Frontends* that are declared before compiling.
When another *Micro Frontend* is availale it is not possible to load it without to change the settings and recompile it which means, that the *Shell* has to be built and deployed every time.

The dynamic approach gives more flexibility. It allows the *Shell* to laod and remove *Micro Frontends* during runtime without recompiling.

___

# Pros and Cons of Dynamic Module Federation

## Pro
- No need of recompiling for adding *Micro Frontends*
- *Micro Frontends* can be loaded and removed durign runtime
- Provides possibility to select available *Micro Frontends* for Admins etc.
- *Micro Frontends* integration can be done without touching *Shell*
- Shell becomes more flexible while runtime

## Contra
- More complexity
- Maybe overkill for smaller Projects or projects with certain amount of *Micro Frontends*

___

## Dynamic Linking of Micro Frontends
In this case the the upfront of the *Micro Frontends* are known and it should be possible to change the entrypoints at runtime.
![[Pasted image 20230214102943.png]]

To mak use of that approach the *Shell* the Manifest is editable and thererfor must be reloaded every time it changes.

### Generating the manifest
```powershell
ng g @angular-architects/module-federation --project shell --port 4200 --type dynamic-host
```
This commands generates following:
- Webpack configuration
- Manifest
- Some Code in main.ts which loads the manifest

### Loading the Micro Frontends
```typescript
import { Routes } from '@angular/router';
 import { HomeComponent } from './home/home.component';
 import { loadRemoteModule } from '@angular-architects/module-federation';
 
 export const APP_ROUTES: Routes = [
     {
       path: '',
       component: HomeComponent,
       pathMatch: 'full'
     },
     {
       path: 'CamCheck',
       loadChildren: () => loadRemoteModule({
           type: 'manifest',
           remoteName: 'mfe1',
           exposedModule: './Module'
         })
         .then(m => m.CamCheckModule)
     },
     {
       path: 'Licensing',
       loadChildren: () => loadRemoteModule({
           type: 'manifest',
           remoteName: 'mfe2',
           exposedModule: './Module'
         })
         .then(m => m.LicensingModule)
     },
 ];
```

"remoteName" points to the key and therefor to the current url in the manifest.

### Configurig the Micro Frontends
```powershell
npm i -g @angular-architects/module-federation -D
 
 ng g @angular-architects/module-federation --project mfe1 --port 4201 --type remote
```

This command generates the config file for the remotes.
In this config file the exposed module is declared:
```typescript
 const { shareAll, withModuleFederationPlugin } = require('@angular-architects/module-federation/webpack');
 
 module.exports = withModuleFederationPlugin({
 
   name: 'mfe1',
 
   exposes: {
     // Adjusted line:
     './Module': './projects/mfe1/src/app/cam-check/cam-check.module.ts'
   },
 
   shared: {
     ...shareAll({ singleton: true, strictVersion: true, requiredVersion: 'auto' }),
   },
 
 });
```

Add routing links to your template and you are good to go:
```html
 <ul>
     <li><img src="../assets/angular.png" width="50"></li>
     <li><a routerLink="/">Home</a></li>
     <li><a routerLink="/CamCheck">CamCheck</a></li>
     <li><a routerLink="/Licensing">Licensing</a></li>
 </ul>
 
 <router-outlet></router-outlet>
```

## Even more Dynamic 
In case you do not know, how many *Micro Frontends* will be used, the *Shell* must be able to add and remove them at runtime.

In order to provide such functions, some additional information must be added:

1) Additional metadata to the manifest:
```json
{
     "mfe1": {
         "remoteEntry": "http://localhost:4201/remoteEntry.js",
 
         "exposedModule": "./Module",
         "displayName": "CamCheck",
         "routePath": "CamCheck",
         "ngModuleName": "CamCheckModule"
     },
     "mfe2": {
         "remoteEntry": "http://localhost:4202/remoteEntry.js",
 
         "exposedModule": "./Module",
         "displayName": "Licensing",
         "routePath": "Licensing",
         "ngModuleName": "LicensingModule"
     }
 }
```

Only "remoteEntry"- property is predefined and not custom.

2) Add datatype for Custom Configuration
```typescript
 import { Manifest, RemoteConfig } from "@angular-architects/module-federation";
 
 export type CustomRemoteConfig = RemoteConfig & {
     exposedModule: string;
     displayName: string;
     routePath: string;
     ngModuleName: string;
 };
 
 export type CustomManifest = Manifest<CustomRemoteConfig>;
```

- CustomRemoteConfig: represents the entries in the manifest
- CustomManifest: represents the whole manifest

3) Add function to iterate through the manifest and return all the routes
```typescript
 import { loadRemoteModule } from '@angular-architects/module-federation';
 import { Routes } from '@angular/router';
 import { APP_ROUTES } from '../app.routes';
 import { CustomManifest } from './config';
 
 export function buildRoutes(options: CustomManifest): Routes {
 
     const lazyRoutes: Routes = Object.keys(options).map(key => {
         const entry = options[key];
         return {
             path: entry.routePath,
             loadChildren: () => 
                 loadRemoteModule({
                     type: 'manifest',
                     remoteName: key,
                     exposedModule: entry.exposedModule
                 })
                 .then(m => m[entry.ngModuleName])
         }
     });
 
     return [...APP_ROUTES, ...lazyRoutes];
 }
```
