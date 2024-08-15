# Pros and Cons of Angular Module Federation:

## Pro
- Official method for micro frontends
- Dynamic loading of seperate applications at run-time
- Small build times per micro frontend
- NO framework
	- Plugin for Webpack 
- Micro frontends work independant from each other
- Micro frontends can be developed independant from each other
- Scalable/expendable - Good for huge code bases
- Easy integration in existing projects
- [[Dynamic Module Federation]]
- Reduce Compile Time

## Contra
- Shared libraries must have the same versions
	- Can create dependencies between different application parts
- Dependency to Webpack
- Complexity at bigger projects
	


## Something from the real world
This is a real world exmaple of an existing and well designed Angular Web Page based on Module federation in combination with NX Monorepos and DDD
https://www.angulararchitects.io/en/aktuelles/interview-micro-frontends-and-module-federation-at-cube-bikes/
https://www.cube.eu/de-de/e-bikes/mountainbike/hardtail/reaction-hybrid