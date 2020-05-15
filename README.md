# Velvet's Text-Based Adventure game.


## Quick insight: VTAG Started as a full-fledged game...attempt. I didn't really know what I was doing, and everything got jumbled up really, really quickly. That project has been disbanded. Why did I keep the acronym despite it being an API? Dunno. I'm not creative enough to think of something better. 



### VTAG Is meant to be an easy to use API, so don't expect these docs to be very long. 



In the main file, typically `Program.cs` or otherwise, in the main method, you'll want to initialize the display.

```cs
    public static void Main()
    {
      Display.InitializeDisplay(int w, int h);
    }
```
Now, this works fine, but VTAG allows for some additional customization of the window. By default, all these options are false. 
These options are `DisableClose`, `DisableMax`, `DisableMin`, and `DisableResize`. These options are only set when the `InitializeDisplay()` method is called. 

They're somewhat straight-forward, but if you don't understand, DisableClose will disable the window's close button. This is good if you need to ensure the console is not shut down before some save is created or the likes. 

