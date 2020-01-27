# CA Unified Infrastructure Manager

The xMatters probe is set to sit on your UIM message bus and listen for any message with a subject of "xmatters".

When a event with a subject of "xmatters" is found, the xmatters probe will execute the xmattersgtw.jar file and POST UIM fields over to an inbound integration in the xMatters workflow.

The xMatters workflow has outbound integration for Event Status and Response. The outbound integration points to the xMatters Integration Agent which updates UIM tickets.

---------

<kbd>
  <img src="https://github.com/xmatters/xMatters-Labs/raw/master/media/disclaimer.png">
</kbd>

---------



# Pre-Requisites
## For the integration
* Nimsoft UIM version 8.4
* xMatters Integration Agent - Download [here](https://support.xmatters.com/hc/en-us/articles/201463419-Integration-Agent-for-xMatters-5-x-xMatters-On-Demand)
* xMatters account - If you don't have one, [get one](https://www.xmatters.com)!

## For customizing the integration
See [here](#import-eclipse-project) for instructions. 
* [Java SE Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* [Eclipse IDE for Java Developers](http://www.eclipse.org/downloads/packages/eclipse-ide-java-developers/neon3)
* [Winzip](http://www.winzip.com/), [Unarchiver](http://unarchiver.c3.cx/unarchiver), or another application capable of extracting a Jar File.
* [UIM Help Documents](https://docops.ca.com/ca-unified-infrastructure-management/8-5-1/en)
* [UIM Probes Help Documents](https://docops.ca.com/ca-unified-infrastructure-management-probes/ga/en)


# Files
* [xmattersgtw_1.14.zip](xmattersgtw_1.14.zip) - xMatters UIM Probe 
* [xmattersgtw-Eclise-Archive.zip](xmattersgtw-Eclise-Archive.zip) - xMatters Eclipse Project
* [UIMNimsoft-xMatters-Workflow.zip](UIMNimsoft-xMatters-Workflow.zip) - xMatters UIM Nimsoft Workflow
* [UIM-xMatters-Integration-Service.zip](UIM-xMatters-Integration-Service.zip) - UIM Integration Service for Integration Agent



# How it works
The xMatters probe is set to sit on your UIM message bus and listen for any message with a subject of "xmatters".

When a event with a subject of "xmatters" is found, the xmatters probe will execute the xmattersgtw.jar file and POST UIM fields over to an inbound integration in the xMatters workflow.

The xMatters workflow has outbound integration for Event Status and Response. The outbound integration points to the xMatters Integration Agent which updates UIM tickets.

## Default UIM Fields passed to xMatters

The out of the Box properties that UIM will send to xMatters are as follows:

*UIM Property List:*

* subject
* alarmSev
* hostname
* subsystem
* robot
* probe
* message
* timeReceived
* timeArrived
* alarmCount
* alarmID
* alarm_source
* UserTag1
* UserTag2
* Custom_1
* Custom_2
* Custom_3
* Custom_4
* Custom_5



# Installation
These are instructions for installing the base integration. For details on customizing the integration, see [below](#import-eclipse-project)

## UIM Setup
### Add xmattersgtw_1.14.zip to the archive

Whether you have customized a java file and created a new jar file or not you will need to do this step. 
You will be able to add your a customized jar file to the package after it is added to the archive.

1. Go into Archive
2. Right click anywhere in the archive and go to Import 

<kbd> 
	<img src="media/14_import_archive.png">
</kbd>

3. Browse to the xmattersgtw_1.14.zip
4. Click Open

### Updating xmattersgtw_1.14 Package with customized Jar File

1. Go into Archive
2. Locate the xmattersgtw package that was installed perviously
3. Double click on xmattersgtw package
4. Remove xmattersgtw.jar file
  1. Go to the Files Tab and locate the xmattersgtw.jar file.
  2. Right click on the xmattersgtw.jar file and go to Remove file
  3. Click OK to confirm remove

<kbd>
	<img src="media/15_remove_archive.png">
</kbd>

5. Right click anywhere in the Files Tab and go to Add File...

<kbd>
	<img src="media/16_add_file.png">
</kbd>

6. Click Browse

<kbd>
	<img src="media/17_browse.png">
</kbd>

7. Select the updated xmattersgtw.jar file.
8. Click OK
9. Click Ok again.
10. Confirm that the new file has been added to the package.
11. Click OK.


### Deploying the xMattersgtw probe

There are two ways to deploy a probe.

#### Drag and drop the probe from the Archive to a domain/hub/robot

<kbd>
	<img src="media/18_drag_n_drop.png">
</kbd>

#### Distribute the probe as instructed below.

1. Select xmattersgtw package in the archive.
2. Right-click and select Distribute from the menu. A Distribute dialog box appears.

<kbd>
	<img src="media/19_distribute.png">
</kbd>

3. Select the domain/hub/robot where you want to distribute the package, and click the Add button. The domain/hub/robot name appears in the right column.
4. Click OK. A View Distribution Progress dialog box appears with detailed information about the distribution. *Note*: You can minimize this dialog box and continue working in Infrastructure Manager without interfering with the distribution.

<kbd>
	<img src="media/20_progress_dialog.png">
</kbd>

5. Click the Close Dialog button after distribution is finished. 


### Configuring the xmattersgtw probe

1. Navigate to the domain/hub/robot where you deployed the xmattersgtw probe.
2. Right click on xmattersgtw probe and go to Raw Configure...

<kbd>
	<img src="media/21_raw_configure.png">
</kbd>

3. Set the following values:

You will get the values for this step after you have configured and installed the UIM - Nimsoft xMatters Workflow. You will do this later in this guide and instructions can be found here. LINKME

*xmattersurl* = This is the url of the Inbound Integration for the Nimsoft xMatters Workflow. 
*logfile* = xmattersftw.log
*loglevel* = Set how detailed you want the log to be. 1 = Very few logs, 5 : The most logs, debug.
*cmattersuser* = uim_api
*xmattespassword* = The password for uim_api user created in xMatters.

4. Click OK
5. Right clik on xmattersgtw probe and go to Activate. 

### Setting up an alarm repost with subject of xmatters

The xMatters probe is set to sit on your UIM message bus and listen for any message with a subject of "xmatters".

When a event with a subject of "xmatters" is found, the xmatters probe will execute the xmattersgtw.jar file and do an api call to send UIM fields over to xMatters.

The Nimsoft Alarm Server processes all alarms.


1. Go to your domain/hub/robot that you previously installed the xMatters probe.
2. Locate the probe named nas (Nimsoft Alarm Server)

<kbd>
	<img src="media/22_nas.png">
</kbd>

3. Double click on the nas probe.
4. Go to Auto-Operator tab and then to the Profiles tab.
5. Right click anywhere in the list and go to New.

<kbd>
	<img src="media/23_new.png">
</kbd>

6. Configure the New Profile as follows:

*Action Type*: repost

*Subject*: xmatters (must be all lowercase)

*Action mode*: On message arrival (or at another interval if your use case requires)

*Matching Criteria*: Set your criteria for what messages you want to create a repost on and send to xMatters. Remember the xMatters probe is looking for this repost and when it finds it, the event will be sent to xMatters.


For more information go [here](https://docops.ca.com/ca-unified-infrastructure-management-probes/ga/en/alphabetical-probe-articles/nas-alarm-server/nas-versions-4-4-4-7/v4-6-nas-im-configuration/the-auto-operator-tab-v4-6#TheAuto-OperatorTabv4.6-ProfileAdvanced).

<kbd>
	<img src="media/24_repost.png">
</kbd>


## Installing xMatters Integration Agent

Follow instructions located [here](https://support.xmatters.com/hc/en-us/articles/202004275). 

Once you have  installed the xMatters Integration Agent and it is successfully communicating with xMatters you can go on to the next steps below.

### Correcting UIM callback logging error

1. Open the xMatters integration agent script `/lib/integrationservices/javascript/xmio.js`
2. Change line 104 to 109 from this:

```javascript
var response = {};
response.status = resp.getStatusLine().getStatusCode();
response.body = XMIO.http.getResponseAsString(resp);
XMIO.http.releaseConnection(resp);
IALOG.info("\t\tReceived response code: {0} and payload: {1}", response.status,  response.body);
return response;
```


To:

```javascript
var response = {};
response.status = resp.getStatusLine().getStatusCode();

if (method !== 'PUT') {
    response.body = XMIO.http.getResponseAsString(resp);
    XMIO.http.releaseConnection(resp);
    IALOG.info("\t\tReceived response code: {0} and payload: {1}", response.status, response.body);
}
else {
    XMIO.http.releaseConnection(resp);
    IALOG.info("\t\tReceived response code: {0}", response.status);
}    
return response;
```

## Configure the Integration Agent

### Add UIM Integration Service to the Agent

Extract the contents of UIM-xMatters-Event-Domain.zip into the following Integration Agent Directory.

`<IA-Home>\integrationservices\applications\`

The directory structure should become: `<IA-Home>\integrationservices\applications\uim\`
 
### Edit the configuration.js file

1. Navigate to the directory `<IA-Home>\integrationservices\applications\uim`
2. Open `configuration.js`
3. Edit the following lines. These lines are part of the UIM Put API path in uim.js file.
*Line 15*: `UIM_PROTOCOL = "http";`
*Line 16*: `UIM_SERVER = "amdc1pxm02";`
The following is the default path for UIM Put API:
`UIM_PROTOCOL + "://" + UIM_SERVER + "/rest/alarms/" + msg.additionalTokens.alarmID + "/assign/"`
4. And these lines. These are for Authenticating the Put API into UIM system. 
*Line 19*: `UIM_USER = "xmatters";`
*Line 20*: `UIM_SERVER = "password";`
A user in UIM must exist with the user ID and password set in these lines. 
This user must have permission to make web service calls into UIM.
5. Save and close `configuration.js`.



### Add new Integration Service reference

1. Navigate to the directory `<IA-Home>\conf\`
2. Open `IAConfig.xml`
3. Scroll down to around line 330 and look for the code:

```xml
<service-configs dir="../integrationservices">
  <!--
| 0 or more paths (relative to <services-configs>/@dir), that refer to
| the Service Config files that this IA will load whenever it is started or
| the "iadmin reload all" command is issued.
|
| NOTE: Paths may be Unix or Windows-formatted, although it is
| recommended that Unix-formatting be used since it works under both environments.
|
| NOTE: Depending on the OS, paths may be case-sensitive.
-->
```

4. Add the following path just before `</service-configs>`:
`<path>applications/uim/uim.xml</path>`
5. Save `IAConfig.xml`
6. Close `IAConfig.xml`


## Set up xMatters

###  Add new Event Domain to xMatters instance

1. Login to xMatters instance with a user that has company supervisor role.
2. Go to Developer Tab 
3. Click on Event Domains

<kbd>
	<img src="media/25_event_domains.png">
</kbd>

4. Click on the Event Domain with the name `applications`.

<kbd>
	<img src="media/26_applications_domain.png">
</kbd>

5. Click Add New beside the INTEGRATION SERVICES SECTION at the bottom of the page. *Note* there may already be another integration service installed. 

<kbd>
	<img src="media/27_new_integration_service.png">
</kbd>

6. Give the new Integration Service the name: `uim`. Add a description if you would like. Do not fill in a path.

<kbd>
	<img src="media/28_name.png">
</kbd>

7. Click Save button. 


## Test that the new Integration Service is Working

### Integration Agent

1. Open a new Command Prompt window as an Administrator.
2. Change to the `<IA-Home>\bin` directory
3. Stop the integration agent using the following command:
`stop_service`
4. Start the integration agent using the following command:
`start_service`
5. After the Integration Agent has successfully started run the following command:
`iadmin get-status`
6. Scroll through the command window and ensure uim application has status ACTIVE.
```
Name: uim
Clients: [APCLIENT, MG]
URL: http://hostnamehere:8081/applications_uim
Started: May 12, 2017 9:07:30 AM
Last request: none
Status: ACTIVE
Pending request count: 0
Normal priority inbound APXML queue size: 0
High priority inbound APXML queue size: 0
Normal priority outbound APXML queue size: 0
High priority outbound APXML queue size: 0
```

### xMatters Web UI
1. Login to your xMatters instance.
2. Navigate to the Developer Tab.
3. Click on Event Domains.
4. Click on the event domain named applications
5. Look at INTEGRATION SERVICES section and ensure the status of uim is *Active*

### Dealing with Errors
If uim has Status: ERROR you will need to trouble shoot the problem.

1. Open the following file: 
`<IA-Home>\log\AlarmPoint.txt`
2. Search for uim
3. Read the log to find out where the error is
4. Correct the error


## Configure xMatters UIM Workflow

Download the workflow: [UIMNimsoft-xMatters-Workflow.zip](UIMNimsoft-xMatters-Workflow.zip)

### Create an xMatters API user

1. Login to your xMatters instance.
2. Click on USERS tab.
3. Click Add button.
4. Create a new user. This user will have permission to make xMaters Web Service calls and will be the user that authenticates into xMatters from UIM.
User ID: uim_api
Roles: REST Web Services User

<kbd> 
	<img src="media/29_rest_user.png">
</kbd>

6. Click Add. 

### Install xMatters UIM Workflow

1. Login to your xMatters instance.
2. Navigate to the Workflows 
3. Click Import Worflow.

<kbd>
	<img src="media/30_import_workflow.png">
</kbd>

4. Choose File: UIMNimsoft-xMatters-Workflow.zip.
5. Click Import.
6. Ensure the Plan is Enabled.
7. Click Edit -> Access Permissions. Check Accessible by All. Alternatively, select the REST user from above and any other developers who should have edit access. 

<kbd>
	<img src="media/31_accessible_by_all.png">
</kbd>

8. On the UIM - Nimsoft Workflow click Edit -> Forms
9. Ensure Web Service Only is checked / enabled. 
10. Click Web Service Only -> Sender Permissions.
11. Add `uim_api` user to have sender permission. (Created above)

<kbd>
	<img src="media/32_form_sender.png">
</kbd>

### Configure Integration Builder Settings

1. Click on Integration Builder tab
2. Click Edit Endpoints button
3. Assign the uim_api user to the xMatters Endpoint and Save Changes.

<kbd>
	<img src="media/33_assign_endpoint.png">
</kbd>

4. Expand the Inbound Integrations by clicking on 1 Configured 
5. Click on `UIM - Inbound`
6. Copy the Inbound Integration url at the bottom of the page. 

<kbd>
	<img src="media/34_inbound_url.png">
</kbd>

7. Configure the UIM Probe according to instructions found [here](#configuring-the-xmattersgtw-probe).
  * The Inbound Integration url from the previous step is used for the xmattersurl.
  * The credentials for the uim_api user are used for cmattersuser and xmattespassword.
8. Check the configuration of each of the outbound integrations.
9. Expand the Outbound Integrations by clicking on 2 Configured.
10. Click Event Status.
11. Ensure that Step 5: Select integration service has uim selected.
12. Enter the Integration Agent Name.
  1. If you are not sure of the Integration Agent Name:
  2. Click on Agents in the left had menu.
  3. Click on INSTALLED
  4. Copy the name of the installed Integration Agent that you want to target.

  <kbd>
  	<img src="media/35_installed_agents.png">
  </kbd>
13. Repeat these for Outbound Integration: Response. *Note*: Make sure to use the same agent for both outbound integrations

   
# Testing
Create an event in UIM with a subject of `xmatters`. An event will be generated in xMatters targeting the designated recipients. The recipients will receive notifications based on their device selection and can then respond. The responses will be sent back to xMatters for auditing, then along to the Integration Agent and finally the event in UIM will be updated reflecting the user's reponse. 

# Troubleshooting

## Inbound from UIM

If an event is not reaching xMatters as expected, check the UIM log to ensure the POST to xMatters was attempted. If it was attempted, check the Inbound Integration Activity Steam for any errors. 

## Outbound from xMatters

If a response is not being logged in UIM, check `<IA-Home>/log/AlarmPoint.txt` file for any errors. 


# Customizing
This section details how to make changes to the UIM Probe or to send fields to xMatters that are not part of the Out of Box UIM Probe.

## Pre-steps
1. Install an application that can extract Jar files such as: Winzip or Unarchiver
2. Check what version of Java you have installed. For instructions go [here](https://www.java.com/en/download/help/version_manual.xml#jcpl).
3. If you have Java 8 or higher: Go to step 4
4. If your version of Java is older than Java 8:  Install Java 8+ from the link below.
[Java SE Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
5. Install Eclipse by downloading here: [Eclipse IDE for Java Developers](http://www.eclipse.org/downloads/packages/eclipse-ide-java-developers/neon3)


## Import Eclipse project
### First time running Eclipse
1. Open Eclipse.
2. Follow the prompts to create a new workspace. This is where all Eclipse projects will be stored. 
3. After Creating a new Workspace you will be taken the the welcome screen shown below.
4. Click Import existing projects.

<kbd>
	<img src="media/1_Import_existing.png">
</kbd>

5. Check Select archive File radio button.
6. Browse and select xmattersgtw-Eclipse-Archive.zip file.
7. Ensure *xMatters_UIM (xMatters_UIM/)* project is selected.

<kbd>
	<img src="media/2_Import_part_2.png">
</kbd>

8. Click Finish.


### Using an existing Workspace
1. Open Eclipse.
2. Select an existing Workspace or create a New Workspace.
3. File -> Import.
4. Expand General Folder, Select Existing Project into Workspace and click Next.

<kbd>
	<img src="media/3_Import_Existing.png">
</kbd>

5. Check Select archive File radio button.
6. Browse and select [xmattersgtw-Eclipse-Archive.zip](xmattersgtw-Eclipse-Archive.zip) file.
7. Ensure xMatters_UIM (xMatters_UIM/) project is selected.

<kbd>
	<img src="media/4_Import_Existing_part_2.png">
</kbd>

8. Click Finish.

## Modifying Java files

Locate the Java files by expanding the following items in your Eclipse Project and double clicking on the Java file.

xMatters_UIM -> src -> com.uim.field.xmattersgtw -> XMattersAlarmTemplate.java
xMatters_UIM -> src -> com.uim.field.xmattersgtw -> XMattersGtw.java

<kdb>
	<img src="media/5_Package_Explorer.png">
</kbd>


## Packaging a New Jar File

If you have made a change to a java file, you will need to create a new Jar file in Eclipse. The following process will walk you through this.

1. Make sure your project is saved. 
2. Close all open file editing windows with Java or Manifest files. Leaving these open can cause compiling to fail.
3. Start The export process. File -> Export

<kbd>
	<img src="media/6_Export.png">
</kbd>

4. Expand Java Folder, Select JAR file and click Next.
5. Select the following resources to export:
*Select:*
- [x] src
- [x] src -> com.uim.field.xmattersgtw
- [x] src -> com.uim.field.xmattersgtw ->XMattersAlarmTemplate.java
- [x] src -> com.uim.field.xmattersgtw ->XMattersGtw.java

*Do Not Select:*
- [ ] .settings
- [ ] com
- [ ] lib
- [ ] META-INF

<kbd>
	<img src="media/7_Select.png">
</kbd>

6. Ensure the following Export Settings are Checked / Unchecked

<kbd>
	<img src="media/8_settings.png">
</kbd>

7. Select the export destiation by clicking Browse. Give the file the following name: xmattersgtw.jar

<kbd>
	<img src="media/9_filename.png">
</kbd>

8. Ensure the following options are Cheked/ Unchecked:

<kbd>
	<img src="media/10_options.png">
</kbd>

9. Click Next >. *Do not click finish!*
10. Ensure the following are checked:
-[x] Export class files with compile errors
-[x] Export class files with compile warnings

<kbd>
	<img src="media/11_more_options.png">
</kbd>

11. Click Next >. *Do not click finish!*
12. Select *Use existing manifest from workspace* and browse to the following file:

<kbd>
	<img src="media/12_yet_more_options.png">
</kbd>

13. Expand *META-INF* folder, select the *MANIFEST.MF* file and click Ok. 

<kbd>
	<img src="media/13_manifest.png">
</kbd>

14. Click *Finish*.



## Troubleshooting Typical Eclipse / UIM Errors 

If you are getting errors when compiling your jar package in eclipse try the following.


*Errors about the Build Path try the following:*

- Project => Clean
- File => Refresh
- Close all open files in Eclipse, try to export jar again.
- Check your Build Path:
  1. Right Click xMatters_UIM go to Properties
  1. Double Click Java Build Path
  1. Click on Sources Tab
  1. Ensure Default output folder is set to:  xMatters_UIM/com/uim/field/xmattersgtw
- File => Restart


*Errors about the version of Java when installing into UIM:*

Change the Java Compiler version in Eclipse:
1. Right Click xMatters_UIM go to Properties.
1. Double Click Java Compiler
1. Uncheck Use Compliance from execution environment
1. Change Compiler compliance level to appropriate version

