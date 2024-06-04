---
description: Inventory interface usage examples
---

# Inventories

### Adding Items

The `addItem` method allows you to add one or more items to the inventory. It returns a map of slots and items that couldn't be added, indicating which items failed to be placed due to inventory constraints.

```java
// Example: Adding items to the inventory
ItemStack item1 = new ItemStack(VanillaMaterial.DIAMOND.getMaterial(), 10);
ItemStack item2 = new ItemStack(VanillaMaterial.IRON_INGOT.getMaterial(), 20);
HashMap<Integer, ItemStack> failedItems = inventory.addItem(item1, item2);

if (!failedItems.isEmpty()) {
    Cotton.getLogger().info("Some items couldn't be added to the inventory:");
    failedItems.forEach((slot, item) -> {
        Cotton.getLogger().info("Slot: " + slot + ", Item: " + item);
    });
}
```

### Checking for Items

You can check if the inventory contains a specific item or material using the `contains` methods.

```java
// Example: Checking if the inventory contains a material with a minimum amount
boolean containsMaterial = inventory.contains(VanillaMaterial.IRON_INGOT.getMaterial(), 10);
Cotton.getLogger().info("Inventory contains at least 10 iron ingots: " + containsMaterial);
```

### Retrieving Items

The `first` methods allow you to find the first occurrence of an item or material in the inventory. You can also find the first empty slot using `firstEmpty`.

```java
// Example: Finding the first occurrence of a material
Integer firstMaterialSlot = inventory.first(VanillaMaterial.GOLD_INGOT.getMaterial());
Cotton.getLogger().info("First occurrence of the material is at slot: " + firstMaterialSlot);

// Example: Finding the first empty slot
Integer firstEmptySlot = inventory.firstEmpty();
Cotton.getLogger().info("First empty slot is at index: " + firstEmptySlot);
```

### Removing Items

The `remove` methods allow you to remove specific items or materials from the inventory.

```java
// Example: Removing all items of specific materials from the inventory
inventory.remove(VanillaMaterial.GOLD_INGOT.getMaterial(), VanillaMaterial.EMERALD.getMaterial());
```

### Clearing Inventory

You can clear the entire inventory or specific slots using the `clear` methods.

```java
// Example: Clearing the entire inventory
inventory.clear();

// Example: Clearing a specific slot in the inventory
int slotToClear = 5;
inventory.clear(slotToClear);
```

### Setting Contents

The `setContents` method allows you to set the inventory's contents to a specific array of items.

```java
// Example: Setting the inventory's contents
ItemStack[] newContents = new ItemStack[inventory.getSize()];
newContents[0] = new ItemStack(VanillaMaterial.DIAMOND.getMaterial(), 64);
newContents[1] = new ItemStack(VanillaMaterial.IRON_INGOT.getMaterial(), 64);
inventory.setContents(newContents);
```

### Querying Inventory Information

You can get various information about the inventory, such as its size, type, contents, and more.

```java
// Example: Getting the inventory's size
int inventorySize = inventory.getSize();
Cotton.getLogger().info("Inventory size: " + inventorySize);

// Example: Getting the inventory's maximum stack size
int maxStackSize = inventory.getMaxStackSize();
Cotton.getLogger().info("Maximum stack size: " + maxStackSize);

// Example: Checking if the inventory is empty
boolean isEmpty = inventory.isEmpty();
Cotton.getLogger().info("Inventory is empty: " + isEmpty);

// Example: Getting the inventory's contents
ItemStack[] contents = inventory.getContents();
Cotton.getLogger().info("Inventory contents: " + Arrays.toString(contents));

// Example: Getting the inventory's type
Identifier inventoryType = inventory.getType();
Cotton.getLogger().info("Inventory type: " + inventoryType);

// Example: Getting the inventory's holder
InventoryHolder holder = inventory.getHolder();
Cotton.getLogger().info("Inventory holder: " + holder);
```

By utilizing these methods, you can effectively manage and manipulate the contents of an inventory in various scenarios, ensuring smooth and efficient item handling within your application.
