# Parameters compile flag

Add `-parameters` flag to your compiler to use all features of LiteCommands:
Depending on the build system you are using, add the following code to your project:

<tabs group="languages">
<tab title="Gradle KTS" group-key="gradle">

Add the following line to your `build.gradle.kts` file:
<br/><br/>

```kotlin
tasks.withType<JavaCompile> {
    options.compilerArgs.add("-parameters")
}
```
</tab>

<tab title="Gradle Groovy" group-key="groovy">

Add the following line to your `build.gradle` file:
<br/><br/>

```kotlin
tasks.withType(JavaCompile) {
    options.compilerArgs << "-parameters"
}
```
</tab>

<tab title="Maven" group-key="maven">

Add the following lines to your `pom.xml` file in the `plugins` section:
<br/><br/>

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-compiler-plugin</artifactId>
    <version>3.11.0</version>
    <configuration>
        <compilerArgs>
            <arg>-parameters</arg>
        </compilerArgs>
    </configuration>
</plugin>
```
</tab>
</tabs>

<tip>
Parameters are used to get the name of the parameter in the method. 
Without this flag, the name of the command arguments will be <code>arg0</code>, <code>arg1</code>, etc. 

Also you can define the name of the parameter in the <code>@Arg("name")</code> annotation.
</tip>
