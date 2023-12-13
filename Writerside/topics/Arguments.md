# Argument

Arguments are used to parse the command sender's input and complete the command.





## Full Example

```java
@Command(name = "ban")
public class BanCommand {
    @Execute
    public void ban(@Arg Player player, @Flag("-s") boolean isSilent, @Join String reason) {
        // ...
    }
}
```
