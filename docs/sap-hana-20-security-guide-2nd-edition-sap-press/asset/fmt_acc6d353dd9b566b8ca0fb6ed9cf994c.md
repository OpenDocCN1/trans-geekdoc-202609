
## Figure 14.14 Create Transport Route Window

Enter the Name of the transport route and choose the Source System. The Source System dropdown list will only contain registered systems. The target system value is fixed and can’t be changed. In the Content section, select the Delivery Units radio button and then select one or more source system delivery units to transport. Click the Create button at the bottom right.

With the transport route defined, you can now start the transport process, as shown in [Figure 14.15](#14_003.html#f14.15). To transport a delivery unit, select the transport route in the list 1. Once selected, start the transport process by clicking the Start Transport button 2.

[![Selecting Transport Package and Starting Transport Process](bilderklein/klein14_015.png)](img-f14.15.html)

## Figure 14.15 Selecting Transport Package and Starting Transport Process

Once the Start Transport button is clicked, the Start the Transport window will appear to confirm the start action. Click the OK button to start the transport process. The window will disappear, and you’ll return to the transport route-listing page.

To view the status of the transport request, click the submenu item labeled Logs. You’ll see the current and historical status of transports initiated within the system. If any issues have arisen, the Status column will show a red triangle. If the transport is complete, the Status column will show a green square.

## 14.3.2 Exporting a Delivery Unit to a File

In addition to using SAP HANA application lifecycle management to export a delivery unit in [Section 14.2.3](#14_002.html#h14.2.3), you can also use SAP HANA Studio. This functionality is not available in the SAP HANA cockpit, so we’ll explain how SAP HANA Studio can be used in this chapter. SAP HANA Studio provides an interface to export a delivery unit to a compressed file. This compressed file can be imported back into the SAP HANA repository later. Developers often use this export process to serve as a backup of their code. However, this functionality also can be used for lifecycle management, even though SAP HANA application lifecycle management is the preferred tool to manage transports between SAP HANA instances.

To start the process, switch to the administration console perspective within SAP HANA Studio. From the menu bar, choose File • Export. The Export window will appear. Within the Select an Export Wizard section, expand SAP HANA Content, and then choose Delivery Unit. Click Next to continue. The Select Source System window will appear. In the list of systems, select the system that will serve as the source of the delivery unit. Click Next to continue. The Export Through Delivery Unit window will appear with the subtitle Select Delivery Unit. This window is used to specify the delivery unit export options, as shown in [Figure 14.16](#14_003.html#f14.16).

[![Export Options in SAP HANA Studio](bilderklein/klein14_016.png)](img-f14.16.html)

## Figure 14.16 Export Options in SAP HANA Studio

In this window, use the Delivery Unit dropdown list to choose the delivery unit for export. The export tool will include all development artifacts associated with the packages listed in the section labeled List of Packages. However, you also have the option of exporting development artifacts based on their activation date. Use the Filter by time checkbox to enable the time-based filters. With the Filter by time checkbox selected, choose a Time Internal using the provided dropdown list. The dropdown list provides the following intervals: Last Week, Last Month, and Time Range. Choose Time Range to specify custom From and To dates.

When exporting the delivery unit file, you can choose to place the file on the server or download the file to SAP HANA Studio’s client system. Typically, you’ll export to the client system because most developers don’t have access to the SAP HANA server’s file system. Click Export to Client in the Export Location section. In the Location field, specify the local file path where the delivery unit file will be downloaded. The File Name field will be prepopulated with a file name based on the current time, system, and delivery unit name. You can change the name, but be sure to retain the file extension .tgz. Click Next to continue. A Summary page will appear with an overview of the export settings. Click Finish to start the export process. Once completed, a file will appear in the configured path. Once created, the file can be used as a backup or as an import source.

## 14.3.3 Importing a Delivery Unit from a File

In addition to using SAP HANA application lifecycle management to import a delivery unit in [Section 14.2.3](#14_002.html#h14.2.3), you can also use SAP HANA Studio. This functionality is not available in the SAP HANA cockpit, so we’ll explain how SAP HANA Studio can be used in this chapter. SAP HANA Studio provides an interface to import a delivery unit file into a package repository. The tool will import all development artifacts found in the file and activate them within the repository. The file can be imported into an SAP HANA instance, assuming that the export source and import source share a similar SAP HANA software version.

To start the import process, switch to the administration console perspective in SAP HANA Studio. From the menu bar, choose File • Import. The Import window will appear. Within the Select an Import Wizard section, expand SAP HANA Content and then choose Delivery Unit. Click Next to continue. A new popup window will appear titled Target System. In the list of systems, select the system that will serve as the import target for the delivery unit file. Click Next to continue. The Import Through Delivery Unit window will appear, as shown in [Figure 14.17](#14_003.html#f14.17).

[![Import Options in SAP HANA Studio](bilderklein/klein14_017.png)](img-f14.17.html)

## Figure 14.17 Import Options in SAP HANA Studio

To configure the import options, start by choosing the import file location. Choose the Client location for files stored on the SAP HANA Studio client system. Click the Browse button to specify the path of the file. In the Actions section, choose from the following options: Select the Overwrite inactive versions checkbox to import the delivery unit content even if another version of the content already exists in the target. Select the Activate objects checkbox to have the import wizard activate the newly imported development artifacts. If this option isn’t selected, the objects will be imported without activation.

In the Activate Mode dropdown list, decide how the wizard should handle inconsistencies. The Activate and ignore the inconsistencies in affected objects mode will activate the objects directly found in the delivery unit file even if their activation causes existing development artifacts to become inconsistent. The Stop activation in case of inconsistencies in affected objects option will stop the activation process if any inconsistencies are detected during import. The default option is to Activate and ignore the inconsistencies in imported objects and in their affected objects. With this option selected, the import wizard will attempt to activate development artifacts found in the delivery unit file even if some of the artifacts and their affected objects fail to import.

The Object import simulation section contains a listing of the development artifacts that will be imported. In addition, you’ll see the anticipated activation status based on a review of the target repository. Note that objects might fail to import even if the simulation indicates that no errors will arise. Click Finish to import the objects.
