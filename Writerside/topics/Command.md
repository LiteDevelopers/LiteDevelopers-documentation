# Command

The command structure is the most important part of the command. It is the structure that determines how the command will be executed.

For example, the command `/time set day` 

```java
@Command(name = "time")
public class TimeCommand {
    
    @Execute(name = "set day")
    public void day() {
        // ... /time set day
    }
    
}
```

You can do the same thing with the other way:
    
```java
@Command(name = "time set")
public class TimeSetCommand {
    
    @Execute(name = "day")
    public void day() {
        // ... /time set day
    }
    
}
```

It not requires to use the `name` parameter in the `@Execute` annotation.
For example `/day` command:

```java
@Command(name = "day")
public class DayCommand {
    
    @Execute
    public void day() {
        // ... /day
    }
    
}
```