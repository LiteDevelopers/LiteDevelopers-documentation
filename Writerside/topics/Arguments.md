# Argument

Argument is a value that is passed to the command. 
For example, you can use the `String` object as an argument in your command:

<tabs>
<tab title="Annotation">

```java
@Command(name = "say")
public class SayCommand {
    @Execute
    public void ban(@Arg String text) {
        // ...
    }
}
```
</tab>
<tab title="Programmatically">

```java
new LiteCommand<CommandSender>("say")
    .argument("text", String.class)
    .onExecute(context -> {
        String text = context.argument("text", String.class);
        // ...
    })
```
</tab>

<tab title="Programmatic (class)">

```java
public class SayCommand extends LiteCommand<CommandSender> {
    public SayCommand() {
        super("say");
        argument("text", String.class);
    }

    @Override
    public void execute(Context<CommandSender> context) {
        String text = context.argument("text", String.class);
        // ...
    }
}
```
</tab>
</tabs>

LiteCommands supports multiple argument types. You can find all of them in the table below.

| Argument Type | Values                                         | Platforms |
|---------------|------------------------------------------------|-----------|
| `Boolean`     | `true`, `false`                                | *         |
| `Byte`        | `-128` - `127`                                 | *         |
| `Short`       | `-32768` - `32767`                             | *         |
| `Integer`     | `-2147483648` - `2147483647`                   | *         |
| `Long`        | `-9223372036854775808` - `9223372036854775807` | *         |
| `Float`       | `0.0` - `3.4028235E38`                         | *         |
| `Double`      | `0.0` - `1.7976931348623157E308`               | *         |
| `String`      | Any string                                     | *         |
| `Enum`        | Any enum                                       | *         |
| `Duration`    | 1d, 1h, 1m, 1s, 1ms                            | *         |
| `Period`      | 1y, 1mo, 1w, 1d                                | *         |
| `Instant`     | yyyy-MM-dd HH:mm:ss                            | *         |
| `Component`   | Any string                                     | Adventure |
| `Component`   | Any string                                     | Adventure |
| `Player`      | Any player                                     | Bukkit    |
| `World`       | Any world                                      | Bukkit    |
| `Location`    | Any location                                   | Bukkit    |
| `Player`      | Any player                                     | Minestom  |

// TODO: Add more argument types
| `UUID`          | Any UUID                                       | All       |
| `Color`         | Any color                                      | All       |
| `Enchantment`   | Any enchantment                                | All       |
| `ChatColor`     | Any chat color                                 | All       |

