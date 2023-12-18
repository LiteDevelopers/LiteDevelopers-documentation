# IntelliJ IDEA Plugin

The LiteCommands **IntelliJ IDEA** Plugin enhances the development experience for LiteCommands framework users by providing a set of powerful features aimed at improving command and argument validation, offering helpful suggestions, and facilitating seamless migration. Below are the key features of the plugin:

## Command Viewer

The Command Viewer is a tool that allows you to view current commands in your command class. It provides a convenient way to navigate through your commands and view their structure with their properties.

![intellij-command-viewer.png](intellij-command-viewer.png) { width="350" }

## Command Validation

The Command Validation highlights any errors in your command methods and arguments and provides helpful suggestions to fix them. 

### Missing Annotation

![intellij-command-validation-no-annotation.png](intellij-command-validation-no-annotation.png)


### Primitive cannot be nullable

// TODO image

### Invalid route command

// TODO Image

## Legacy Annotations Migration

### 2.x -> 3.x
- `@Permission`
- `@Route` -> `@Command`
- `@Section` -> `@Command`
- `@Execute`
- `@Arg`
- `@Flag`
- `@Joiner` -> `@Join`

// TODO Image