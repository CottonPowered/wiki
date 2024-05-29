# Custom Events

If you landed on this page, you probably want to create your own event, listen to it and call it. If this is the case you landed at the right spot!

In order to create a functional custom event you need to first create a class for it. In our case we are going to call it `CustomEvent`. This class must extend Cotton's `Event` class.

Each event has an identifier which is the plugin's namespace and the event name. These may not overwrite each other, or you might get into trouble when calling the event. It is recommended to have a public static variable in your event class for the identifier. Example:

```java
public static final String IDENTIFIER = ExamplePlugin.NAMESPACE + ":customEvent";
```

The class constructor should have the same event name and namespace.

```java
public CustomEvent() {
    super(ExamplePlugin.NAMESPACE, "customEvent");
}
```

Now the only thing missing is the call method which is going to be used for calling. It is highly recommended to call your calling function `call`. To execute all listeners, use the built-in `runListeners` function.

```java
// you can put arguments you wish to give your event here
public void call(String firstArgument, Player secondArgument) {
    // do whatever you want with your arguments
    this.firstArgument = firstArgument;
    this.secondArgument = secondArgument;
    
    // now run all listeners that are listening to this event
    runListeners();
}
```

Here's an example of a custom event:

```java
package com.example.plugin.events;

import net.snackbag.cottonpowered.api.event.Event;
import net.snackbag.cottonpowered.api.entity.Player;
import com.example.plugin.ExamplePlugin;

public class CustomEvent extends Event {
    // this is optional but highly recommended
    public static final String IDENTIFIER = ExamplePlugin.NAMESPACE + ":customEvent";
    
    // your arguments, used later for the getter
    private String firstArgument;
    private Player secondArgument;
    
    public CustomEvent() {
        // this namespace and name should be the same as in the
        // IDENTIFIER variable
        super(ExamplePlugin.NAMESPACE, "customEvent");
    }
    
    public void call(String firstArgument, Player secondArgument) {
        // do whatever you want with your arguments
        this.firstArgument = firstArgument;
        this.secondArgument = secondArgument;
        
        // run all listeners that are listening to this event
        runListeners();
    }
    
    public String getFirstArgument() {
        return firstArgument;
    }
    
    public Player getSecondArgument() {
        return secondArgument;
    }
}
```
