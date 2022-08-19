# ConfigFile - YAML Helper class for Bukkit/Spigot/Paper/...

This wrapper class allows easy access to YAML files from your Bukkit/Spigot/Paper/... plugin.\

Every method is well-documented so you should be able to get started quickly

## Setup
The only thing you need to get started is calling `setPlugin()` in your `onEnable` method.
```java
ConfigFile.setPlugin(this);
```
The ConfigFile needs the plugin to know where it can load resources from.

## Config Types
ConfigFiles can have 3 types, `LOAD_AND_SAVE`, `LOAD_ONLY` and `SAVE_ONLY`. \
**"Loading"** means, that it is looking for default values in your plugin resource folder. \
**"Saving"** means, that you can call `save()` to write all values to a file in the plugin data folder.

## Examples
```java
// Loads a config.yml datei from the folder "folder"
// This constructor sets the type to ConfigFile.Type.LOAD_AND_SAVE
ConfigFile config = new ConfigFile("folder/config");

// Using the config works as always, since its just a YamlConfiguration underneath.
config.set("Test", 4);
String test = config.getString("SomeDefaultValue");

// Save your changes to the data folder (the resource in you plugin's jar is not modified)
config.save();

// Delete the file from the plugin data folder
config.delete();

// If you dont have default values, you can change the type to SAVE_ONLY
ConfigFile data = new ConfigFile("data", ConfigFile.Type.SAVE_ONLY);
data.set("data1", "test");
data.save();

// if you only want to load the defaults from the resource folder
// and never save changes to the data folder, use LOAD_ONLY
ConfigFile defaults = new ConfigFile("defaults", ConfigFile.Type.LOAD_ONLY);
String value = defaults.getString("SomeValue");
```

## Bugs & Improvements
If you found a bug, please open an Issue, explain it in detail and ideally add source code or error messages.

If you think this class can be improved, send me an email at nlfmt@gmx.de, or submit a pull request.

## License
You're free to use the code in any way you want, altough I'd appreciate it if you mentioned me :)