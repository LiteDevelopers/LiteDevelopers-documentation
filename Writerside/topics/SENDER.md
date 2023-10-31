# What is SENDER?

LiteCommands uses the `SENDER` type in the documentation to indicate the sender type that corresponds to the platform you are using.

Depending on the platform, the sender type may be different.

| Platform   | Sender Type     | Sender Import                                   |
|------------|-----------------|-------------------------------------------------|
| Bukkit     | `CommandSender` | `org.bukkit.command.CommandSender`              |
| Velocity   | `CommandSource` | `com.velocitypowered.api.command.CommandSource` |
| BungeeCord | `CommandSender` | `net.md_5.bungee.api.CommandSender`             |
| Minestom   | `CommandSender` | `net.minestom.server.command.CommandSender`     |
| JDA        | `User`          | `net.dv8tion.jda.api.entities.User`             |