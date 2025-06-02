# Takari POM

[![Maven Central](https://img.shields.io/maven-central/v/io.takari/takari.svg?label=Maven%20Central)](https://search.maven.org/artifact/io.takari/takari)
[![Verify](https://github.com/takari/takari-pom/actions/workflows/ci.yml/badge.svg)](https://github.com/takari/takari-pom/actions/workflows/ci.yml)


The parent POM for all projects of Takari allowing publishing to the Central
Repository and centralized plugin and configuration management. The publishing
uses Sonatype Central Portal service.

This parent uses Takari Lifecycle and has the following **build time requirement**:
* Java 17+
* Maven 3.9+

Note: user doing the publishing must have set up the namespace and have access to
target namespace, as documented on [Central Portal](https://central.sonatype.org/register/central-portal/).
Also, the user `settings.xml` must contain the properly filled in [release-settings-template.xml](.mvn/release-settings-template.xml)
snippets. User has to generate publishing tokens on Portal and replace them in the
XML snippet above.

To check your publishing status/setup, use `mvn njord:status -Dnjord.enabled`.

## Usage

Just add a parent segment with the latest version to your project

```
  <parent>
    <groupId>io.takari</groupId>
    <artifactId>takari</artifactId>
    <version>70</version>
  </parent>
```

To release your project you can use the usual Maven release process.

```
mvn release:prepare release:perform
```

This publishes the project to the
[Central Repository](http://central.sonatype.org/) and hence the
binaries are available wherever Central is available.

SNAPSHOT version deployments emulating the full release build can be done with

```
mvn clean deploy -P takari-release
```

Snapshot binaries (by default configuration) end up on 
https://central.sonatype.com/repository/maven-snapshots/

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

