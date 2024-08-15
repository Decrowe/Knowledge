- Consists of:
	- Host: Shell that hosts micro frontends
	- Remotes: Micro frontends which will be loaded by Remote
	
- Remotes can be developed and compiled seperately
- Ships with WebPack 5 as Plugin
- Host is an application for its own

- May be used Independant of Framework (not recommend)

- Remotes:
	- Devide main module and remote entry
	- Loaded dynamicly while runtime (on page load)

- Harmonizes great with mono repos
	- Sharing Libraries
	- Sharing runtime data

- Ready to use code generators
	- Angular Architects
	- Nrwl
## Static and Dynamic Loading
### Static
- Remotes defined staticly in source code
``` ts
module.exports = {
  name: 'mf-host',
  remotes: ['mf-remote-1', 'mf-remote-2'],
};
```
#### Con:
- Remotes must be known at compile time
- Not changable while runtime
#### Pro:
- Easy implementation
### Dynamic
``` ts
module.exports = {
  name: 'mf-host',
  remotes: [],
};
```
#### Con:
- More complex to implment
- Needs aditional Service to get Config 
	- Config holds data about remotes and their exposed modules
#### Pro:
- Changeable while runtime
	- Remotes can be added / removed 
- More flexible


## Example
- [[Module Federation - ShellUI]]