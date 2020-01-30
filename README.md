#dockerfile-maven-problem

Minimal reproduction of a bug with [dockerfile-maven](https://github.com/spotify/dockerfile-maven)

The project consists of two modules, each of which uses dockerfile-maven to produce a docker image. 
The module b depends on module a, and the dockerfile in module b inherits from module a.

Steps to reproduce: 
* clone this repository
* `mvn clean install`

Expected behaviour: both docker images are built successfully

Actual behaviour: the build for module b fails with an error: 
```
[ERROR] manifest for mfashby/image-a:1.0-SNAPSHOT not found: manifest unknown: manifest unknown
[WARNING] An attempt failed, will retry 1 more times
org.apache.maven.plugin.MojoExecutionException: Could no
```