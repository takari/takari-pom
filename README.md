# Takari POM

The parent POM for all projects of Takari allowing deployment to the Central
Repository and centralized plugin and configuration management.

## Usage

Just add a parent segment with the latest version to your project

```
  <parent>
    <groupId>io.takari</groupId>
    <artifactId>takari</artifactId>
    <version>51</version>
  </parent>
```

To release your project you can use the usual Maven release process.

```
mvn release:prepare release:perform
```

This deploys the project to the
[Central Repository](http://central.sonatype.org/) and hence the
binaries are available whereever Central is available. Prior to that the staging
repository needs to be closed and released on [OSSRH](https://oss.sonatype.org/).

SNAPSHOT version deployments emulating the full release build can be done with

```
mvn clean deploy -P takari-release
```

Binaries end up on https://oss.sonatype.org/content/repositories/snapshots/

The project uses the 
[Takari Lifecycle](http://takari.io/book/40-lifecycle.html) for resources,
compiler, jar, install and deploy replacement. 

## Build

As usual

```
mvn clean install
```

## Release

Same as for usage of the project...

