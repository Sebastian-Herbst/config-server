# Config-Service

The config-service is responsible for all configurations of the services. On boot, the service sends a request to this service based on the service name and profile.

## Local (not Git)
At the moment, the configurations are build in this service. So a change of a configuration will result in a new deployment including a new container. 
This will be changed, but for the moment it should work.

## Containerize
This service can be containerized via [Google Jib](https://github.com/GoogleContainerTools/jib). Jib is a [Gradle](https://gradle.org/) plugin for building Docker and [OCI](https://github.com/opencontainers/image-spec) images for your Java applications.

### Local registry
In the file build.gradle the container is published to a local repository at [raspberrypi-dev](http://raspberrypi-dev:11002/). If you are using a different repository you have to change this.

```groovy
plugins {
    '...'
    id 'com.google.cloud.tools.jib' version '3.3.0'
    '...'
}


jib.allowInsecureRegistries = true
jib.container.creationTime = 'USE_CURRENT_TIMESTAMP'
jib.to.image = "raspberrypi-dev:11001/${project.name}:${project.version}"
```


### Additional Links
[Syntax Markdown](https://www.markdownguide.org/extended-syntax/)</br>
[Banner-Generator](https://devops.datenkollektiv.de/banner.txt/index.html) Font: slant
