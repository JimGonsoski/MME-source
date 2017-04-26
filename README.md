Minnesota Metadata Editor
==========

MME is a DotNet incarnation of a simple editor for GIS metadata XML files that adhere to the [Minnesota Geographic Metadata Guidelines (MGMG version 1.2)](http://www.mngeo.state.mn.us/committee/standards/mgmg/metadata.htm). 

#### MME Version
    1.2.1

1. Force 'mailing and physical' in addrtype fields for contacts if none provided on these tags:
    * 10290 idinfo/ptcontac/cntinfo/cntaddr/addrtype
    * 13250 distinfo/distrib/cntinfo/cntaddr/addrtype
    * 13450 metainfo/metc/cntinfo/cntaddr/addrtype
2. XSL template MGMG.xsl
   * return the 'HTTP' protocol that was stripped during formatting on output.
   * allow HTTPS as a URL protocol that HyperLinks.
3. Remove all references to MnGeo.
4. Change the spatial extent of data field to a text box (from a combo with pull-down list).
5. Fix Online linkage, publisher field wipe-out when doing a 'refresh from database'.
6. Help links from menu and field label link directly to MnGeo Help URL.
7. Minnesota County Coordinate System now supports 'feet' as well as 'meters' for NAD83 datum.
8. Extraneous blank rows in database tables removed. This should prevent poeple from setting blank values as default.
9. Add check for database version and fail to load if the wrong database is used - link user to a help page.
10. Add fields: Vertical Datum, vertical Units, depth datum, depth units, browse graphic description.
11. Modify fields: Publication Date, Progress of data, Update Frequency to pull-down lists + text entry.   

What it is
==========
The Minnesota Metadata Editor (MME) is a desktop application that is intended to simplify and expedite the process of developing geospatial metadata.  

The program operates as a standalone application that helps you create, edit and display formatted metadata that adheres to the [Minnesota Geographic Metadata Guildelines (MGMG version 1.2)](http://www.mngeo.state.mn.us/committee/standards/mgmg/metadata.htm), an implementation of the Federal Geographic Data Committee's (FGDC's) Content Standard for Digital Geospatial Metadata (CSDGM).  

The MME is a customized version of the EPA Metadata Editor (EME) 3.1.1.  For more information on the EPA Metadata Editor, see [https://edg.epa.gov/EME/](https://edg.epa.gov/EME/). 

## Get it

Visit the [MME GitHub site](https://github.com/MetropolitanCouncil/MME) and click the **Download ZIP** button in the lower right-hand corner to get a copy of the program. It might help to [read the help](http://www.mngeo.state.mn.us/chouse/mme/help).

## Run it
MME runs as portable application and needs no installation. Just unzip the contents of the application to any folder on your computer (We suggest **Minnesota Metadata Editor** as the folder name). Then open the folder and double-click **MetadataEditor.exe** to run the editor. 

Microsoft .NET Framework 3.5 must be installed on your machine.You can determine if the .NET Framework is on your machine by going to Start->Control Panel->Add or Remove Programs. 
You should see Microsoft .NET Framework 3.5 listed.  Multiple versions of Microsoft .Net Framework (e.g., 1,2,3) may exist on your machine simultaneously. Microsoft's .NET Framework 3.5 is freely available and can be accessed from [Microsoft's website](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=21).

### Source
The source code for this application is available [here](https://github.com/MetropolitanCouncil/MME-source) with no strings attached. It was last compiled with Visual Studio 2012 but should be reasonably compatible with Visual Studio 2010 if you create a new solution. Most of the **helper** files for spell-checking and old-time XML support are included in the \bin\debug directory.

### Database
The application is data-driven using a Microsoft Access database -- metadata.mdb -- stored in the application **\portable** folder. You can edit this database to assign default values that apply to your particular agency or group. You need Microsoft Access in order to edit the database. Once edited, it can, however, be distributed to other machines that do not have Access installed. The application, itself, does not require Access installed on the local computer in order to run.

#### MME Table
The relationship between the form fields and the metadata tags they store in are defined in the database table **MME**. The order of the table rows determines the order of the output metadata tags. The field *srcTable* determines if a special database table exists to hold values for populating pull-down or setting default values in the fields.

The *help* field designates a help file URL that deviates from the standard of *tabNo_tag* (i.e. \t1_publish.html). It also allows for designating the same help page for multiple related fields. 

The *cluster* field designates a root tag for each individual field in the database table that defines the cluster allowing you to define a row that in turn populates many metadata tags on output. Contact information is a good example. Each person designated as a contact can have a separate set of information defining organization, address and contact information.

### Structure
Originally, this program came in three-flavors: 1) an installed version that integrated with ESRI ArcMap, 2) an installed version that was stand-alone, and 3) a portable version that required no installation. Eventually flavors 1 ans 2 were removed in favor of 3 as it created the least number of problems. 

The program checks for a \portable directory in the applicaton path and uses this as its database. The database must have a table called *Version* (added in release 1.2.1) or else all will fail.


