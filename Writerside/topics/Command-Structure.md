# Command Structure

<tldr>
    <p>
        Annotations <shortcut>@Command</shortcut> <shortcut>@Execute</shortcut>
    </p>
</tldr>

The command structure is the most important part of the command. It is the structure that determines how the command will be executed.

For example, the command structure of the `/ban` command is:

```java
@Command(name = "ban")
public class BanCommand {

    @Execute
    void ban() {
        // ...
    }

}
```

For the `/ban ip` command, the structure is:

```java
@Command(name = "ban")
public class BanCommand {

    @Execute(name = "ip")
    void banIp() {
        // ...
    }

}
```
