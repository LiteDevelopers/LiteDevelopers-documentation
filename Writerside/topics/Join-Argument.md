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
target = JohnDoe
reason = Offensive language and behavior
```

## Notes
- The `@Join` annotation is particularly useful when you want to capture a variable number of arguments into a single string.
- The joined string includes spaces between the original arguments, making it suitable for textual descriptions or reasons.

## Additional Options


- The `limit` option allows developers to specify the
maximum number of arguments to include in the joined string. 
- On the other hand, the `separator` option enables developers to define a custom string that separates each joined
argument, allowing for fine-grained control over formatting.

```java
@Command(name = "ban")
public class BanCommand {
    @Execute
    public void ban(
        @Arg Player target,
        @Join(limit = 10, separator = "-") String reason
    ) {
        // Command implementation
    }
}
```

Let's consider the following command usage:

```
/ban JohnDoe Offensive language and behavior
target = JohnDoe
reason = Offensive-language-and-behavior
```