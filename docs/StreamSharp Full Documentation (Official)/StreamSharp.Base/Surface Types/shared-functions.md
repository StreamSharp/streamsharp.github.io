# Shared Functionality

StreamSharp's surface types will have shared functions. In this page, I will detail the shared functions and what they're for. Allowing the focus on the individual/combined types to be on the code used for those.

## Example code

??? example

    ```cs
    [PluginActionId("com.developer.csharptemplate.pluginactionkeyanddial")]
    public class PluginActionKeyAndDial : KeyAndEncoderBase
    {
        private class PluginSettings
        {
            public static PluginSettings CreateDefaultSettings()
            {
                PluginSettings instance = new PluginSettings();
                instance.OutputFileName = String.Empty;
                instance.InputString = String.Empty;
                return instance;
            }

            [FilenameProperty]
            [JsonProperty(PropertyName = "outputFileName")]
            public string OutputFileName { get; set; }

            [JsonProperty(PropertyName = "inputString")]
            public string InputString { get; set; }
        }

        #region Private Members

        private PluginSettings settings;

        #endregion

        // Individual type functionality will go here

        public override void Dispose()
        {
            Logger.Instance.LogMessage(TracingLevel.INFO, "Destructor called");
        }

        public override void OnTick() { }

        public override void ReceivedSettings(ReceivedSettingsPayload payload)
        {
            Tools.AutoPopulateSettings(settings, payload.Settings);
            SaveSettings();
        }

        public override void ReceivedGlobalSettings(ReceivedGlobalSettingsPayload payload) { }

        #region Private Methods

        private Task SaveSettings()
        {
            return Connection.SetSettingsAsync(JObject.FromObject(settings));
        }

        #endregion
    }
    ```

## Dissecting the code

### Plugin Action ID

```cs
[PluginActionId("com.developer.csharptemplate.pluginactionkeyanddial")]
```

This code represents the UUID of the specific action. In this sense 