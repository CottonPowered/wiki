# Plugin Info File

{% hint style="info" %}
If you are looking for all values in the plugin info file, read [Basic Plugin](../setup/basic-plugin.md).
{% endhint %}

Getting data from the plugin info file using code is very simple. Use the `getPluginInfoFile` method within your main class. Here's an example of setting a namespace variable in the main class:

```java
public class ExamplePlugin extends CottonPlugin {
    public static String NAMESPACE;
    
    @Override
    public void onInitialize() {
        // Plugin startup logic
        NAMESPACE = getPluginInfoFile().getNamespace();
    }
}
```
