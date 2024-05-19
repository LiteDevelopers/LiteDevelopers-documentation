# Builder Configuration

Create a new instance of `LiteCommands` using specific factory for your platform.

<tabs>

<!-- Bukkit -->
<tab title="Bukkit">

<warning>
<b><u>Don't</u></b> add any commands to <code>plugin.yml</code>! If you have declared commands in the <code>plugin.yml</code> then LiteCommands will <b>not able</b> to register them.
</warning>
<br/>

```Java
public class MyPlugin extends JavaPlugin {

    private LiteCommands<CommandSender> liteCommands;

    @Override
    public void onEnable() {
        this.liteCommands = LiteBukkitFactory.builder("my-plugin", this)
            .commands(
                new FlyCommand(),
                new GameModeCommand()
            )
            .build();
            
        // your code ...
    }
    
    @Override
    public void onDisable() {
        this.liteCommands.unregister();
    }
    
}
```

</tab>

<!-- Velocity -->
<tab title="Velocity">

```Java
@Plugin(id = "example-plugin", name = "ExamplePlugin", version = "1.0.0")
public class ExamplePlugin {

    private final ProxyServer proxyServer;
    private LiteCommands<CommandSource> liteCommands;

    @Inject
    public ExamplePlugin(ProxyServer proxyServer) {
        this.proxyServer = proxyServer;
    }

    @Subscribe
    public void onProxyInitialization(ProxyInitializeEvent event) {
        this.liteCommands = LiteVelocityFactory.builder(this.proxyServer)
            .commands(
                new SendCommand(),
                new MoveCommand()
            )
            .build();
            
        // your code ...
    }
    
    @Subscribe
    public void onProxyShutdown(ProxyShutdownEvent event) {
        this.liteCommands.unregister();
    }
}
```

</tab>

<!-- BungeeCord -->
<tab title="BungeeCord">

```Java
public class ExamplePlugin extends Plugin {

    private LiteCommands<CommandSender> liteCommands;

    @Override
    public void onEnable() {
        this.liteCommands = LiteBungeeFactory.builder(this)
            .commands(
                new SendCommand(),
                new MoveCommand()
            )
            .build();
            
        // your code ...
    }
}

```
</tab>

<!-- Minestom -->
<tab title="Minestom">

```Java
public class ExampleMinestom {

    public static void main(String[] args) {
        LiteMinestomFactory.builder()
            .commands(
               new FlyCommand(),
               new GameModeCommand()
            )
            .build();
            
        // your code ...
    }
}
```
</tab>

<!-- Sponge -->
<tab title="Sponge">

```Java
@Plugin("sponge-plugin")
public class SpongePlugin {

    @Inject
    public SpongePlugin(PluginContainer pluginContainer, Game game) {
        LiteSpongeFactory.builder(pluginContainer, game)
            .commands(
                new TeleportCommand(),
                new KickCommand()
            )
            .build();
            
        // your code ...
    }
}
```
</tab>

<!-- Fabric -->
<tab title="Fabric">

```Java
public class ExampleFabric implements ModInitializer {

    @Override
    public void onInitialize() {
        LiteFabricFactory.create()
            .commands(
                new BanCommand(),
                new MuteCommand()
            )
            .build();
        
        // your code ...
    }
}
```
</tab>

<!-- JDA -->
<tab title="JDA">

```Java
public class ExampleJDA {

    public static void main(String[] args) {
        JDA jda = JDABuilder.createDefault("token")
            .build();
        
        LiteJDAFactory.builder(jda)
            .commands(
               new EmbedCommand(),
               new MessageCommand()
            )
            .build();
        
        // your code ...
    }
}
```
</tab>


</tabs>