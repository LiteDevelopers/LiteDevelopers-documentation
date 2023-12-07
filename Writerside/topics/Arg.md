# @Arg Argument

The `@Arg` annotation in the LiteCommands framework is used to define command method
parameters that represent required arguments. Arguments are essential pieces of information
that the user must provide when invoking a command. The `@Arg` annotation helps structure
and validate these inputs within the command method.

## Usage

The `@Arg` annotation is applied to parameters within a command method that represent
required arguments. Here is an example of how to use the `@Arg` annotation:

`/give <player> <type> <amount>`

```java
@Command(name = "give")
public class GiveCommand {
    @Execute
    void give(@Arg Player target, @Arg Material type, @Arg int amount) {
        // Command implementation
    }
}
```

In this example:

- `@Arg Player` target represents a required argument for a player.
- `@Arg Item` item represents a required argument for an item.
- `@Arg int` amount represents a required argument for an integer value.

## Example

Let's consider the following command usage:

```
/give JohnDoe diamond 3
```

In this case, the `target` parameter will represent the player "JohnDoe," 
the `item` parameter will represent the material DIAMOND,
and the `amount` parameter will represent the integer value 3.

<video src="../images/argument/arg/giveCommandExample.mp4" controls/>