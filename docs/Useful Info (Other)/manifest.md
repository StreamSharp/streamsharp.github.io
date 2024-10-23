# Manifest Support

!!! info
    Please be sure to check the [Elgato SDK Manifest Information](https://docs.elgato.com/streamdeck/sdk/references/manifest) for all the latest documentation. We are not currently providing documentation on this page (but this will change in the future.)
<!--
Information on this page may be out of date.

## Understanding the Manifest

The manifest is the file that tells the Stream Deck software where your code is found, along with which actions relate to which buttons, etc. Think of it as the translation layer between the software and your plugin.

### Important Notes
-->

??? failure annotate "Cannot use the schema in Visual Studio"
    When using the schema in Visual Studio (this does not apply to Visual Studio Code), it is not able to use the schema (it states that the schema is incorrect). This stops the IDE being able to validate your JSON schema to ensure you have included everything you need. (1) It is recommended that you use a separate editor such as Visual Studio Code for writing your manifest. As Visual Studio is only available for Windows, this issue does not affect Mac or Linux developers.

1. We may attempt to bring out a variant of the schema specifically for use on Visual Studio.

<!--
## See the Code

!!! Example "Example Manifests"
    === "Basic Manifest"

        ```json linenums="1" title="manifest.json"
        {
            "$schema": "https://schemas.elgato.com/streamdeck/plugins/manifest.json",
            "Actions": [
                {
                    "Icon": "Images/icon",
                    "Name": "Key Action",
                    "States": [
                        {
                            "Image": "Images/pluginAction",
                            "TitleAlignment": "middle",
                            "FontSize": "12"
                        }
                    ],
                    "SupportedInMultiActions": false,
                    "DisableCaching": true,
                    "UserTitleEnabled": true,
                    "Tooltip": "I am an action that only runs on keys",
                    "UUID": "com.developer.csharptemplate.pluginactionkey",
                    "PropertyInspectorPath": "PropertyInspector/PluginActionPI.html"
                }
            ],
            "Author": "Example Developer",
            "Name": "StreamSharp Documentation Manifest",
            "Description": "This plugin showcases the manifest functionality of StreamSharp, in a neat example",
            "Icon": "Images/pluginIcon",
            "URL": "https://github.com/streamsharp",
            "UUID": "com.developer.csharptemplate",
            "Version": "1.0.0,0",
            "CodePath": "com.developer.csharptemplate.exe",
            "CodePathWin": "com.developer.csharptemplate.exe",
            "CodePathMac": "com.developer.csharptemplate",
            "Category": "Custom",
            "CategoryIcon": "Images/categoryIcon",
            "OS": [
                {
                    "Platform": "macos",
                    "MinimumVersion": "10.11"
                },
                {
                    "Platform": "windows",
                    "MinimumVersion": "10"
                }
            ],
            "SDKVersion": 2,
            "Software": {
                "MinimumVersion": "6.4"
            }
        }
        ```

    === "Encoder Manifest"

        ```json linenums="1" hl_lines="7-17" title="manifest.json"
        {
            "$schema": "https://schemas.elgato.com/streamdeck/plugins/manifest.json",
            "Actions": [
                {
                    "Icon": "Images/icon",
                    "Name": "Dial Action",
                    "Controllers": ["Keypad", "Encoder"],
                    "Encoder": {
                        "background": "Images/touchscreen-background",
                        "layout": "$B1",
                        "TriggerDescription": {
                            "Push": "What happens when I click the dial?",
                            "Rotate": "What happens when I rotate the dial?",
                            "Touch": "What happens when I quickly tap the touch screen?",
                            "LongTouch": "What happens when I hold down on the touch screen?"
                        }
                    }
                },
                    "States": [
                        {
                            "Image": "Images/pluginAction",
                            "TitleAlignment": "middle",
                            "FontSize": "12"
                        }
                    ],
                    "SupportedInMultiActions": false,
                    "DisableCaching": true,
                    "UserTitleEnabled": true,
                    "Tooltip": "I am an action that only runs on keys",
                    "UUID": "com.developer.csharptemplate.pluginactionkey",
                    "PropertyInspectorPath": "PropertyInspector/PluginActionPI.html"
                }
            ],
            "Author": "Example Developer",
            "Name": "StreamSharp Documentation Manifest",
            "Description": "This plugin showcases the manifest functionality of StreamSharp, in a neat example",
            "Icon": "Images/pluginIcon",
            "URL": "https://github.com/streamsharp",
            "UUID": "com.developer.csharptemplate",
            "Version": "1.0.0,0",
            "CodePath": "com.developer.csharptemplate.exe",
            "CodePathWin": "com.developer.csharptemplate.exe",
            "CodePathMac": "com.developer.csharptemplate",
            "Category": "Custom",
            "CategoryIcon": "Images/categoryIcon",
            "OS": [
                {
                    "Platform": "macos",
                    "MinimumVersion": "10.11"
                },
                {
                    "Platform": "windows",
                    "MinimumVersion": "10"
                }
            ],
            "SDKVersion": 2,
            "Software": {
                "MinimumVersion": "6.4"
            }
        }
        ```

    === "Manifest with Profiles"

        ```json linenums="1" hl_lines="44-55" title="manifest.json"
        {
            "$schema": "https://schemas.elgato.com/streamdeck/plugins/manifest.json",
            "Actions": [
                {
                    "Icon": "Images/icon",
                    "Name": "Key Action",
                    "States": [
                        {
                            "Image": "Images/pluginAction",
                            "TitleAlignment": "middle",
                            "FontSize": "12"
                        }
                    ],
                    "SupportedInMultiActions": false,
                    "DisableCaching": true,
                    "UserTitleEnabled": true,
                    "Tooltip": "I am an action that only runs on keys",
                    "UUID": "com.developer.csharptemplate.pluginactionkey",
                    "PropertyInspectorPath": "PropertyInspector/PluginActionPI.html"
                }
            ],
            "Author": "Example Developer",
            "Name": "StreamSharp Documentation Manifest",
            "Description": "This plugin showcases the manifest functionality of StreamSharp, in a neat example",
            "Icon": "Images/pluginIcon",
            "URL": "https://github.com/streamsharp",
            "UUID": "com.developer.csharptemplate",
            "Version": "1.0.0,0",
            "CodePath": "com.developer.csharptemplate.exe",
            "CodePathWin": "com.developer.csharptemplate.exe",
            "CodePathMac": "com.developer.csharptemplate",
            "Category": "Custom",
            "CategoryIcon": "Images/categoryIcon",
            "OS": [
                {
                    "Platform": "macos",
                    "MinimumVersion": "10.11"
                },
                {
                    "Platform": "windows",
                    "MinimumVersion": "10"
                }
            ],
            "Profiles": [
                {
                    "DeviceType": 2,
                    "DontAutoSwitchWhenInstalled": true,
                    "Name": "Custom Profile (SD XL)"
                },
                {
                    "DeviceType": 7,
                    "DontAutoSwitchWhenInstalled": true,
                    "Name": "Custom Profile (SD +)"
                }
            ],
            "SDKVersion": 2,
            "Software": {
                "MinimumVersion": "6.4"
            }
        }
        ```

    === "App Monitoring Manifest"

        ```json linenums="1" hl_lines="48-51" title="manifest.json"
        {
            "$schema": "https://schemas.elgato.com/streamdeck/plugins/manifest.json",
            "Actions": [
                {
                    "Icon": "Images/icon",
                    "Name": "Key Action",
                    "States": [
                        {
                            "Image": "Images/pluginAction",
                            "TitleAlignment": "middle",
                            "FontSize": "12"
                        }
                    ],
                    "SupportedInMultiActions": false,
                    "DisableCaching": true,
                    "UserTitleEnabled": true,
                    "Tooltip": "I am an action that only runs on keys",
                    "UUID": "com.developer.csharptemplate.pluginactionkey",
                    "PropertyInspectorPath": "PropertyInspector/PluginActionPI.html"
                }
            ],
            "Author": "Example Developer",
            "Name": "StreamSharp Documentation Manifest",
            "Description": "This plugin showcases the manifest functionality of StreamSharp, in a neat example",
            "Icon": "Images/pluginIcon",
            "URL": "https://github.com/streamsharp",
            "UUID": "com.developer.csharptemplate",
            "Version": "1.0.0,0",
            "CodePath": "com.developer.csharptemplate.exe",
            "CodePathWin": "com.developer.csharptemplate.exe",
            "CodePathMac": "com.developer.csharptemplate",
            "Category": "Custom",
            "CategoryIcon": "Images/categoryIcon",
            "OS": [
                {
                    "Platform": "macos",
                    "MinimumVersion": "10.11"
                },
                {
                    "Platform": "windows",
                    "MinimumVersion": "10"
                }
            ],
            "SDKVersion": 2,
            "Software": {
                "MinimumVersion": "6.4"
            },
            "ApplicationsToMonitor": {
                "windows": ["streamsharp.exe"],
                "mac": ["com.developer.streamsharp"]
            }
        }
        ```

Next, we're going to take a look at all the code and what it means.

### Explaining the Code

=== "Basic Manifest"

=== "Encoder Manifest"

=== "Manifest with Profiles"

=== "App Monitoring Manifest"
-->