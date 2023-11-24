# Argument

Arguments are used to get the values from the command sender.

## @Arg Argument

`@Arg` is the most common argument. It is used to get the value from the command sender.

```java
@Command(name = "ban")
public class BanCommand {
    @Execute
    public void ban(@Arg Player player) {
        // ...
    }
}
```

## @Flag Argument

`@Flag` is used to get the value from the command sender, but it is optional.

```java
@Command(name = "ban")
public class BanCommand {
    @Execute
    public void ban(@Flag("-s") boolean isSilent) {
        // ...
    }
}
```

## @Join Argument

`@Join` is used to get the value from the command sender, it joins all arguments into one string.

```java
@Command(name = "ban")
public class BanCommand {
    @Execute
    public void ban(@Join String reason) {
        // ...
    }
}
```

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
