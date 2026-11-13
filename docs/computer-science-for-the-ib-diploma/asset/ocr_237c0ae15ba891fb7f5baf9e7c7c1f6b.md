```
public static synchronized ConfigManager getInstance() {
    if (instance == null) {
        instance = new ConfigManager();
    }
    return instance;
}
```

```
// Load settings from file
private void loadSettings() {
    try (FileInputStream inputStream = new FileInputStream("settings.json")) {
        JSONTokener tokenizer = new JSONTokener(inputStream);
        JSONObject jsonObject = new JSONObject(tokenizer);
        settings = toMap(jsonObject);
    } catch (IOException e) {
        e.printStackTrace();
        settings = new HashMap<>(); // Fallback to an empty map
    }
}
```

```
// Helper method to convert JSONObject to Map
private Map<String, Object> toMap(JSONObject jsonObject) {
    Map<String, Object> map = new HashMap<>();
    jsonObject.keys().forEachRemaining(key -> map.put(key, jsonObject.get(key)));
    return map;
}
```

```
// Get a setting value by key
public Object getSetting(String key) {
    return settings.get(key);
}
```

```
public class Application {
    public static void main(String[] args) {
        ConfigManager configManager = ConfigManager.getInstance(); // Initialize
        // the Singleton
        String databaseUrl = (String) configManager.getSetting("databaseUrl*");
        Integer timeout = (Integer) configManager.getSetting("timeout*");
        System.out.println("Database URL: " + databaseUrl);
        System.out.println("Timeout: " + timeout);
    }
}
```