# Jakarta Extension

The `litecommands-jakarta` is a extension for supporting Jakarta EE annotation validation.

```Java
@Execute
void ban(@Arg @Pattern(regexp = "[a-zA-Z_]+") String name)
```

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
    <artifactId>litecommands-jakarta</artifactId>
    <version>%latest_version%</version>
</dependency>
```
</tab>
</tabs>


## Registering the extension

Register the extension in the `LiteCommands` builder:

```java
.extension(new LiteJakartaExtension<>())
```

## Example

```Java
@Command(name = "ban")
public class BanCommand {

    @Execute
    void ban(
        @Arg @Pattern(regexp = "[a-zA-Z_]+") String name,
        @Arg @Future Instant date,
    ) {
        // Command implementation
    }

}
```

See documentation for [Jakarta EE Bean Validation](https://jakarta.ee/specifications/bean-validation/3.0/apidocs/jakarta/validation/constraints/package-summary) to learn more about validation annotations.

## Handling validation errors

If the validation fails, then the handler for `JakartaResult` will be called.

```Java
public class JakartaResultHandler implements ResultHandler<SENDER, JakartaResult> {

    @Override
    public void handle(Invocation<SENDER> invocation, JakartaResult result, ResultHandlerChain<SENDER> chain) {
        for (ConstraintViolation<Object> violation : result.getViolations()) {
            String message = violation.getMessage();
            String messageKey = violation.getMessageTemplate();
            
            // ... (send message to the sender)
        }
    }

}
```

And register it in the `LiteCommands` builder:

```Java
.result(new JakartaResultHandler())
```