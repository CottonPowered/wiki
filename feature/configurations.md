# Configurations

Configurations aren't just useful for setting things, they are also great when saving data. That's why we have made creating and reading from configurations as simple as possible. In our example we are going to showcase the `JSONConfiguration`, but you can apply the same knowledge to upcoming other configurations.

### Initializing

To create a configuration, you first need to create a `JSONConfiguration` object. It is recommended to do this in the main file, but you can do this wherever and whenever you wish. Here's an example:

```java
// Your plugin main file
public static JSONConfiguration config;

@Override
public void onInitialize() {
    // ...
    config = new JSONConfiguration(this, "config.json");
}
```

Each configuration needs to know which plugin it belongs to, and what the name of its file is. This automatically creates all folders for it. If instead of using `config.json` you'd use `foo/config.json` it would automatically create the `foo` folder if it doesn't exist yet.

### Reloading and saving

After you have made changes to it, you can save it to disk by using the `save()` method. Caution: any changes that were not made by the code will be overwritten! If do not want this behaviour, you can use the upcoming `saveChanges()` method.

If you want to load changes that were potentially made, you can use the `reload()` method. This will reload the file from disk. Caution: this will overwrite any unsaved changes.

### Retrieving, setting and removing

You can nest keys by putting a dot. Example: `foo.bar`

**Retrieving data**: You can use the `getString(key)` method and it will return a string of the value the key is linking to. If the key doesn't exist it will return `null`. You can also use the `getStringOrDefault(key, default)` method.

**Setting data**: Use `put(key, value)` if you are trying to set data. If you only want to set something if they key doesn't exist yet (e.g. for default values), use the `putIfEmpty(key, value)` method. Don't forget to save if you want to see it on disk!

**Removing data**: The same as putting data, but instead put `null` as the value.

**Checking for existence**: Use the `has(key)` method for this.

### Misc

You can get the filename by using `getFileName()`, the absolute path with `getAbsolutePath()`, and the plugin with `getPlugin()`.
