# KeyAndEncoderBase

This combines the keys and the dials into a single format (for a single action).

## Example code

```cs
[PluginActionId("com.developer.csharptemplate.pluginactionkeyanddial")]
public class PluginActionBoth : KeyAndEncoderBase
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
    public PluginActionBoth(SDConnection connection, InitialPayload payload) : base(connection, payload)
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

    private void UpdateTitle()
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, "UpdateTitle called");
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

    public override void DialRotate(DialRotatePayload payload)
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, "Dial Rotate");
    }

    public override void DialDown(DialPayload payload)
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, "Dial Down");
    }

    public override void DialUp(DialPayload payload)
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, "Dial Up");
    }

    public override void TouchPress(TouchpadPressPayload payload)
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, "Touch Press");
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

## Misc information

??? success "Granular control OK"
    There are no merged functions in this device type. It is therefore possible to maintain fully granular control over functionality for functions between keys and dials.

??? info "Included!"
    Until further notice, `KeyAndEncoderBase` is included in StreamSharp.Base - however this is subject to change.