# @OptionalArg (null way)

The `@OptionalArg` annotation is applied to parameters within a command method that represent optional arguments.

When an optional argument is not provided, the parameter will be set to `null` by default.

## Usage
Here is an example of how to use the @OptionalArg annotation:

```java
@Command(name = "day")
public class DayCommand {
    @Execute
    void day(@Context Player sender, @OptionalArg World world) {
        if (world == null) {
            world = sender.getWorld();
        }
        
        world.setTime(1000);    
    }
}
```

In this example:

- `@Arg Player target` represents a required argument for a player.
- `@OptionalArg Location destination` represents an optional argument for a location. If the user provides a location, it will be captured in the destination parameter. If not provided, destination will be null by default.