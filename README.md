# CA Unified Infrastructure Manager

The xMatters probe is set to sit on your UIM message bus and listen for any message with a subject of "xmatters".

When a event with a subject of "xmatters" is found, the xmatters probe will execute the xmattersgtw.jar file and POST UIM fields over to an inbound integration in the xMatters communication pan.

The xMatters communication plan has outbound integration for Event Status and Response. The outbound integration points to the xMatters Integration Agent which updates UIM tickets.



# Pre-Requisites
## For base integration
* CA UIM VERSION HERE
* xMatters Integration Agent - Download [here](https://support.xmatters.com/hc/en-us/articles/201463419-Integration-Agent-for-xMatters-5-x-xMatters-On-Demand)
* xMatters account - If you don't have one, [get one](https://www.xmatters.com)!

## For customizing the integration
* [Java SE Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* [Eclipse IDE for Java Developers](http://www.eclipse.org/downloads/packages/eclipse-ide-java-developers/neon3)
* [Winzip](http://www.winzip.com/), [Unarchiver](http://unarchiver.c3.cx/unarchiver), or another application capable of extracting a Jar File.
* [UIM Help Documents](https://docops.ca.com/ca-unified-infrastructure-management/8-5-1/en)
* [UIM Probes Help Documents](https://docops.ca.com/ca-unified-infrastructure-management-probes/ga/en)


# Files
* [xmattersgtw_1.14.zip](xmattersgtw_1.14.zip) - xMatters UIM Probe 
* [xmattersgtw-Eclise-Archive.zip](xmattersgtw-Eclise-Archive.zip) - xMatters Eclipse Project
* [UIMNimsoft-xMatters-Comm-Plan.zip](UIMNimsoft-xMatters-Comm-Plan.zip) - xMatters UIM Nimsoft Communication Plan
* [UIM-xMatters-Integration-Service.zip](UIM-xMatters-Integration-Service.zip) - UIM Integration Service for Integration Agent



# How it works
The xMatters probe is set to sit on your UIM message bus and listen for any message with a subject of "xmatters".

When a event with a subject of "xmatters" is found, the xmatters probe will execute the xmattersgtw.jar file and POST UIM fields over to an inbound integration in the xMatters communication pan.

The xMatters communication plan has outbound integration for Event Status and Response. The outbound integration points to the xMatters Integration Agent which updates UIM tickets.


# Installation
Details of the installation go here. 

## Application ABC set up
Specific steps go here

## xMatters set up
1. Create a new Shared Library or (In|Out)bound integration
2. Add this code here:
   ```
   var items = [];
   items.push( { "stuff": "value"} );
   console.log( 'Do stuff' );
   ```
   
# Testing
Be specific. What should happen to make sure this code works? What would a user expect to see?

# Troubleshooting
Optional section for how to troubleshoot. Especially anything in the source application that an xMatters developer might not know about. 
