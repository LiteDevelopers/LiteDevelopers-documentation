# Custom Types

You can create your own argument types! It's very simple and easy.

To create a custom type, you need to create a class that extends the `ArgumentResolver`!

```java
public class PlotResolver extends ArgumentResolver<SENDER, Plot> {

    private final PlotManager plotManager;
    
    public PlotResolver(PlotManager plotManager) {
        this.plotManager = plotManager;
    }

    @Override
    protected ParseResult<Plot> parse(Invocation<SENDER> invocation, Argument<String> context, String argument) {
        Plot plot = this.plotManager.getPlot(argument);
        
        if (plot == null) {
            return ParseResult.failure("Plot not found!");
        }
        
        return ParseResult.success(plot);
    }

    @Override
    public SuggestionResult suggest(Invocation<SENDER> invocation, Argument<String> argument, SuggestionContext context) {
        return this.plotManager.getPlots().stream()
            .map(plot -> plot.getName())
            .collect(SuggestionResult.collector());
    }

}
```