---
uid: Cube_Feature_Release_10.4.8
---

# DataMiner Cube Feature Release 10.4.8 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
> For release notes for this release that are not related to DataMiner Cube, see [General Feature Release 10.4.8](xref:General_Feature_Release_10.4.8).

## Highlights

- [Enabling or disabling SLAnalytics features either system-wide or for specific parameters [ID_39692]](#enabling-or-disabling-slanalytics-features-either-system-wide-or-for-specific-parameters-id_39692)

## New features

#### DataMiner Cube will now reflect all changes to user-defined APIs in real time [ID_39238]

<!-- MR 10.3.0 [CU17] / 10.4.0 [CU5] - FR 10.4.8 -->

DataMiner Cube now subscribes to the *ApiTokenChangedEventMessage* and the *ApiDefinitionChangedEventMessage*, which were introduced in DataMiner version 10.5.0/10.4.6. As a result, the *User-Defined APIs* section of *System Center* and the *Automation* module will now reflect all changes to user-defined APIs in real time.

#### Enabling or disabling SLAnalytics features either system-wide or for specific parameters [ID_39692]

<!-- MR 10.3.0 [CU17] / 10.4.0 [CU5] - FR 10.4.8 -->

The following SLAnalytics features can now be enabled either system-wide or for specific parameters.

- Trend icons
- Behavioral anomaly detection
- Proactive cap detection

To configure for which parameters those features are enabled, do the following:

1. In *System Center > System settings > Analytics config*, configure the *Enabled* and *Run on trended parameters by default* settings for each of the above-mentioned features.

   **Trend icons**

   | Enabled | Run on trended parameters by default | Result |
   |---|---|---|
   | False | -     | Trend icons are not displayed for any parameters. |
   | True  | True  | Trend icons are generated by default for all trended numeric parameters.<br>In the trend template, this setting can be overridden for specific parameters. See below. |
   | True  | False | Trend icons are disabled system-wide, except for trended parameters of which the *Trend icons* setting has explicitly been enabled in the trend template. |

   **Behavioral anomaly detection**

   | Enabled | Run on trended parameters by default | Result |
   |---|---|---|
   | False | -     | Behavioral anomaly detection is disabled. |
   | True  | True  | Behavioral anomaly detection is enabled by default for trended numeric parameters that are not part of partial tables.<br>In the trend template, this setting can be overridden for specific parameters. See below. |
   | True  | False | Behavioral anomaly detection is disabled system-wide, except for trended parameters of which the *Anomalies* setting has explicitly been enabled in the trend template. |

   **Proactive cap detection**

   | Enabled | Run on trended parameters by default | Result |
   |---|---|---|
   | False | -     | Proactive cap detection is disabled. |
   | True  | True  | Proactive cap detection is enabled by default for trended numeric parameters that are not part of partial tables and have explicitly specified value bounds.<br>In the trend template, this setting can be overridden for specific parameters. See below. |
   | True  | False | Proactive cap detection is disabled system-wide, except for trended parameters of which the *Proactive alarms* setting has explicitly been enabled in the trend template. |

1. In a trend template, the *Trend icons*, *Anomalies* and *Proactive alarms* settings of all parameters are by default set to "System default". This means that the settings configured in *System Center > System settings > Analytics config* will apply.

   However, if you want to override the settings configured in *System Center > System settings > Analytics config* for a specific trended parameter, set its *Trend icons*, *Anomalies* and/or *Proactive alarms* settings to either "On" or "Off".

   > [!NOTE]
   > In the trend template editor, the *Trend icons*, *Anomalies* and/or *Proactive alarms* settings are only displayed when you click the cogwheel button and select the *Allow Augmented Operations configuration* option.

## Changes

### Enhancements

*No enhancements have been added yet.*

### Fixes

#### Incorrect `CubeHost: Unable to load assembly` errors in Cube log files on client computers [ID_39767]

<!-- MR 10.3.0 [CU17] / 10.4.0 [CU5] - FR 10.4.8 -->

On client computers, up to now, incorrect `CubeHost: Unable to load assembly` errors mentioning the following DLL files would be added to the log files in the `%LocalAppData%/Skyline/DataMiner/DataMinerCube/Logs` folder:

- Google.Protobuf
- System.Buffers
- System.Diagnostics.DiagnosticSource
- System.Memory
- System.Numerics.Vectors
- System.Runtime.CompilerServices.Unsafe

#### Alarm Console: Problem when sorting alarms by the PollingIP column [ID_39804]

<!-- MR 10.3.0 [CU17] / 10.4.0 [CU5] - FR 10.4.8 -->

When, in the Alarm Console, you tried to sort alarms by the *PollingIP* column, Cube could throw an exception or even stop working when that column contained IP addresses starting with "http://" or "https://".

#### URLs pointing to the DataMiner Agent to which Cube was connected via gRPC would contain an incorrect hostname [ID_39851]

<!-- MR 10.3.0 [CU17] / 10.4.0 [CU5] - FR 10.4.8 -->

When Cube was connected to a DataMiner Agent via a gRPC connection, in some cases, the URLs of e.g. log files would contain an incorrect hostname, making it impossible to retrieve those files from the DataMiner Agent.
