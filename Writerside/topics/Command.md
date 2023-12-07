# Command

<tldr>
    <p>
        Annotations <shortcut>@Command</shortcut> <shortcut>@Execute</shortcut>
    </p>
</tldr>

The command structure is the most important part of the command. It is the structure that determines how the command will be executed.

For example, the command `/time day` 

```java
@Command(name = "time")
public class TimeCommand {
    
    @Execute(name = "day")
    public void day() {
        // ... set time to day
    }
    
}
```
