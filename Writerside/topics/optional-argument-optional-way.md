# @Arg Optional&lt;T&gt; (Optional way)

The `@Arg Optional<T>` is applied to parameters
within a command method that represent optional arguments. 

When an optional argument is not provided, the parameter will be set to `Optional.empty()` by default.

## Usage

Here is an example of how to use the `@Arg Optional<T>`:

```java
@Command(name = "day")
public class DayCommand {
    @Execute
    void day(@Context Player sender, @Arg Optional<World> world) {
        World world = world.orElse(sender.getWorld());
        
        world.setTime(1000);
    }
}
```

- `@Arg Player target` represents a required argument for a player.
- `@Arg Optional<World> world` represents an optional argument for a world. If the user provides a world, it will be captured in the world parameter. If not provided, world will be `Optional.empty()` by default.