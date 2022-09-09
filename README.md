# Configuration-Server

## Why?
TODO 

## Local (not Git)
TODO

## Containerize

### Local registry

The [Docker Registry 2.0](https://hub.docker.com/_/registry/) implementation for storing and distributing Docker images.

```shell
docker run -d -p 5000:5000 --restart always --name registry registry:2
```

### Build and push container 
Jib is a [Gradle](https://gradle.org/) plugin for building Docker and [OCI](https://github.com/opencontainers/image-spec) images for your Java applications.

```groovy
plugins {
    '...'
    id 'com.google.cloud.tools.jib' version '3.3.0'
    '...'
}


jib.allowInsecureRegistries = true
jib.to.image = "localhost:5000/${project.name}:${project.version}"

tasks.build.dependsOn tasks.jib
```

Every time the build-Task is called the image gets build as well and pushed to the registry


### Additional Links
[Syntax Markdown](https://www.markdownguide.org/extended-syntax/)
