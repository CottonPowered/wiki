# Events

### Overview

Events are a necessity in all plugins. They trigger when a specific action occurs, which can be very handy. For example: you want a message to appear when a player joins the server. This is what is called a "Listener", which you can learn more about [here](listening.md).

Sometimes there's the case that you want to create your own events, which is also possible! You can use the Event API to achieve this. Read more about it [here](custom-events.md)

### Event concept

**Events** are occurrences within the game that trigger certain actions. These events can be anything from a player joining the server, to a block being broken, to an entity dying. Each event is an object that carries information about the occurrence.

**Listeners** are classes or methods designed to "listen" for specific events and define what actions should be taken when those events occur.

* **Implementing Listeners**: To create a listener, you need to extend the `Listener` class and override the `onEvent` method to handle the specified event.
* **Registering Listeners**: Listener classes must be registered with the `EventManager` in order to start receiving events.

#### How they work together

1. **Event Occurrence**: An event occurs within the game, such as a player joining the server.
2. **Event Dispatching**: The `EventManager` will get the correct event object and execute its `call` method.
3. **Event Handling**: Each listener that listens to the affected event processes the event by running the `onEvent` method.

#### Key points

* **Events**: Represent actions or ocurrences in the game (e.g., [PlayerJoinEvent](all-events/playerjoinevent.md))
* **Listeners**: Define what happens in response to its assigned event (e.g., send a welcome message when a player joins)

Understanding this distinction is crucial for developing effective and responsive plugins using Cotton.
