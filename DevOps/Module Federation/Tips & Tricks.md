- jest config:   
	 - Otherwise an error is thrown because of module federation imports
	 - These settings must be set in the project corresponding *jest.config.ts*
``` ts
  transformIgnorePatterns: [
    '<rootDir>/node_modules/(?!@angular-architects/module-federation(?:/|$))',
  ],
```

- module federation config for shell:
const { withModuleFederation } = require('@nrwl/angular/module-federation');

const config = require('./module-federation.config');

module.exports = withModuleFederation(config);