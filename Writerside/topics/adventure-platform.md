# Install (adventure-platform)

LiteCommands Adventure Platform is an extension for supporting Kyori Adventure features 
for platforms that are doesn't have native support for it. E.g. Bukkit, BungeeCord, etc.

> Make sure you have read the [Adventure Kyori](Adventure-Kyori.md) page before using this extension.
{style="note"}

> Before you start, you need to add the [Adventure Platform](https://docs.advntr.dev/platform/index.html) to your project.

## Dependency
Add the following dependency to your project:

<tabs>
<tab title="Gradle KTS">

```kotlin
implementation("dev.rollczi:litecommands-adventure-platform:%latest_version%")
```
</tab>
<tab title="Maven">

```xml
<dependency>
    <groupId>dev.rollczi</groupId>
    <artifactId>litecommands-adventure-platform</artifactId>
    <version>%latest_version%</version>
</dependency>
```
</tab>
</tabs>

## Registering the extension

Register the extension in the `LiteCommands` builder:

```java
.extension(new LiteAdventurePlatformExtension<>(this.audienceProvider), config -> config
    .miniMessage(true)
    .legacyColor(true)
    .colorizeArgument(true)
    .serializer(this.miniMessage)
)
```

- `audienceProvider` - the provider for the `Audience` object. If you don't have it, read the [Adventure Platform](https://docs.advntr.dev/platform/index.html) page for more information.

- `miniMessage()` - enables the MiniMessage support. (`<red>`, `<gradient:red:blue>`, `<#ff0000>`, etc.)
- `legacyColor()` - enables the legacy color support. `&c`, `&a`, etc.
- `colorizeArgument()` - enables the default colorizer for the `@Arg Component` argument.
- `serializer()` - sets the custom serializer (colorizer) for the `@Arg Component` argument. (if replaced, the `miniMessage()` and `legacyColor()` will be ignored)

<warning>
    Remember to replace <code>SENDER</code> with your sender type that corresponds to the platform you are using.
    See <a href="SENDER.md">What is SENDER?</a> for more information.
</warning>

## Full Example

> See [this full example](https://github.com/Rollczi/LiteCommands/tree/master/examples/bukkit-adventure-platform)
> to check how to use this extension in your project.