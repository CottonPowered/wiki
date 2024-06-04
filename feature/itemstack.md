# ItemStack

{% hint style="info" %}
When an ItemStack gets added to an inventory or is in an inventory and you change the values of it, it automatically gets updated ingame. If you want to have a copy of the ItemStack, use the `copy` method.
{% endhint %}

### Creating ItemStacks

The `ItemStack` class allows you to create items with specific materials, amounts, and optional display names. Here's how you can create different types of `ItemStack` objects.

#### Basic ItemStack

```java
// Example: Creating a basic ItemStack with a material
ItemStack diamondStack = new ItemStack(VanillaMaterial.DIAMOND.getMaterial());
Cotton.getLogger().info("Created ItemStack: " + diamondStack);
```

#### ItemStack with Amount

```java
// Example: Creating an ItemStack with a specific amount
ItemStack ironStack = new ItemStack(VanillaMaterial.IRON_INGOT.getMaterial(), 20);
Cotton.getLogger().info("Created ItemStack with amount: " + ironStack);
```

#### ItemStack with Display Name

```java
// Example: Creating an ItemStack with a display name
ItemStack namedStack = new ItemStack(VanillaMaterial.GOLD_INGOT.getMaterial(), "Golden Ingot");
Cotton.getLogger().info("Created ItemStack with display name: " + namedStack);
```

#### ItemStack with Material, Amount, and Display Name

```java
// Example: Creating an ItemStack with material, amount, and display name
ItemStack customStack = new ItemStack(VanillaMaterial.EMERALD.getMaterial(), 10, "Shiny Emerald");
Cotton.getLogger().info("Created custom ItemStack: " + customStack);
```

### Managing ItemStack Properties

You can manage various properties of an `ItemStack`, such as its amount, display name, and manager.

#### Getting and Setting Amount

```java
// Example: Getting and setting the amount of an ItemStack
int amount = diamondStack.getAmount();
Cotton.getLogger().info("Current amount: " + amount);

diamondStack.setAmount(5);
Cotton.getLogger().info("Updated amount: " + diamondStack.getAmount());
```

#### Getting and Setting Display Name

```java
// Example: Getting and setting the display name of an ItemStack
String displayName = customStack.getDisplayName();
Cotton.getLogger().info("Current display name: " + displayName);

customStack.setDisplayName("New Shiny Emerald");
Cotton.getLogger().info("Updated display name: " + customStack.getDisplayName());
```

#### Checking Similarity Between ItemStacks

You can check if two `ItemStack` objects are similar (meaning if they are stackable).

```java
// Example: Checking if two ItemStacks are similar
boolean areSimilar = diamondStack.similar(new ItemStack(Material.DIAMOND));
Cotton.getLogger().info("Are the ItemStacks similar? " + areSimilar);
```

### Copying ItemStacks

The `copy` method creates a new `ItemStack` with the same properties as the original, but without an assigned inventory or manager.

```java
// Example: Copying an ItemStack
ItemStack copiedStack = ironStack.copy();
Cotton.getLogger().info("Copied ItemStack: " + copiedStack);
```
