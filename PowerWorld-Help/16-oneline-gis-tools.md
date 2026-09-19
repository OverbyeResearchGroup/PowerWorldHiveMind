---
title: "Oneline GIS Tools"
part: "Oneline Diagrams"
chapter_file: "16-oneline-gis-tools.md"
topics: 17
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Oneline GIS Tools

GIS tools, geographic data views and coordinate handling.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (17)**

- [Map Projections](#map-projections)
- [Great Circle Distance Dialog](#great-circle-distance-dialog)
- [Great Circle Distance Calculation](#great-circle-distance-calculation)
- [Populate Lon,Lat with Display X,Y](#populate-lonlat-with-display-xy)
- [Geography/Coordinates](#geographycoordinates)
- [Shape File Import](#shape-file-import)
- [GIS Shapefile Data: Control](#gis-shapefile-data-control)
- [GIS Shapefile Data: Identify](#gis-shapefile-data-identify)
- [GIS Shapefile Data: Modify](#gis-shapefile-data-modify)
- [GIS Shapefile Data: Format](#gis-shapefile-data-format)
- [GIS Shapefile Data: Shape List](#gis-shapefile-data-shape-list)
- [Shapefile Database Record Dialog](#shapefile-database-record-dialog)
- [Export Oneline As Shapefile](#export-oneline-as-shapefile)
- [Insert Measure Line](#insert-measure-line)
- [Delete All Measure Lines](#delete-all-measure-lines)
- [Path Distances from Bus or Group](#path-distances-from-bus-or-group)
- [Closet Facilities to Point](#closet-facilities-to-point)

---

<a id="map-projections"></a>

## Map Projections

*Source: [`Content/MainDocumentation_HTML/Map_Projections.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Map_Projections.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Background on Map Projections

In order to create a map of a spherical object such as the Earth it is first necessary to convert the Earth coordinates of latitude and longitude into a two-dimensional coordinate system needed for a map. This conversion from the spherical coordinates of latitude and longitude to some xy Cartesian coordinate system is called a *map projection*. Mapmakers and mathematicians throughout history have invented many map projections. For each map, the mapmaker must decide which projection will look best for his or her purposes. This will depend on what part of the globe is being drawn, the size of the area being drawn, and the shape of the object being drawn. In general, map projections fall into three standard classes: cylindrical, conical, and planar. For a complete analysis of the topic of map projections see reference 1.

For maps of North America, PowerWorld supports a Simple Conic map projection which is described below.

For maps of the entire Earth, PowerWorld supports a Mercator projection which is described below.

Simple Equidistant Conic Map Projection

For maps made of the 48 conterminous states in the United States, maps are often made using one of the conical map projections. These projections can be recognized by the constant latitude lines that are seen as arcs. When looking at the U.S./Canadian border in the western United States, you will see that it curves on maps made using a conical projection, even though this is a constant latitude border. Several conical projections exist including the Albers Equal-Area Projection, Lambert Conformal Projection, and Simple Equidistant Projection. They can be visualized as taking the globe and placing a cone over it as shown in Figure 1 and then using this to map the coordinates to the xy plane shown at the right. Constant longitude lines are seen as straight lines and constant latitude lines are seen as arcs on the resulting map.

![Map Projections Figure1 664x357](images/Map_Projections_Figure1_664x357.jpg)

The equations for converting back and forth between (longitude,latitude) and (x,y) using the simple equidistant projection are described next. These equations are taken from reference 1.

First, you must specify seven values that are parameters of the mapping:

![Map Projections Equation1](images/Map_Projections_Equation1.gif)

For these values, the following variables are defined:

![Map Projections Equation2](images/Map_Projections_Equation2.gif)

Then given a latitude = ϕ and a longitude = λ, calculate the x and y coordinate using

![Map Projections Equation3](images/Map_Projections_Equation3.gif)

And given an x and y coordinate, calculate the latitude(ϕ) and longitude(λ) using

![Map Projections Equation4](images/Map_Projections_Equation4.gif)

Figure 2 shows more clearly what some of these variables are.

![Map Projections Figure2](images/Map_Projections_Figure2.gif)

Albers Conic Equations:

The equations for converting back and forth between (longitude,latitude) and (x,y) using the simple equidistant projection are described next. These equations are taken from reference 1.

First, you must specify seven values that are parameters of the mapping:

![Map Projections Equation1](images/Map_Projections_Equation1.gif)

For these values, the following variables are defined:

![Map Projections Equations A2 562x95](images/Map_Projections_Equations_A2_562x95.gif)

Then given a latitude = ϕ and a longitude = λ, calculate the x and y coordinate using

![Map Projections Equations A3 204x171](images/Map_Projections_Equations_A3_204x171.gif)

And given an x and y coordinate, calculate the latitude(ϕ) and longitude(λ) using

![Map Projections Equations A4 258x246](images/Map_Projections_Equations_A4_258x246.gif)

Maps made using PowerWorld's built-in map borders for North America use the following parameters:

![Map Projections Equation5](images/Map_Projections_Equation5.gif)

These numbers were thus set to be the default map projection numbers within PowerWorld. This projection will work well for the one-line diagrams with PowerWorld Corporation has created on the same standard background.

Mercator Projection Use in PowerWorld

For the Mercator Projection, PowerWorld assumes R = 30700.0 units. From this, given a latitude = ϕ and a longitude = λ, calculate the x and y coordinate using

![Map Projections Equation6](images/Map_Projections_Equation6.gif)

And given an x and y coordinate, we calculate the latitude(ϕ) and longitude(λ) using

![Map Projections Equation7](images/Map_Projections_Equation7.gif)

References

1.  Snyder, John P., Map Projections - A Working Manual, U. Geological Survey Professional Paper 1395, United States Government Printing Office, Washington, D.C.: 1987.

---

<a id="great-circle-distance-dialog"></a>

## Great Circle Distance Dialog

*Source: [`Content/MainDocumentation_HTML/Great_Circle_Distance_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Great_Circle_Distance_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To find the Great Circle Distance between any two points of longitude, latitude, select **GIS Tools \>** **** **Great Circle Distance** from the **[Active](02-simulator-ribbon.md#active-ribbon-group)** ribbon group on the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab and the Great Circle Distance Dialog will be displayed. This can be done in Edit or Run Mode.

The Great Circle Distance Dialog allows the calculation of distance between two points of longitude, latitude. The [Great Circle Distance Calculation](#great-circle-distance-calculation) assumes that the earth is a sphere and makes no adjustments for the actual flattening of the earth. The two longitude, latitude points can either be entered manually for any two valid points or can be chosen from valid longitude, latitude values stored with either buses or substations. Valid longitude values are between -180 and 180 degrees. Valid latitude values are between -90 and 90 degrees. The calculated distance is given in either kilometers or miles.

From Location

Click the **Choose From Location** button to choose either the location of a bus or substation as the **From Location**. The **Latitude (degrees)** and **Longitude (degrees)** entries for the From Location will be filled in with the latitude, longitude information that is stored with the chosen element in the case data. These entries are not based on the location of a display object, if one exists, of the chosen element. If the element does not have valid geographic information stored, the values that are entered for the latitude, longitude will not be valid.

The Latitude, Longitude entries can also be entered manually.

To Location

Click the **Choose To Location** button to choose either the location of a bus or substation as the **To Location**. The **Latitude (degrees)** and **Longitude (degrees)** entries for the To Location will be filled in with the latitude, longitude information that is stored with the chosen element in the case data. These entries are not based on the location of a display object, if one exists, of the chosen element. If the element does not have valid geographic information stored, the values that are entered for the latitude, longitude will not be valid.

The Latitude, Longitude entries can also be entered manually.

Units

Choose the units in which to report the calculated distance.

Calculate Distance

Click this button to calculate the distance in the chosen Units between the From Location and the To Location. The calculated distance will appear in the box above the button. *Error in input data* will be returned if there is a problem with any of the latitude, longitude information.

---

<a id="great-circle-distance-calculation"></a>

## Great Circle Distance Calculation

*Source: [`Content/MainDocumentation_HTML/Great_Circle_Distance_Calculation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Great_Circle_Distance_Calculation.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Great Circle Distance Calculation allows the calculation of distance between two points of longitude, latitude. The Great Circle Distance Calculation assumes that the earth is a sphere and makes no adjustments for the actual flattening of the earth.

The calculation consists of the following parameters:

![Great Circle Distance Calculation Equation1](images/Great_Circle_Distance_Calculation_Equation1.gif)

The distance in kilometers between the starting and ending location is determined from the following equation:

![Great Circle Distance Calculation Equation2](images/Great_Circle_Distance_Calculation_Equation2.gif)

This calculation is used with several GIS tools to determine the distance between two locations or facilities on a diagram.

---

<a id="populate-lonlat-with-display-xy"></a>

## Populate Lon,Lat with Display X,Y

*Source: [`Content/MainDocumentation_HTML/Populate_Lon_Lat_with_Display_X_Y.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Populate_Lon_Lat_with_Display_X_Y.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To populate the longitude,latitude fields of buses and substations with the locations of corresponding display objects converted to longitude,latitude using the selected projection, go to the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, then on the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group choose **GIS Tools \> Populate Lon,Lat with Display X,Y**. 

The Populate Lon,Lat with Display X,Y Dialog will be displayed.  This can be done in either Edit or Run Mode.  The dialog will show which map projection is currently in use for the oneline.  Users should be careful to not change the map projection once one has been established so that all objects on the oneline are consistently using the same projection.  If no projection has been set, the dialog shows **None (x,y)** as the Map Projection, selecting a map projection will establish that map projection as the current oneline map projection. 

**[Map Projection](#map-projections)**

**None (x,y)**

No map projection is in use. 

**North American (simple conic)**

This projection is better when dealing with longitude, latitude points in North America.  This is the projection that has been used in Simulator for years in defining geographic borders and placing then on a oneline.

**Entire World (Mercator)**

This projection is better when dealing with longitude, latitude points spread throughout the world.

**Alaska (Albers Conic)**

This projection is better when dealing with longitude, latitude points spread in Alaska.

Click **Populate Longitude,Latitude** to complete the conversion.  The longitude, latitude values converted from display x, y coordinates can be viewed on the bus and substation case information displays or the information dialogs.

---

<a id="geographycoordinates"></a>

## Geography/Coordinates

*Source: [`Content/MainDocumentation_HTML/Geography_Coordinates.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Geography_Coordinates.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The option is available to display screen coordinates in longitude, latitude instead of x,y. This option can be set by selecting **Oneline Display Options** from the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab or the [Options](02-simulator-ribbon.md#options-tab-overview) ribbon tab. The following options are located under the **Geography/Coordinates** category.

[Map Projection](#map-projections) in Use

The map projection indicates which projection has been selected for inserting objects on the oneline. Users should be careful to not change a projection once one has been established. Otherwise, there is the risk that different objects will be inserted with different projections.

Show longitude, latitude coordinates when showing x, y coordinates

When this option is checked and a map projection other than *None (x,y)* is selected, longitude, latitude coordinates will be displayed anywhere that x,y screen coordinates are normally displayed. This option will only be enabled when a map projection other than *None (x,y)* has been selected.

---

<a id="shape-file-import"></a>

## Shape File Import

*Source: [`Content/MainDocumentation_HTML/Shape_File_Import.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Shape_File_Import.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator allows you to import ESRI shapefiles (\*.shp/\*.dbf pairs) as a group of background lines or points on a oneline diagram. There are several locations where you may open the GIS Shapefile Import Dialog.

  - Go to the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, then on the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group choose **GIS Tools \> **Insert GIS Data from Shapefile****.
  - Go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, then on the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group choose **Background \> Insert GIS Data from Shapefile**
  - Go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, then on the [Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group) ribbon group choose **Auto Insert \> Insert GIS Data from Shapefile**

The GIS Shapefile Data Dialog has the following sections:

[Control](#gis-shapefile-data-control)

[Modify](#gis-shapefile-data-modify)

[Identify](#gis-shapefile-data-identify)

[Format](#gis-shapefile-data-format)

[Shape List](#gis-shapefile-data-shape-list)

---

<a id="gis-shapefile-data-control"></a>

## GIS Shapefile Data: Control

*Source: [`Content/MainDocumentation_HTML/GIS_Shapefile_Data_Control.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GIS_Shapefile_Data_Control.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This is the first page of the [GIS Shapefile Data](#shape-file-import) dialog. The control page contains the controls for reading a shapefile into Simulator and provides some basic information on the shapes read from the file.

Read in Shapefile

Pressing this button will allow you to choose a shapefile and will load it into Simulator for placement on the currently selected oneline diagram.

Save Shapefile

Clicking this button will save to file the shapefile information currently loaded in memory. This option is useful if making changes to shape format attributes or eliminating certain shapes from those read in and then saving these changes in the shapefile format.

Shapefile Information

Once the shapefile has been loaded into memory, this section will be populated with general information on the number of shapes loaded, and the maximum and minimum X and Y values (usually in longitude and latitude.)

Transfer Shapefile Objects to Oneline

If you are ready to place the shapes on the oneline diagram, but want to continue working with existing shapes or read more shapes from another file, press the **Transfer Shapes to Oneline and Clear** button. This will keep the dialog open following the transfer. It also gives you options of what should happen to the current shapes in memory after you have transferred them to the diagram. You can choose to clear only the shapes that were transferred, all of the shapes, or none of the shapes. The first choice relates to options you have on the [Shapefile Objects](#gis-shapefile-data-shape-list) page regarding whether or not to transfer certain shapes from the shapefile to the diagram.

Insert Into Layer

Before transferring the shapes to the oneline diagram, you can choose which [layer](14-editing-onelines.md#screen-layers) the shapes should be assigned to. If you wish to place the shapes into a new undefined layer, click on the **Define Layer** button to access the [Screen Layers](14-editing-onelines.md#screen-layers) table.

Transfer Shapes to Oneline and Close

If you wish to transfer the currently loaded shapes to the oneline and close the dialog (clearing the shapes from memory), press this button to complete the process.

---

<a id="gis-shapefile-data-identify"></a>

## GIS Shapefile Data: Identify

*Source: [`Content/MainDocumentation_HTML/GIS_Shapefile_Data_Identify.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GIS_Shapefile_Data_Identify.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

After using the [Control](#gis-shapefile-data-control) page to read in shapes from a shapefile but before placing them on the diagram, identification options can be specified on the Identify page.

Identification String for Display Auxiliary Files

Shapefile shapes are created as background objects when added to a diagram. If using [display auxiliary files](03-cases-files-and-formats.md#auxiliary-file-format-aux) to create or edit diagrams, objects must be uniquely identified. Because background objects typically do not link to an object in the power flow case, and therefore have no other unique means of identification, a unique ID string must be assigned to objects created via shapefiles. This unique identifier populates the **Auxiliary ID** field used in [display auxiliary files](03-cases-files-and-formats.md#auxiliary-file-format-aux) and can be viewed from the [Display Explorer](15-using-onelines-tools-and-options.md#display-objects-case-information-display).

Prefix 

Optionally, a prefix can be concatenated with the selected Attribute to further identify the shape.

Attribute

The drop-down box is populated with the fields that are available with the .dbf file. Choose a field whose value will be used to uniquely identify the shape. By default, the *Record Number* of the shape is used for identification if no other Attribute is selected.

Suffix

Optionally, a suffix can be concatenated with the selected Attribute to further identify the shape.

Linkage to Supplemental Data

Background objects created from shapefiles can be linked to [Supplemental Data](15-using-onelines-tools-and-options.md#supplemental-data) records for purposes of further identifying the objects. This is useful when applying filters, applying dynamic formatting, using Select By Criteria, or defining custom hints with display objects created from shapefiles.

Link Display Objects to Supplemental Data

Check this box to link the background objects created from shapefile shapes to Supplemental Data records.

Supplemental Classification

Select an existing Supplemental Classification from the drop-down box or click **New** to create a new Supplemental Classification.

Attribute for Supplemental Data Name

Select an Attribute from the drop-down box. The list of attributes is populated from the fields that are available in the .dbf file. For each unique Attribute value, a supplemental data record will be created with the chosen Supplemental Classification and with its Name set to the Attribute value.

---

<a id="gis-shapefile-data-modify"></a>

## GIS Shapefile Data: Modify

*Source: [`Content/MainDocumentation_HTML/GIS_Shapefile_Data_Modify_Shapes_or_Projection.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GIS_Shapefile_Data_Modify_Shapes_or_Projection.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

After using the [Control](#gis-shapefile-data-control) page to read in shapes from a shapefile but before placing them on the diagram, the Modify page can be used to modify the XY attributes of the shapes.

[Map Projection](#map-projections)

There are two map projections you can choose from when placing the shapes onto a oneline diagram. The choices are:

  - North American (simple conic)
  - Entire World (Mercator)

Once you have selected which projection to use, click on the **Convert to Specified Map Projection** button to process the conversion on the shapes currently in memory.

Shift/Scale Shapefile X/Y Data

You also have the option to shift the XY coordinates of shapes or scale them by scalar values. To shift shapes, enter scalar shift values for the X value and Y value and press the **Shift XY Data** button. To scale the XY coordinates, enter scalar scaling factors for the X and Y value, and press the **Scale XY Data** button.

---

<a id="gis-shapefile-data-format"></a>

## GIS Shapefile Data: Format

*Source: [`Content/MainDocumentation_HTML/GIS_Shapefile_Data_Modify_Colors_and_Format.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GIS_Shapefile_Data_Modify_Colors_and_Format.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

After using the [Control](#gis-shapefile-data-control) page to read in shapes from a shapefile but before placing them on the diagram, the Format page can be used to modify the appearance attributes of the shapes.

Change Shape Format Characteristics

**Point Size**

The size of points read from the shapefile can be adjusted when transferred to the oneline diagram.

**Line/Border Thickness**

Choose the pixel thickness of the shapefile lines when transferred to the oneline diagram.

**Line/Border Color**

Set the line color of the shapefile lines when transferred to the oneline diagram.

**Fill Color for Points/Polygons**

Set the fill color of the shapefile points and polygons when transferred to the oneline diagram. The box labeled **Use Fill Color** must be checked as well.

**Stack Level**

Indicate which [stack level](14-editing-onelines.md#levelslayers-options) should be applied to the shapes when they are transferred to the oneline diagram.

**Immobile**

Check this box if you wish for the shape file objects to be immobile once they are transferred to the oneline diagram. This will prevent you from inadvertently selecting and moving the shapefile objects on the oneline diagram while in [Edit mode](01-getting-started.md#edit-mode-introduction).

**Set all shape format attributes to the values above**

Once you have finished changing the format settings for the shapes, press this button to apply them for the transfer of shapes to the oneline diagram.

Automatic Color Mapping

**Available Attributes**

To customize the shapefile shapes based on a field value read from the .dbf file, select an attribute from the list.

**Color Map**

Select a color map to apply to the selected attribute. To modify existing or create new color maps, click on the **Modify Color Maps** button. The color of the object will then be based on where its selected attribute value maps to the selected color map.

**Change Border Color, Change Fill Color**

These two boxes allow you to choose if the color map selected should apply to the border color, the fill color, or both.

**Change Color Based on Attribute/Color Map**

Once you have finished setting the color map for a selected attribute, press this button to apply the settings before the transfer of shapes to the oneline diagram.

---

<a id="gis-shapefile-data-shape-list"></a>

## GIS Shapefile Data: Shape List

*Source: [`Content/MainDocumentation_HTML/GIS_Shapefile_Data_Shapefile_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GIS_Shapefile_Data_Shapefile_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

After using the [Control](#gis-shapefile-data-control) page to read in shapes from a shapefile but before placing them on the diagram, the Shape List page can be used to flag shapes for inclusion in the transfer and customize the appearance attributes of specific shapes.

This page will be blank until you have actually read a shapefile into memory. Once you have done so, you will see a list of all shapes read from the file. The table allows you to customize the appearance and attributes of a specific shape, similar to the options on the [Format](#gis-shapefile-data-format) page.

In addition, you also can choose to include or exclude shapes from the transfer to the oneline diagram. This gives you the greatest flexibility for hand-picking which shapes you want to add to a oneline diagram.

---

<a id="shapefile-database-record-dialog"></a>

## Shapefile Database Record Dialog

*Source: [`Content/MainDocumentation_HTML/Shapefile_Database_Record_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Shapefile_Database_Record_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Shapefile Database Record dialog is available by selecting **Show Shapefile Fields…** from the local popup menu (obtained by right-clicking on a display object) of any display object that was created from a shapefile. This menu option will not be available for display objects that were not created from a shapefile. This dialog provides information read from the database file (.dbf) associated with the shapefile from which the display object was created. Each time that this dialog is displayed, the database file is read to fill in the field information. The field information is not stored in the PowerWorld display file (.pwd) so the associated database file must be available for this information to be displayed.

File Name

This is the path and name of the database file (.dbf) associated with the shapefile from which the display object was created.

Record Number

This is the record number of the display object within the shapefile.

List of Fields

This list details the fields and values belonging to the given record number in the database file.

Edit Oneline Browsing Path

Select this option to update the Oneline Browsing Path. This browsing path will be used to search all listed directories for the database file specified in File Name if it cannot be found in the directory specified with the File Name.

---

<a id="export-oneline-as-shapefile"></a>

## Export Oneline As Shapefile

*Source: [`Content/MainDocumentation_HTML/Export_Oneline_As_Shapefile.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Export_Oneline_As_Shapefile.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Display objects can be exported into shapefile formats (.shp/.dbf pairs) by going to the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, then in the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group, choosing **GIS Tools \>  Export Oneline as Shapefile**.**** This will open the Select Objects and Fields to Export Dialog, which is similar to the Select by Criteria Dialog.

The dialog is used to select one type of display object to export to the shapefile and the criteria used to select which specific objects will be included in the export.

**Selecting Areas and Zones**

Use the **Area** and **Zone** fields to select the areas and zones in which to select display objects. [Ranges](04-model-explorer-and-case-information-part3.md#entering-a-range-of-numbers) of area and zone numbers can be entered in the usual way, or the **All Areas** or **All Zone** boxes can be checked to select all areas and all zones respectively. The **Areas** and **Zones** tab pages can also be used to select the areas and zones in which to select display objects.

Selecting Voltage Levels

Specify the max and min voltage levels using the boxes that are provided, keeping in mind that all voltages are in kV. The **All Voltages** box **** can be checked to include all voltages without requiring the specification of a voltage range.

Selecting Layers

All layers **** can be selected by choosing the **All** option for Layers. If specific layers are to be selected, the **Range** option should be selected and the **Layers** tab should be used to check and uncheck specific layers in which to select display objects.

Type of Drawing Object

Select the type of object to export in the **Type of Drawing Object** dropdown box. Alternatively, the **Find…** button next to the dropdown can be used to select the object type from a list of available object types.

Filter

The **Filter** dropdown box provides a list of filters available for the selected Type of Drawing Object. The **Find…** button next to this dropdown can be used to find a filter or define a new filter for the selected object type. Filter options will not be enabled when an object type that does not allow filtering is selected.

Selecting Fields

The **Fields** list will be populated for object types that have associated fields. The selected fields will be written to the database file (.dbf) along with the value of the field. When the **Specified** option is selected, individual fields can be chosen by checking the box next to specific fields. When the **All** option is selected, then all fields associated with the selected type of object will be included in the database file. When the **Show Only Commonly Used Fields** option is checked, only those fields that are deemed to be commonly used will be displayed in the list. To show all fields associated with the selected object type, uncheck this box. Use the **Check All** and **Uncheck All** buttons to check all or uncheck all of the fields.

Advanced Selection Criteria

If only objects that are currently visible on the display (due to layering, etc.) are to be selected, check the box labeled **Select only currently visible objects.** If some display objects have been selected prior to opening the dialog, an advanced selection option becomes available. If the box labeled **Use as a filter on presently selected objects** is checked, the criteria chosen in the dialog will only affect the previously selected objects. In other words, only the objects that were previously selected AND that match the chosen criteria will remain selected when exporting to the shapefile.

Export Coordinates in Longitude,Latitude

If a valid map projection has been selected for displaying display object coordinates in longitude,latitude, then the option to **Export coordinates in longitude,latitude** will be enabled. (A valid map projection can be set with the Map Projection in Use Option found in the [Geography/Coordinates](#geographycoordinates) category of the Oneline Display Options dialog.) By default, the Export coordinates in longitude,latitude option will be checked when it is enabled. When checked, the coordinates of the display objects will be exported to the shapefile in longitude,latitude instead of PowerWorld Simulator x,y coordinates.

Saving Shapefile Export Descriptions

Shapefile Export Description settings can be saved with the case by clicking **Save As** to save with a new name or **Save** to save with the current name. This will allow the quick recovery of settings that may have been previously used. Use the **Rename** button to rename an already saved set or the **Delete** button to remove a previously saved set of criteria. If Shapefile Export Description sets have been saved, they can be exported to an auxiliary file by choosing **Save to AUX file.** The **Load from AUX file** button will load an entire auxiliary file regardless of whether it contains Shapefile Export Descriptions or not.

Saving the Shapefile

After all criteria have been set, click **OK**. A dialog will open prompting for the name of the file to save. Enter a file name and click **Save.** The type of file that is specified in the dialog is a shapefile with .shp extension, however, three files will be saved. All files will have the name specified in the save dialog, but the extensions will be .shp, .dbf, and .shx.

---

<a id="insert-measure-line"></a>

## Insert Measure Line

*Source: [`Content/MainDocumentation_HTML/Insert_Measure_Line.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Insert_Measure_Line.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Distances between display objects can be approximated by inserting a measure line on the display. A measure line is similar to a background line. It can be drawn as a straight line between two points or as a line with many vertices and segments. By default, a measure line is drawn as a yellow line with a pixel thickness of 4.

To insert a measure line go to the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, then on the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group choose **GIS Tools \> Insert Measure Line**. Then position the mouse cursor on the display where the line should begin and click and release the left mouse button. Move the mouse to the desired termination point of the first line segment. A straight segment will follow the mouse movements. Click and release the left mouse button to complete the line segment and to prepare for drawing the next segment, or double-click if this is the last line segment. To draw a freehand shape rather than a series of straight line segments, click and hold the left mouse button where the freehand shape begins and drag the mouse to trace the desired shape (while holding the left mouse button down). Release the left mouse button to complete the section of the freehand shape. At this point, either another freehand section or a straight line segment can be added. When all desired freehand and straight line segments have been added, double-click the left mouse button to complete the line.

To change the shape of the line, first left click on the line to select it. Handles will appear at each vertex. A vertex can be moved by holding the left mouse button down and dragging the vertex to a new location. To remove a vertex, hold down the CTRL key and then click the vertex you would like to delete. To add a vertex, hold down the CTRL key and then click on the line where the new vertex should be added. Note that freehand lines are nothing more than a continuous series of vertices.

Once the measure line has been added to the display, the length of the line can be displayed by right-clicking on the line and selecting **Measure Length…** from the local menu. The units of the length are dependent on the map projection in use and whether the option to **Show longitude,latitude coordinates when showing x,y coordinates** is checked on the [Oneline Display Options dialog](#geographycoordinates). If the map projection in use is something other than *x,y* and the option to show longitude,latitude coordinates is checked, the length will be given in miles and kilometers. Otherwise, the length will be given in Simulator units. The [Great Circle Distance calculation](#great-circle-distance-calculation) is used to determine the distance between vertices on the line to determine the approximate length in miles and kilometers.

---

<a id="delete-all-measure-lines"></a>

## Delete All Measure Lines

*Source: [`Content/MainDocumentation_HTML/Delete_All_Measure_Lines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Delete_All_Measure_Lines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

All [measure lines](#insert-measure-line) can be deleted from the display. To do this go to the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, then on the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group choose **GIS Tools \>  Delete All Measure Lines**.

---

<a id="path-distances-from-bus-or-group"></a>

## Path Distances from Bus or Group

*Source: [`Content/MainDocumentation_HTML/Path_Distances_from_Bus_or_Group.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Path_Distances_from_Bus_or_Group.htm)*

To access the Determine Path Distances from Bus dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Connections \> Determine Path Distances to Bus** from the [Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group) ribbon group. The Determine Path Distances from Bus or Group dialog provides a way to calculate how far electrically every bus in the system is from a particular starting point.

After clicking the **Calculate** button, all buses that are part of the start element will be labeled internally as being a path distance zero. Then a calculation will be done that determines for *each bus* in the system the shortest total path length in getting from each bus to the Start Element. Buses that cannot reach the Start Element will be flagged with a very large distance (by default 10,000). The results of the calculation will then be copied into the Bus Field specified under the Bus Field to Populate option. The results will be displayed in a case information display at the bottom of the dialog.

The options on the dialog are described below.

Start Element Type and Element

Choose an element type to be either a Bus, Substation, Area, Zone, Super Area or Injection Group. Then use the object chooser to choose the particular object to be the starting element. For more help on the object choose see the [Find Dialog Basics](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Distance Measure

Choose the distance measure that will be used to determine distances between nodes. Each branch will be treated as having a length based on the choice below. Note: negative values are not allowed, therefore negative values will be treated as extremely small lengths instead.

**X** - Per unit series reactance.

**|Z|** - Magnitude of the series impedance (based on the per unit reactance and resistance).

**Length** - Length field for each branch.

**Number of Nodes** - Length of 1.0 is used for all branches.

**Other** - When choosing Other, click the **Find..** button to choose any numeric field of a branch.

Lines to Process

Regardless of the Distance Measure above, you can choose which branches allowed to be traversed when finding the shortest path.

**All** - All branches are allowed to be traversed.

**Only Closed** - Only branches that are presently closed can be traversed.

**Filter** - Only branches that meet the advanced filter specified can be traversed. Click **Define...** to choose or create and advanced filter.

**Selected** - Only branches whose Selected? field is set to *YES* can be traversed.

Bus Field to Populate

Choose a field into which the resulting path distances will be copied. It is recommended that you use the custom floating point or integer fields for this purpose.

---

<a id="closet-facilities-to-point"></a>

## Closet Facilities to Point

*Source: [`Content/MainDocumentation_HTML/Closest_Facilities_To_Point.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Closest_Facilities_To_Point.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To produce a list of display objects and their distance from a point selected on the one-line diagram, go to the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, then on the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group choose **GIS Tools \> Closest Facilities to Point**. After selecting this option, the mouse cursor will become a crosshair. Move the cursor to a location on the diagram and left-click. A dialog will open listing all of the display objects and their distance from the selected point in ascending distance from the point.

Select to Show Display Objects of Type

This allows the option of showing all display objects in one list or only listing objects of a particular type.

Distance

This field is listed by default with the display objects. This shows the distance between a given display object and the selected point. The location of the selected point is given by the **X/Longitude** and **Y/Latitude** fields on the dialog. The location of a given object is provided by the **X/Longitude Location** and **Y/Latitude Location** fields with the display object. The units of the distance is given in the Units field on the dialog.

X/Longitude and Y/Latitude

Each display object listed has a corresponding **X/Longitude Location** and **Y/Latitude Location** field. The **X/Longitude** and **Y/Latitude** fields given on the dialog provide the location of the point that was selected on the diagram. The fields on the dialog can also be manually adjusted to determine the distance between the display objects and a given coordinate.

All of the fields that give the location of either the display object or the point selected on the diagram are given in x,y coordinates if a valid map projection is not selected or the option to show coordinates in longitude, latitude is not selected. Otherwise, the coordinates will be longitude, latitude. Both of these options can be set from the Oneline Display Options dialog in the [Geography/Coordinates](#geographycoordinates) category.

Units

This indicates the units that the distance is in. The units will be in PowerWorld units if a valid map projection is not selected or the option to show coordinates in longitude, latitude is not selected. Otherwise, the units will be in either miles or kilometers. To display the distance in miles, the option to use the *English* **Measurement System** must be selected on the PowerWorld Simulator Options dialog under the [Environment](10-power-flow-solution-and-options-part2.md#environment-options) category. Select **Metric (SI)** as the Measurement System to display the distance in kilometers.

Recalculate Distances

Click this button to recalculate distances after changing the coordinates of the selected point by entering new values for the X/Longitude or Y/Latitude fields.
