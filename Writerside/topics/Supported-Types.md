# Supported Types

LiteCommands supports multiple argument types. You can find all of them in the table below.

| Argument Type     | Values                                         | Example             |
|-------------------|------------------------------------------------|---------------------|
| `Boolean`         | `true`, `false`                                | `true`              |
| `Byte`            | `-128` - `127`                                 | `10`                |
| `Short`           | `-32768` - `32767`                             | `1000`              |
| `Integer`         | `-2147483648` - `2147483647`                   | `1000000000`        |
| `Long`            | `-9223372036854775808` - `9223372036854775807` | `100000000000`      |
| `Float`           | `0.0` - `3.4028235E38`                         | `10.5`              |
| `Double`          | `0.0` - `1.7976931348623157E308`               | `10.5`              |
| `String`          | Any string                                     | `text`              |
| `String` (Quoted) | Any string surrounded by quotes                | `"Hello World"`     |
| `Enum`            | Any enum                                       | `WORLD`             |
| `Duration`        | `Xd`, `Xh`, `Xm`, `Xs`, `Xms`,                 | `10m`, `5d4h30m15s` |
| `Period`          | 1y, 1mo, 1w, 1d                                | `1y`, `12mo`, `1w`  |
| `Instant`         | yyyy-MM-dd HH:mm:ss                            | `2021-01-01 00:00`  |



