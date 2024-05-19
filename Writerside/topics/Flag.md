# @Flag Argument

The @Flag annotation in the LiteCommands framework is used to define flags for command methods. 
Flags are optional parameters that modify the behavior of a command. 
They are specified by adding certain keywords or symbols (flags) to the command input. 
Flags in LiteCommands provide a convenient way to enable 
or disable specific functionalities within a command.

## Usage

The `@Flag` annotation is applied to boolean parameters within a command method. 
Here is an example of how to use the `@Flag` annotation:

`/mute <player> -s`

```java
@Command(name = "mute")
public class MuteCommand {
    @Execute
    public void mute(
        @Arg Player player,
        @Flag("-s") boolean isSilent
    ) {
        // ..
    }
}
```

- `@Flag("-s")` declares a flag with the identifier `-s`.
- `boolean isSilent` is the corresponding parameter that will be set to true if the -s flag is provided in the command input. If the flag is not present, the parameter will be set to false by default.
- The identifier for the flag, typically a string starting with a symbol like `-` or `--`.

Example of command input and the corresponding result:

```
input: /mute Notch
result: isSilent = false

input: /mute Notch -s
result: isSilent = true
```

> The order of flags in the input does matter.
{ style="warning" }
> 
<video src="../images/argument/flag/muteCommandExample.mp4"/>