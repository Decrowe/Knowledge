# Version Mismatch

The *Shell* and the *Remotes* can share their used libraries. This reduces bundle size and and compile time. Therefor they both have to give information about their used libararies. 

The problem is: What happens if the Shell does not know the Remotes yet?

In that case the *Shell* and the *Remotes* are not able to commit to specific versions of the shared libraries. The *Shell* will then decide to take its own needed version of the library.

When now a *Remote* is loaded and its version is compatible with the *Remotes* one, it will it.
Otherwise when the *Remote* is loaded and is incompatible with the *Shells* version the *Remote* will load its own version.

To prevent this mismatching the entrypoints of the *Remotes* can be defined at compile time in the shell. But that means a potential loss of dynamics. 

See the [documentation](https://www.angulararchitects.io/en/aktuelles/getting-out-of-version-mismatch-hell-with-module-federation/).
