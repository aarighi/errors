# Gradle builds

Smart and useful code for building projects with Gradle.

### Generate Javadoc JAR
*Note: tested with [jitpack.io](https://jitpack.io) - visit /javadoc to see the docs on jitpack*

Add the following to your `build.gradle`:
```Gradle
task javadocJar(type: Jar, dependsOn: javadoc) {
    classifier = 'javadoc'
    from javadoc.destinationDir
}

artifacts {
    archives javadocJar
}
```

### Generate Java sources JAR

Add the following to your `build.gradle`:
```Gradle
task sourcesJar(type: Jar, dependsOn: classes) {
    classifier = 'sources'
    from sourceSets.main.allSource
}

artifacts {
    archives sourcesJar
}
```
