+++
weight = "10"
type = "post"
draft = false
sidebar = false
date = 2016-10-21T07:56:39Z
title = "IOOS Metadata Profile for NetCDF, Version 1.0"

+++




*This page provides description of the IOOS NetCDF Metadata Profile that IOOS Program Office has developed for distribution of the IOOS data using THREDDS or ERDDAP servers. The use of the Profile is strongly recommended to all IOOS Data Providers, including RAs and various DACs.*
<!--more-->


# Scope

The Profile defines the bare minimal set of attributes for IOOS Data Providers to include in their NetCDF data files. The Profile allows the NetCDF metadata to overlap with the IOOS SOS metadata in order to ensure a comprehensive cross-walk from NetCDF to IOOS SOS representation via the ncSOS service.
 
While matching the IOOS SOS metadata, the Profile allows the lowest achievable divergence of the IOOS NetCDF files from the NODC/NCEI NetCDF Templates - the Profile includes the Templates' attributes and augment them with a small number of IOOS-specific attributes just to ensure that NetCDF files inherently contain metadata required for the IOOS SOS output in cases when the NODC/NCEI Templates come short. 

Apart from the IOOS-specific portion, the IOOS Profile generally follows the requirements and recommendations of the NOAA NODC NetCDF Templates v1.1 & NCEI NetCDF Templates v2.0, Attribute Conventions for Dataset Discovery v1.1 & 1.3, and Climate and Forecast Conventions v1.6. A Data Provider may use any metadata attributes in the NetCDF file; however, the IOOS Program Office strongly encourages to restrict the attribute variety to the attributes suggested by these Conventions and Templates:

* [**NOAA NODC NetCDF Templates v1.1**](http://www.nodc.noaa.gov/data/formats/netcdf/v1.1/) and [**NOAA NCEI NetCDF Templates v2.0**](http://www.nodc.noaa.gov/data/formats/netcdf/). 
* [**Climate and Forecast (CF) Conventions v1.6**](http://cf-pcmdi.llnl.gov/documents/cf-conventions/1.6/cf-conventions.html).
* [**Attribute Conventions for Dataset Discovery (ACDD) v1.1**](http://wiki.esipfed.org/index.php/Attribute_Convention_for_Data_Discovery_1-1) and [**ACDD v1.3**](http://wiki.esipfed.org/index.php/Attribute_Convention_for_Data_Discovery_1-3). 

# Caveats

 1. [**NOAA NODC NetCDF Templates v1.1**](http://www.nodc.noaa.gov/data/formats/netcdf/v1.1/) is required; the [**NOAA NCEI NetCDF Templates v2.0**](http://www.nodc.noaa.gov/data/formats/netcdf/) is not recommended at the moment. 
 2. [**Attribute Conventions for Dataset Discovery (ACDD) v1.1**](http://wiki.esipfed.org/index.php/Attribute_Convention_for_Data_Discovery_1-1) is required. The [**ACDD v1.3**](http://wiki.esipfed.org/index.php/Attribute_Convention_for_Data_Discovery_1-3) is not recommended at the moment, except for the **`platform_vocabulary`** attribute.  
 2. Each attribute in the Profile is either **required** or **recommended**. 
 3. All **required** attributes must have meaningful values assigned to them in accordance with the rules prescribed by the corresponding Convention or Template. 
 4. Each and all of the **recommended** attributes may be omitted; however, it is highly desirable that these attributes are included into the NetcDF metadata ***AND*** have meaningful values assigned to them. 
 5. The **`platform_variable:ioos_code`** and **`platform_variable:short_name`** are the only **interchangeable** attributes - either a single **`platform_variable:ioos_code`** or a combination of **`platform_variable:short_name`** with **`naming_authority`** is **required** to ensure that ncSOS will be able to produce the IOOS SOS Asset Identifier for the specific platform (see the [NetCDF to IOOS SOS Crosswalk](https://github.com/ioos/ioos-netcdf/blob/master/docs/NetCDF-to-SOS%20Mappings_clean_2016-04-07a.xlsx) for details). The rest of attributes ***may not*** be substituted for one another.
 6. The **`platform_vocabulary`** attribute is at the moment the only pure ACDD v1.3 attribute that is included in the Profile. 
 6. This document only describes a fraction of the Profile:
   - attributes that are IOOS-specific;
   - attributes with a different role in the Templates; for example, the attribute **`_FillValue`** is required by the NODC Template; however, the Profile just recommends to use it because it is optional in the IOOS SOS metadata set (whether the Template requirement should prevail, is beyond the scope of the Profile description);
   - attributes that are **required** by the Profile regardless of their role in the Templates. 
 7.  Other Profile attributes are described in the [**NOAA NODC NetCDF Templates v1.1**](http://www.nodc.noaa.gov/data/formats/netcdf/v1.1/).  A set of "Gold Standard" example NetCDF files, which precisely follow the NODC/NCEI Templates, may be found [here](http://data.nodc.noaa.gov/ncei/example/data/netcdf/) or [here](http://data.nodc.noaa.gov/thredds/catalog/example/catalog.html).
 8.  The [**U.S. IOOS National Glider Data Assembly Center**](https://gliders.ioos.us/index.html) currently uses a slightly different [NetCDF Metadata Profile](https://github.com/ioos/ioosngdac/wiki/NGDAC-NetCDF-File-Format-Version-2); work is in progress to harmonize the NGDAC and IOOS NetCDF Profiles. 


# IOOS NetCDF Metadata Profile Attributes

Name | Convention | Description | Type | Role 
:--------- | :-------: | :------------------- | :--------: | :-------:
contributor_name | ACDD | The name of any individuals or institutions that contributed to the creation of this data. Combined with the **`contributor_role`**, it provides the full description of the contributor. | global | required
contributor_role | ACDD | The role of any individuals or institutions that contributed to the creation of this data. <br>For the IOOS ncSOS, **`contributor_role = "sponsor"`** defines a person, group, or organization’s full or partial support of an IOOS activity, asset, model, or product. | global | required
creator_address | IOOS | Street address of the person or organization that collected the data.  | global | recommended
creator_city | IOOS | City of the person or organization that collected the data.  | global | recommended
creator_country | IOOS | Country of the person or organization that operates a platform or network, which collected the observation data. | global | required 
creator_email  | ACDD | Email address of the person or institution that collected the data. | global | required
creator_name  | ACDD | Name of the person or organization that collected the data. | global | recommended
creator_phone | IOOS | The phone number of the person or group that collected the data. | global | recommended
creator_sector | IOOS | [IOOS classifier](http://mmisw.org/orr/#http://mmisw.org/ont/ioos/sector) that best describes the platform (network) operator's societal sector. <br><br>Example: **`creator_sector = "academic"`** | global |required
creator_state | IOOS | State of the person or organization that collected the data.  | global | recommended
creator_url  | ACDD | The URL of the institution that collected the data. | global | recommended
creator_zipcode | IOOS | ZIP code of the person or organization that collected the data.  | global | recommended
featureType | CF | CF attribute for identifying the featureType, e.g. featureType = "timeSeries". | global | required
geophysical_variable:_FillValue<br><br>geospatial_variable:_FillValue | CF | This value is considered to be a special value that indicates undefined or missing data, and is returned when reading values that were not written: <ul>  <li>time:_FillValue = 0.0f    <li>lat:_FillValue = 0.0f    <li>on:_FillValue = 0.0f    <li>z:_FillValue = 0.0f    <li>sea_water_temperature:_FillValue = 0.0f</ul> | variable | recommended
geophysical_variable:standard_name | CF | Standardized field which uses the [CF Standard Names](http://www.cfconventions.org/documents.html/). If a variables does not have an existing standard_name in the CF-managed list, this attribute should not be used. In these cases, a standard name can be proposed to the CF community for consideration and acceptance. | variable | required
id | ACDD | An identifier for the data set, provided by and unique within its naming authority. The combination of the **`naming authority`** and the **`id`** should be globally unique, but the **`id`** can be globally unique by itself also. IDs can be URLs, URNs, DOIs, meaningful text strings, a local key, or any other unique string of characters. The **`id`** should not include blanks. | global | required
institution  | ACDD | The institution of the person or group that collected the data. | global | required
instrument_variable:discriminant | IOOS | The value of a **`discriminant`** applies to the like-named field in the IOOS SOS Asset Identifier URN; it ensures that in case of multiple sensors measuring the same **`observedProperty`**, each sensor has a unique ID. <br><br>Examples: <ul> <li>sea_water_temperature:**top** <li> sea_water_temperature:**bottom** <li> sea_water_temperature:**nortek_adp_514** </ul>| variable | required, if applicable
keywords | ACDD | A comma separated list of key words and phrases. | global | recommended
license  | ACDD | Describe the restrictions to data access and distribution. | global | recommended
naming_authority  | ACDD | The organization that provides the **`id`** for the dataset. <br>The naming authority should be uniquely specified by this attribute; the combination of the **`naming_authority`** and the **`id`** should be a globally unique identifier for the dataset. A reverse-DNS naming is recommended; URIs are also acceptable. <br>Example: **`edu.ucar.unidata`** | global | required
platform | NODC Templates<br>(ACDD 1.3) | Name of the platform(s) that supported the sensor data used to create this data set or product. Platforms can be of any type, including satellite, ship, station, aircraft or other. The controlled vocabulary must be indicate in **`platform_vocabulary`** (see example there).<br>The value of the attribute should be set to another variable which contains the details of the platform. There can be multiple platforms involved depending on if all the instances of the featureType in the collection share the same platform or not. If multiple platforms are involved, a variable should be defined for each platform and referenced from the geophysical variable in a <b>space</b> separated string. | global | required 
platform_variable:ioos_code | IOOS | Provides IOOS asset identification similar to **`wmo_code`** and **`nodc_code`**. The attribute is a URN that should follow the "[IOOS Convention for Asset Identification](http://ioos.github.io/conventions-for-observing-asset-identifiers/ioos_assets_wiki_upd_v0_8_draft/)" with a general pattern of _**`urn:ioos:asset_type:authority:label[:discriminant]`**_.  <br><br>Examples: <ul> <li> **`urn:ioos:glider:wmo:4801902:20160218T1913Z`** <li>**`urn:ioos:station:us.glos:45024`** </ul> <br>**NOTE:** interchangeable with **`platform_variable:short_name`** | variable | required
platform_variable:long_name | NODC Templates | Provide a descriptive, long name for this variable. | variable | required
platform_variable:short_name | IOOS | Provide a short name for the platform.  Similar to ID, a **`short_name`** can be any unique string of characters that does not include blanks. <br><br>Examples: <ul> <li> **`station_1:short_name = “carquinez”`** <li>**`station_1:short_name = “cb0102`** </ul> <br>**NOTE:** interchangeable with **`platform_variable:ioos_code`** | variable | required
platform_variable:type | IOOS | In  conjunction with a **`platform_vocabulary`** attribute, identifies platform's type as defined in the [IOOS Platform Categories vocabulary](https://mmisw.org/orr/#http://mmisw.org/ont/ioos/platform), or [SeaVoX Platform Categories vocabulary](http://vocab.nerc.ac.uk/collection/L06/current/"), or any other vocabulary. The URL of the actual vocabulary must be published in the **`platform_vocabulary`** global attribute. <br><br>Alternatively, the **`platform`** and **`platform_vocabulary`** pair of attributes may be used; however, this option is not recommended (see details in the **`platform_vocabulary`** description.) | variable | required
platform_vocabulary | ACDD 1.3<br>(NCEI Templates v2.0) | Controlled vocabulary for the names used in the "platform" attribute.<br><br> It is recommended that this attribute is used in conjunction with the **`platform_variable:type`** attribute. In that case, the recommended value for the **`platform_vocabulary`** attribute is a URL to either the [IOOS Platform Category vocabulary](https://mmisw.org/orr/#http://mmisw.org/ont/ioos/platform), or [SeaVoX Platform Categories vocabulary](http://vocab.nerc.ac.uk/collection/L06/current/). <br><br>Example: **`platform_vocabulary = "https://mmisw.org/orr/#http://mmisw.org/ont/ioos/platform"`**<br><br>As an alternative (although not recommended), a NetCDF file may follow the NCEI Template v2.0, which suggests the use of "NASA GCMD Platform Keywords Version 8.1" string as the fixed value for the **`platform_vocabulary`**, and does not stipulate for the **`platform_variable:type`**. Instead, the actual type of the platform must be placed in the global **`platform`** attribute as described in the Science Keyword Rules (http://gcmd.nasa.gov/learn/rules.html) for NASA Global Change Master Directory (GCMD) Keywords (http://gcmd.nasa.gov/learn/keywords.html). <br><br>Example: **`platform: In Situ Ocean-based Platforms > MOORINGS`** | global | required
publisher_address | IOOS | Street address of the person or organization that distributes the data.   | global | recommended
publisher_city | IOOS | City of the person or organization that distributes the data.   | global | recommended
publisher_country | IOOS | Country of the person or organization that distributes the data.   | global | required
publisher_email  | ACDD | The email address of the person or group that distributes the data files. | global | required
publisher_name  | ACDD | Name of the person or group that distributes the data files. Use the conventions described above when identifying persons and/or institutions when applicable. | global | required
publisher_phone | IOOS | The phone number of the person or group that distributes the data files.  | global | recommended
publisher_state | IOOS | State of the person or organization that distributes the data.   | global | recommended
publisher_url  | ACDD | URL of the person or group that distributes the data files. | global | recommended
publisher_zipcode | IOOS | ZIP code of the person or organization that distributes the data.   | global | recommended
standard_name_vocabulary  | ACDD | Standardized field which uses the [CF Standard Names](http://www.cfconventions.org/documents.html/). If a variables does not have an existing standard_name in the CF-managed list, this attribute should not be used. In these cases, a standard name can be proposed to the CF community for consideration and acceptance. | global | required
summary  | ACDD | One paragraph describing the data set. |  global | recommended
title  | ACDD | One sentence about the data contained within the file. | global | required
units  | CF | Required for most all variables that represent dimensional quantities. The value should come from [**`udunits`**](http://www.unidata.ucar.edu/software/udunits/) authoritative vocabulary, which is documented in the CF standard name table with it's corresponding standard name. The **`udunits`** package includes a file `udunits.dat` which lists its supported unit names. | variable | required
<br>



<!---







<dl>
<dt><b>Conventions</b>:</dt>
<dd>
Version of the <a href="http://cfconventions.org/">Climate and Forecast metadata conventions</a> followed by the file format specification.
</dd>
<dd>
<b>Value</b>: "CF-1.6"
</dd>

-->

<!--

#####<i>platform</i>#####
<dl>
<dd>
<table>
<tr><th><b>Dimension</b></th><td>None</td></tr>
<tr><th><b>Data Type</b></th><td>int</td></tr>
<tr><th><b>Value Type</b></th><td>Scalar</td></tr>
<tr><th><b>_FillValue</b></th><td>-999</td>
<tr><th><b>Description</b></th><td>Variable to store meta data about the glider platform that measured the profile.  All of the attributes of this variable, with the exception of <b>comment</b> are <b>REQUIRED</b>.  This variable contains a <b>wmo_id</b> attribute to store the <b>WMO ID</b> assigned to this glider by NDBC.  The <b>WMO ID</b> is also stored as a global file attribute to allow for aggregations of all deployments from the platform with that <b>WMO ID</b>.</td></tr>
</table>
</dd>
<dd>
<a href="https://www.unidata.ucar.edu/software/netcdf/docs/netcdf/Data-Model.html">CDL</a> example with <b>REQUIRED</b> attributes and comments on values:
<pre>
    int platform ;
		platform:_FillValue = -999 ;
		platform:comment = "Slocum Glider ru29" ; # Change
		platform:id = "ru29" ; # Change
		platform:instrument = "instrument_ctd" ;
		platform:long_name = "Rutgers University Slocum Glider ru29" ; # Change
		platform:type = "platform" ;
		platform:wmo_id = " " ; # WMO ID specific to this glider
</pre></dd>
</dl>

-->
