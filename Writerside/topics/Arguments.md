# Argument

Arguments are used to parse the command sender's input and complete the command.



Sometimes you may want to limit the number of arguments that will be joined.
```java
@Join(limit = 2)
```

Or you may want to join arguments with a different separator.
```java
@Join(separator = ", ")
```

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
