# Jakarta Extension

The `litecommands-jakarta` is a extension for supporting Jakarta EE annotation validation.  
It allows you to use Jakarta EE Bean Validation annotations in the command arguments:

```Java
@Execute
void ban(@Arg @Size(min = 3, max = 16) String nick) {
    // Command implementation
}
```

## 0. Dependency
Add the following dependency to your project:

<tabs>
<tab title="Gradle KTS">

```kotlin
implementation("dev.rollczi:litecommands-adventure:%latest_version%")
```
</tab>
<tab title="Maven">

```xml
<dependency>
    <groupId>dev.rollczi</groupId>
    <artifactId>litecommands-jakarta</artifactId>
    <version>%latest_version%</version>
</dependency>
```
</tab>
</tabs>


## 1. Register Jakarta extension

Register the extension in the `LiteCommands` builder:

<tabs>

<tab title="Jakarta Extension">

```java
.extension(new LiteJakartaExtension<>(), config -> config
    // jakarta config ...
)
```
</tab>

<tab title="Jakarta Extension (without config)">

```java
.extension(new LiteJakartaExtension<>())
```
</tab>

</tabs>

Before configuration, it is worth knowing how the Jakarta Validation works in LiteCommands.

Suppose we have a command with a `nick` argument annotated with `@Size` and `@Pattern` annotations.

<img src="litecommands-jakarta.png" alt="litecommands jakarta" width="700"/>

**1*** - Argument `nick` (String)  
**2*** - `@Size` jakarta annotation (between 3 and 16 characters)  
**3*** - `@Pattern` jakarta annotation (only letters)  
**4*** - Jakarta Validation (`org.hibernate.validator:hibernate-validator` implementation)  
**5*** - Result of the validation (contains all violations)  
**6*** - Constraint violations message (joined header with all violation messages)  
**7*** - Violation message (specific message for each violation type)

See documentation for [Jakarta EE Bean Validation](https://jakarta.ee/specifications/bean-validation/3.0/apidocs/jakarta/validation/constraints/package-summary) to learn more about jakarta validation annotations.

## 2. Configure Jakarta messages

### 2.1. Constraint violations message

The `.constraintViolationsMessage()` method allows you to define a message for all constraint violations.

For example, we can define a message for all violations, which will contain the header and all violation messages.
The `result.asJoinedString()` method joins all violation messages into one string.

```Java
.constraintViolationsMessage((invocation, result) -> 
    "[!] Custom constraint violations: \n" + result.asJoinedString("\n")
)
```

Result of the method will be:

```Java
[!] Custom constraint violations:
<nick> - size must be between 3 and 16
<nick> - must match "[a-zA-Z]*"
```

### 2.2. Global violation message

The `.violationMessage()` method allows you to define a message for all violations.

For example, we can define a message for all violations, which will contain the parameter name and the violation message.

```Java
.violationMessage((invocation, violation) -> 
    " - " + violation.getParameterName() + ": " + violation.getMessage()
)
```

Result of the method will be:

```Java
[!] Custom constraint violations:
 - nick: size must be between 3 and 16
 - nick: must match "[a-zA-Z]*"
```

### 2.3. Violation messages for specific annotations

The `.violationMessage()` method allows you to define a message for specific annotations.

For example, we can define a message for the `@Size` annotation.  
The `violation.getAnnotation()` returns `@Size` annotation instance and allows you to get the annotation values.

```Java
.violationMessage(Size.class, (invocation, violation) -> {
    Size size = violation.getAnnotation();
    int min = size.min();
    int max = size.max();
    String name = violation.getParameterName();
    
    return " - " + name + ": between " + min + " and " + max;
})
```

Result of the method will be:

```Java
[!] Custom constraint violations:
 - nick: between 3 and 16
 - nick: must match "[a-zA-Z]*"
```

### 2.4. Violation messages for specific annotations in specific locale

First, we need to define how to get the locale for a command invocation. 

```Java
.locale(invocation -> {
    Locale locale = invocation.sender().getLocale(); 
    
    return locale != null ? locale : Locale.ENGLISH;
})
```

The `.violationMessage()` method allows you to define a message for specific annotations in specific locale.

For example, we can define a message for the `@Pattern` annotation in the English locale.

```Java
.violationMessage(Pattern.class, (invocation, violation) -> {
    Pattern pattern = violation.getAnnotation();
    String name = violation.getParameterName();
    
    return Locale.ENGLISH.equals(violation.getLocale())
        ? " - " + name + ": [English] must match " + pattern.regexp()
        : " - " + name + ": [Polish] musi pasować do " + pattern.regexp();
})
```

Result for the English locale will be:

```Java
[!] Custom constraint violations:
 - nick: [English] must match "[a-zA-Z]*"
 - nick: size must be between 3 and 16
```

Result for the other locale will be:

```Java
[!] Custom constraint violations:
 - nick: [Polish] musi pasować do "[a-zA-Z]*"
 - nick: size must be between 3 and 16
```

## 3. Full configuration

```Java
.extension(new LiteJakartaExtension<>(), config -> config
    // locale
    .locale(invocation -> {
        Locale locale = invocation.sender().getLocale(); 
        
        return locale != null ? locale : Locale.ENGLISH;
    })
    
    // constraint violations message
    .constraintViolationsMessage((invocation, result) -> 
        "[!] Custom constraint violations: \n" + result.asJoinedString("\n")
    )
    
    // global violation message
    .violationMessage((invocation, violation) -> 
        " - " + violation.getParameterName() + ": " + violation.getMessage()
    )
    
    // violation message for specific annotations
    .violationMessage(Size.class, (invocation, violation) -> {
        Size size = violation.getAnnotation();
        int min = size.min();
        int max = size.max();
        String name = violation.getParameterName();
        
        return " - " + name + ": between " + min + " and " + max;
    })
    
    .violationMessage(Pattern.class, (invocation, violation) -> {
        Pattern pattern = violation.getAnnotation();
        String name = violation.getParameterName();
        
        return Locale.ENGLISH.equals(violation.getLocale())
            ? " - " + name + ": [English] must match " + pattern.regexp()
            : " - " + name + ": [Polish] musi pasować do " + pattern.regexp();
    })
)
```

## 4. Advanced configuration

### 4.1. Custom validation factory

The `.validationFactory()` method allows you to define a custom validation factory.

For example, we can define a custom validation factory that will use the `org.hibernate.validator:hibernate-validator` implementation.

```Java
.validationFactory(Validation.byProvider(HibernateValidator.class)
     .configure()
     // hibernate validator config ...
     .buildValidatorFactory()
)
```

## Other examples

```Java
@Command(name = "ban")
public class BanCommand {

    @Execute
    void ban(
        @Arg @Pattern(regexp = "[a-zA-Z_]+") String name,
        @Arg @Future Instant date
    ) {
        // Command implementation
    }

}
```

```Java
@Command(name = "login")
public class LoginCommand {

    @Execute
    void login(@Arg @Size(min = 8) String password) {
        // Command implementation
    }

}
```

```Java
@Command(name = "email")
public class EmailCommand {

    @Execute
    void email(@Arg @Email String email) {
        // Command implementation
    }

}
```

```Java
@Command(name = "credit-card")

public class CreditCommand {

    @Execute
    void credit(@Arg @CreditCardNumber String cardNumber) {
        // Command implementation
    }

}
```

See also:
- [Jakarta EE Bean Validation annotations](https://jakarta.ee/specifications/bean-validation/3.0/apidocs/jakarta/validation/constraints/package-summary)
- [Hibernate Validator](https://docs.jboss.org/hibernate/stable/validator/reference/en-US/html_single/)