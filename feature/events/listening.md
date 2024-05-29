---
description: Describes a way to execute functions when an event is called
---

# Listening

There are just two steps required when creating the listener:

* Making the listener class
* Registering the listener

Listeners listen on events. In our example we will use the [PlayerJoinEvent](all-events/playerjoinevent.md). If you are looking for a list of events you can check that our [here](all-events/). If you feel like an event is missing, just tell us and we'll try our best to add it! Here's an example of a Listener:

```java
package com.example.plugin.listeners;

import net.snackbag.cottonpowered.api.event.Event;
import net.snackbag.cottonpowered.api.event.Listener;
import net.snackbag.cottonpowered.api.event.PlayerJoinEvent;
import net.snackbag.cottonpowered.api.plugin.CottonPlugin;

// Create the Listener which should extend Cotton's Listener
public class JoinListener extends Listener {
    public JoinListener(CottonPlugin plugin) {
        // We specify which plugin uses this Listener and which
        // event we're listening to
        super(plugin, new PlayerJoinEvent());
    }
    
    @Override
    // This function will be executed when the event is called
    public void onEvent(Event e) {
        // Because we get back an Event class and not a
        // PlayerJoinEvent, we will have to cast it.
        PlayerJoinEvent event = (PlayerJoinEvent) e;
        
        // We can use the PlayerJoinEvent's getPlayer() method
        // to get which player just joined
        event.getPlayer().sendMessage("You joined");
    }
}
```

Now that's fun and all, but the Listener will not get executed yet. We will have to register it in our initialization method.

```java
// ExamplePlugin.java
public void onInitialize() {
    // ...
    // We register the Listener through the EventManager.
    // Notice: this may change in the future!
    EventManager.registerListener(new JoinListener(this));
}
```
