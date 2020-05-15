# Velvet's Text-Based Adventure game.


### Quick insight: VTAG Started as a full-fledged game...attempt. I didn't really know what I was doing, and everything got jumbled up really, really quickly. That project has been disbanded. Why did I keep the acronym despite it being an API? Dunno. I'm not creative enough to think of something better. 



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

Disable Max will disable the maximize button, preventing the window from being jumbled if it's un-maximized. DisableMin is somewhat of a less useful option here, but it has been obvserved that the ConsoleBuffer can become ruined when minimizing and reopening the window. DisableResize does as it says on the tin, however this one is likely the most useful, as having the window a fixed size ensures that text is displayed properly.



## Display Areas
    Display areas provide a couple utilities for you, the dev. Display Areas are sectioned off portions of the screen that can be independently written to, as well as cleared independently.
    By defualt, the Display Areas use double boxes that connect nicely in any intended way. 

### Code example:
```cs
            DisplayArea _DisplayArea = DisplayAreaManager.CreateDisplay(new Point(x, y), new Size(w, h));
```
