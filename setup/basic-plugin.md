---
description: This includes everything to get your first plugin up and running
---

# Basic Plugin

Some things are needed before your plugin can actually start:

* Create a `cotton-plugin.toml` file
* Write an initialization class
* Building the plugin JAR

After you created your Java project, open the `resources` folder and create a new file named `cotton-plugin.toml`

In this file you will need to specify all needed things for your plugin to start:

* Name<mark style="color:red;">\*</mark>
* Authors<mark style="color:red;">\*</mark>
* Version<mark style="color:red;">\*</mark>
* Namespace<mark style="color:red;">\*</mark>
* Target Minecraft Version<mark style="color:red;">\*</mark>
* API Version<mark style="color:red;">\*</mark>
* Main Class Path<mark style="color:red;">\*</mark>

Things tagged with <mark style="color:red;">\*</mark> are required

Here's a working example of a `cotton-plugin.toml` file

```toml
# In the information category, you can specify all "cosmetic"
# information about your plugin.
[information]
# (required) This is the name of how the plugin will show up.
name = "Example Plugin"
# (required) This is a list of strings of all people who have worked 
# on this plugin.
authors = ["JX_Snack"]
# (required) The plugin's version
version = "1.0"

# In the execution category everything shown here is required. You
# will configure everything that your plugin needs to start up.
[execution]
# The plugin's namespace. This may only contain lowercase letters,
# underscores and numbers. If there are multiple plugins with the
# same namespace the server will crash. Make sure to pick a unique name!
namespace = "example"
# The targeted Minecraft version for your plugin. If the server is running
# a lower version your plugin will send an error to the console.
minecraft-version = "1.20.1"
# The API version you are depending on. If the server is running an older version
# than the specified API version your plugin will send an error to the console.
api-version = "0.1.0"
# The path to your main class
main = "com.example.plugin.ExamplePlugin"
```

### Initialization class

This is where the specified path in your `cotton-plugin.toml` file leads to. Here's a working example:

```java
package com.example.plugin;

import net.snackbag.cottonpowered.api.CottonPlugin;

public class ExamplePlugin extends CottonPlugin {
    @Override
    public void onInitialize() {
        // Plugin startup logic
        
    }
    
    @Override
    public void onTerminate() {
        // Plugin shutdown logic

    }
}
```

The `onInitialize` method will run when the plugin loads up (e.g. when the server starts) and `onTerminate` when the plugin gets terminated (e.g. when the server stops). You can access the plugin info file through code by using `getPluginInfoFile` in your main class.

It is recommended to set a namespace variable which is the same as in your plugin info file. Learn more [here](../feature/plugin-info-file.md)
