# @Join Argument

The `@Join` annotation in the LiteCommands framework is used to concatenate
multiple arguments into a single string. This annotation is particularly
useful when you want to combine several input parameters into a cohesive
text representation, such as creating a reason for a ban command.

## Usage
The `@Join` annotation is applied to a parameter within a command method
that should be treated as a concatenated string. Here is an example of
how to use the `@Join` annotation:

```Java
@Command(name = "ban")
public class BanCommand {
    @Execute
    public void ban(
        @Arg Player target,
        @Join String reason
    ) {
        // Command implementation
    }
}
```

## Example
Let's consider the following command usage:

```
/ban JohnDoe Offensive language and behavior
In this case, the `target` parameter will represent the player "JohnDoe", and the `reason` parameter will represent the string "Offensive language and behavior." The @Join annotation automatically combines all the remaining text arguments into the reason parameter.
```

## Notes
- The `@Join `annotation is particularly useful when you want to capture a variable number of arguments into a single string.
- The joined string includes spaces between the original arguments, making it suitable for textual descriptions or reasons.

## Additional Options



In LiteCommands, the @Join annotation offers additional options for customization, namely limit and separator. The limit option allows developers to specify the maximum number of arguments to include in the joined string, providing control over the length of the concatenated result. On the other hand, the separator option enables developers to define a custom string that separates each joined argument, allowing for fine-grained control over formatting. These options enhance the flexibility of the @Join annotation, allowing developers to tailor the concatenated string output to their specific needs.