# EncoderBase

Focused solely on using the dials (and corresponding touch screen above each dial), found on the Stream Deck Plus.

## Example code

```cs
[PluginActionId("com.developer.csharptemplate.pluginactiondial")]
public class PluginActionDial : EncoderBase
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
    public PluginActionDial(SDConnection connection, InitialPayload payload) : base(connection, payload)
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, "Constructor called");
    }

    private void UpdateTitle()
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, "UpdateTitle called");
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

    public override void ReceivedSettings(ReceivedSettingsPayload payload)
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, "Received Settings");
    }

    public override void ReceivedGlobalSettings(ReceivedGlobalSettingsPayload payload)
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, "Received Global Settings");
    }

    public override void OnTick() { }

    public override void Dispose()
    {
        Logger.Instance.LogMessage(TracingLevel.INFO, "Destructor called");
    }

    // Additional event handling methods can be added as needed

    // Implement any other necessary methods or properties

    // Define the settings model class if not already defined
    public class MySettingsModel
    {
        public string ImagePath { get; set; }
        public string TargetDevice { get; set; }
        // Add any other settings properties here
    }
}
```