# KeypadBase
Focused solely on using the keys found on most (if not all) Stream Deck devices.

## Example code

```cs
[PluginActionId("com.developer.csharptemplate.pluginactionkey")]
public class PluginActionKey : KeypadBase
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
    public PluginActionKey(SDConnection connection, InitialPayload payload) : base(connection, payload)
    {
        if (payload.Settings == null || payload.Settings.Count == 0)
        {
            this.settings = PluginSettings.CreateDefaultSettings();
            SaveSettings();
        }
        else
        {
            this.settings = payload.Settings.ToObject<PluginSettings>();
        }
    }

    public override void Dispose()
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, $"Destructor called");
    }

    public override void KeyPressed(KeyPayload payload)
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, "Key Pressed");
    }

    public override void KeyReleased(KeyPayload payload)
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, "Key Released");
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