# ChatGPT Extension

The `litecommands-chatgpt` is a extension for supporting ChatGPT suggestions.

## Dependency

Add the following dependency to your project:

<tabs>
<tab title="Gradle KTS">

```kotlin
implementation("dev.rollczi:litecommands-chatgpt:%latest_version%")
```
</tab>
<tab title="Maven">

```xml
<dependency>
    <groupId>dev.rollczi</groupId>
    <artifactId>litecommands-chatgpt</artifactId>
    <version>%latest_version%</version>
</dependency>
```
</tab>

</tabs>


## Registering the extension

Register the extension in the `LiteCommands` builder:

```java
.extension(new LiteChatGptExtension<>(), configuration -> configuration
    .apiKey("OPENAI_API_KEY") // get your api key from https://platform.openai.com/account/api-keys
    .model(ChatGptModel.GPT_4) // get model from https://platform.openai.com/docs/models/gpt-3-5
    .temperature(1.0) // see more https://platform.openai.com/docs/guides/gpt/how-should-i-set-the-temperature-parameter
    .tokensLimit(2, 64) // min and max tokens
    .cooldown(Duration.ofMillis(500)) // cooldown between suggestions per player
)
```

## Example

You can use `@ChatGpt` annotation to get suggestions from ChatGPT.

```Java
@Command(name = "ban")
public class BanCommand {

    @Execute
    void ban(
        @Arg Player player,
        @Join @ChatGpt(topic = "Reason for ban") String reason
    ) {
        player.kickPlayer(reason);
    }

}
```

## Demo

See the demo of ChatGPT extension in action:

<video src="../images/chat-gpt/chat-gpt.mp4"/>
