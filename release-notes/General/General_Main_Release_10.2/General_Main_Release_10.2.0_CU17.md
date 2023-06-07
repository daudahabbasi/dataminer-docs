---
uid: General_Main_Release_10.2.0_CU17
---

# General Main Release 10.2.0 CU17 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
> For information on how to upgrade DataMiner, see [Upgrading a DataMiner Agent](xref:Upgrading_a_DataMiner_Agent).

### Enhancements

#### Cassandra: gc_grace_seconds will now be set to 1 day by default and to 4 hours for records with TTL set [ID_34763]

<!-- MR 10.2.0 [CU17]/10.3.0 [CU4] - FR 10.3.7 -->

In Cassandra databases, the table property `gc_grace_seconds` will now be set to 1 day by default.

For tables containing data with TTL set, this property will be set to 4 hours.

#### Dashboards app & Low-Code Apps: No visual replacement will be displayed anymore when a State component feeds empty query rows [ID_36460]

<!-- MR 10.2.0 [CU17]/10.3.0 [CU4] - FR 10.3.7 -->

Up to now, when a *State* component fed empty query rows, a visual replacement would be displayed. From now on, this will no longer be the case.

#### DataMiner Agents joining a cluster will now synchronize their ProtocolScripts\DllImport folder [ID_36494]

<!-- MR 10.2.0 [CU17]/10.3.0 [CU5] - FR 10.3.8 -->

When a DataMiner Agent joins a cluster, it will now synchronize its `ProtocolScripts\DllImport` folder.

Also, when processing a protocol, a DataMiner Agent will now synchronize

- the files in the `ProtocolScripts/DllImport` folder, and
- the files in the folders mentioned in the *QAction@dllImport* attribute.

#### Stream Viewer will now display parameter IDs in decimal format instead of octal format [ID_36525]

<!-- MR 10.2.0 [CU17]/10.3.0 [CU5] - FR 10.3.8 -->

Stream Viewer will display an error message when an SNMP poll group contained either an invalid parameter or a parameter that did not have its SNMP setting enabled.

Up to now, that error message would contain the ID of the parameter in octal format. From now on, it will contain the ID of the parameter in decimal format instead.

#### Factory reset tool will no longer try to delete non-existing folders [ID_36550]

<!-- MR 10.2.0 [CU17]/10.3.0 [CU5] - FR 10.3.8 -->

Up to now, the factory reset tool *SLReset.exe* would log an exception each time it had tried to delete a non-existing folder. From now on, when it has to delete a folder, it will first check whether that folder exists. If not, it will not try to delete it.

### Fixes

#### DataMiner Cube - Visual Overview: Problem with element or view scope of Children shapes [ID_36354]

<!-- MR 10.2.0 [CU17]/10.3.0 [CU5] - FR 10.3.8 -->

In some cases, when a placeholder was used in the *Element* or *View* shape data field of a *Children* shape, the scope would not be updated when changes were made to the placeholder.

From now on, the scope will be updated correctly whenever changes are made to the placeholder in the *Element* or *View* shape data field.

#### DataMiner Cube - System Center: Problem with 'Show agent alarms' link [ID_36463]

<!-- MR 10.2.0 [CU17]/10.3.0 [CU5] - FR 10.3.8 -->

When you selected an agent in the *Agents* section of *System Center*, in some cases, the alarm numbers shown in the *Show agent alarms* link would not be correct.

Also, when you clicked that *Show agent alarms* link, the alarm tab listing the alarms of the selected agent would incorrectly be empty.

#### Low-Code Apps: Application would be updated each time you hit a key after changing a page name [ID_36479]

<!-- MR 10.2.0 [CU17]/10.3.0 [CU5] - FR 10.3.8 -->

When you changed the name of a low-code app page, the application would incorrectly be updated each time you hit a key. From now on, the application will be updated 250 ms after the last keystroke.

#### SLAnalytics: Incorrect trend predictions in case of incorrect data ranges set in the protocol [ID_36521]

<!-- MR 10.2.0 [CU17]/10.3.0 [CU5] - FR 10.3.8 -->

If, in the protocol, a data range is specified for a parameters for which trend data prediction is required, the trend prediction algorithm will cap the prediction values to the data range. For example, if a parameter has a rangeLow value equal to 0 and a rangeHigh value equal to 100, the prediction will not contain values lower than 0 or higher than 100.

From now on, if the trend data contains values outside of the specified data range, the trend prediction algorithm will no longer consider the data range values to be valid or reliable, and will not limit the prediction to this range.