# Getting started

This page will guide you through the process of adding LiteCommands to your project.
<tip>
LiteCommands requires Java 8 or higher.
</tip>

### Add Panda Repository

Depending on the build system you are using, add the following repository to your project:

<tabs>
<tab title="Gradle KTS">

Add the following line to your `build.gradle.kts` file in the `repositories` section:
<br/><br/>

```kotlin
maven("https://repo.panda-lang.org/releases")
```
</tab>

<tab title="Maven">

Add the following lines to your `pom.xml` file in the `repositories` section:
<br/><br/>

```xml
<repository>
    <id>panda-repo</id>
    <url>https://repo.panda-lang.org/releases</url>
</repository>
```
</tab>
</tabs>

### Add LiteCommands Dependency

<tabs>
<tab title="Gradle KTS">

Add the following line to your `build.gradle.kts` file in the `dependencies` section:
<br/><br/>

```kotlin
implementation("dev.rollczi:[[[ARTIFACT_ID|Platforms.md]]]:3.0.1")
```
</tab>

<tab title="Maven">

Add the following lines to your `pom.xml` file in the `dependencies` section:
<br/><br/>

```xml
<dependency>
    <groupId>dev.rollczi</groupId>
    <artifactId>[[[ARTIFACT_ID|Platforms.md]]]</artifactId>
    <version>3.0.1</version>
</dependency>
```
</tab>

</tabs>

> Replace [ARTIFACT_ID](Platforms.md) with the artifact ID of the platform you want to use. 
> You can find all of them in the [Platforms](Platforms.md) page.
{ style="warning" }