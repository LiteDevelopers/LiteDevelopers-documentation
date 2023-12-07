# Configuration

Create a new instance of `LiteCommands` using specific factory for your platform.

<tabs>

<!-- Bukkit -->
<tab title="Bukkit">

```Java
this.liteCommands = LiteCommandsBukkit.builder("my-plugin", this)
    .commands(
        new FlyCommand(),
        new GameModeCommand()
    )
    .build();
```
</tab>

<!-- Velocity -->
<tab title="Velocity">

```Java
 this.liteCommands = LiteVelocityFactory.builder(this.proxyServer)
     .commands(
         new SendCommand(),
         new MoveCommand()
     )
     .build();
```
</tab>

<!-- BungeeCord -->
<tab title="BungeeCord">

```Java
 this.liteCommands = LiteBungeeFactory.builder(this)
     .commands(
         new SendCommand(),
         new MoveCommand()
     )
     .build();
```
</tab>

<!-- Minestom -->
<tab title="Minestom">

```Java
Server server = MinecraftServer.getServer();
CommandManager commandManager = MinecraftServer.getCommandManager();

this.liteCommands = LiteMinestomFactory.builder(server, commandManager)
    .commands(
       new FlyCommand(),
       new GameModeCommand()
    )
    .build();
```
</tab>

<!-- JDA -->
<tab title="JDA">

```Java
JDA jda = JDABuilder.createDefault("token")
    .build();

this.liteCommands = LiteJDAFactory.builder(jda)
    .commands(
       new EmbedCommand(),
       new MessageCommand()
    )
    .build();
```
</tab>


</tabs>