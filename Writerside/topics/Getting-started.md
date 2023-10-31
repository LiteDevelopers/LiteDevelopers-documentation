# Getting started

This page will guide you through the process of setting up LiteCommands in your project.
After reading this page, you will be able to use LiteCommands in your project.

## Requirements

Please make sure that you have the following requirements before you start:

- Java 8 or higher
- Dependency manager as [Gradle](https://gradle.org/) or [Maven](https://maven.apache.org/)

## Installation

Setup your project with one of the following artifacts:

<tabs>
<tab title="Gradle KTS">

```kotlin
implementation("dev.rollczi:[[[ARTIFACT_ID|Platforms.md]]]:3.0.1")
```
</tab>

<tab title="Maven">

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