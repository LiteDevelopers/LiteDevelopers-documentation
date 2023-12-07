# Adventure

LiteCommands Adventure is an extension for supporting Kyori Adventure features 
for platforms that are have native support for it. E.g. Paper, Purpur, Velocity, Minestom, etc.

But some platforms have built-in support for Adventure Kyori, so you don't need to add any additional dependencies to your project.
See the [Adventure Kyori Extensions](Adventure-Kyori.md) page to check if your platform has built-in support for Adventure Kyori.

> Make sure you have read the [Adventure Kyori](Adventure-Kyori.md) page before using this extension.
{style="note"}

## Dependency
Add the following dependency to your project:

<tabs>
<tab title="Gradle KTS">

```kotlin
implementation("dev.rollczi:litecommands-adventure:%latest_version%")
```
</tab>
<tab title="Maven">

```xml
<dependency>
    <groupId>dev.rollczi</groupId>
    <artifactId>litecommands-adventure</artifactId>
    <version>%latest_version%</version>
</dependency>
```
</tab>
</tabs>

## Registering the extension

Register the extension in the `LiteCommands` builder:

```java
.extension(new LiteAdventureExtension<SENDER>()
    .miniMessage(true)
    .legacyColor(true)
    .colorizeArgument(true)
    .serializer(this.miniMessage)
)
```

- `miniMessage()` - enables the MiniMessage support. (`<red>`, `<gradient:red:blue>`, `<#ff0000>`, etc.)
- `legacyColor()` - enables the legacy color support. `&c`, `&a`, etc.
- `colorizeArgument()` - enables the default colorizer for the `@Arg Component` argument.
- `serializer()` - sets the custom serializer (colorizer) for the `@Arg Component` argument. 
(if replaced, the `miniMessage()` and `legacyColor()` will be ignored)

<warning>
    Remember to replace <code>SENDER</code> with your sender type that corresponds to the platform you are using.
    See <a href="SENDER.md">What is SENDER?</a> for more information.
</warning>