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
DisplayAreaManager is another class, which is documented below.
This method will create a box at a zero-based location in relation to the console. 0,0 will be the upper left. 
Providing a box larger than the console buffer will throw a `ArgumentOutOfRangeException`, which is something that is not internally handled by the API. Boxes larger than the buffer would calse them to overlap on a new line, which is not ideal. Please ensure your areas do not overlap the console buffer. The console buffer's size is initialized to the screen size when `Display.InitializeDisplay();` is called.

Display Areas provide some other niceties, too. For that classic DOS-style game, where the letters slowly emerge across the screen, the display area class provides a few methods to use.
`SlowType(string Text, int Delay)` and `SlowType(string Text, ConsoleColor color, int Delay, params HighlightedStrings)`

The first method takes in a string, and a delay, and will type each character out one by one, using Thread.Sleep() between them with the specified delay.  
The second method however, allows you to spice your text up with some highlighting. It functions similar to the regular `SlowType()`, with the main difference being it's paremeters. It takes a `ConsoleColor`, along with the strings 
