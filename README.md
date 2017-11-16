# Solar-Energy-Calculator-Tool-for-Building-Facades
This is an ArcScene add-on tool for calculating solar energy on building facades in city sclae. The tool calculate incident solar radiation based on two input feature: building footprint polygon and a Digital Terrain Model (DTM) or Digital Surface Model (DSM). The outputs on the other hand are 3D point feature (points on building façade representing certain area of the wall), 2D line feature representing single facade of building and 3D polygon feature representing the total facade area of building. 

## Software Requirements
This tool has been developed using VB.NET as an add-on for ArcGIS 10 or above. Since the outputs of the tool are 3D, ArcScene has been chosen as a target platform for the implementation of the tool. The ArcObjects (set of platform-independent software components of ArcGIS, written in C++) has been used extensively for the development of the tool.

## Installation
Please copy the directory "Help" to C:\. Double click on the "Multipatch solar radiation" ersi addin file and follow the instruction. After installation open the ArcScene then go to Customize>Add-in Manager>customize>Commands>Add-In Controls and drag the "Multipatch Solar Radiation" from commands box to somewhere in the ArcScene menu bars.

## Description of the GUI
A snap shot of the tool GUI is given in the following figure. Rectangles with red and green colour shows the initial (red rectangle) and extended interface (green rectangles) of the tool. The initial GUI (red rec-tangle area) is shown once the user clicks on the specified button on the ArcScene GUI. The initial GUI has options that must be fulfilled to run the tool. The user has to mention at least the input features, minimum one output feature and the time dura-tion for which the insolation would be calculated. All these inputs and parameter can be set by the initial GUI area. The green rectangle area just below the red rectangle is an ex-tended optional area of the tool GUI which can be activated by clicking on the “<<Other optional settings” label. Here the user can tune some default spatial, topographic or radia-tion parameters for calculating the insolation. Another extended area is the green rectangle area on the right hand side of red rectangle. This particular area is provided to give help for each option in the tool GUI and therefore could be activated and deactivated by the user by pressing the button “Show help” and “Hide help”. Detail description of each input, output and parameters in the tool GUIL are given in the following sections.

![](https://github.com/Md-ImranHossain/Solar-Energy-Calculator-Tool-for-Building-Facades/blob/master/Pics/Capture.PNG)

### Section for feature input
A polygon shape file of the urban objects (mostly of the case: buildings) with height attribute and a raster format of Digital Elevation Model (DEM) of the area should be provided in the "Input Feature" section of the GUI. The DEM could be of type Digital Terrain Model (DTM) or Digital Surface Model (DSM).

### Section for specifying output features
The tool can provide up to three different outputs shape file of global radiation as well as three different optional output shape file in a single run. 

The main output of the tool is a 3D point shape file. All other outputs in global radiation output section are calculated by 3D point output. The tool calculates incoming global solar radiation for regular spaced 3D points on build-ing facades. The user can control the spacing between points. The output has units of watt hours per square meter (Wh/m2).

The next output is a 2D line feature class/ shape file. In this case the calculated incoming radiation for each facade is assigned to values in line features representing each building façade. The output has units of watt hours per square meter (Wh/m2).

The third output is a 3D polygon shape file. The tool calculates total solar incoming radiation and intensity for each building (excluding building roof) and assigns the values in the polygon features representing each building. 

Additionally, the tool can provide up to three optional outputs: a 3D point shape file containing measurement of only direct radiation for every point, a 3D point shape file containing measurement of only diffuse radiation for every point and a 3D point shape file containing measurement of duration for direct radiation for every point. The duration means total time of sun visibility for a particular 3D point. 

Time plays an important factor for calculating the insolation. The amount of solar insolation is varying significantly for different season, month and even within a day. The GUI offers various possibilities to specify time duration. To include all possible time intervals three options are given by which a user can specify a particular time interval for solar insolation calculation.

### Optional parameter settings
Optional parameter settings are given in the extended area of the tool interface and there-fore can be enable by clicking on the ‘<<Other optional settings’ label. This particular section of the GUI is designed for modifying some default spatial, topographic and radiation parameters which are needed for insolaiton calculation. 

Spatial parameters

Ooutput point resolution: this parameter defines the spacing between each 3D point (output) in vertical and hori-zontal direction. 
Latitude: for input feature containing a spatial reference, the mean latitude is automatically calcu-lated; otherwise, latitude will be taken with a default value of 45 degrees
Height offset: defines the height (in meters) above the DEM surface for which calculations are to be per-formed. The height offset is usually applied to all 3D points
Sky size: The parameter defines resolution or sky size for the viewshed, sky map, and sun map grids. The units are cells. The default creates a raster of 200 x 200 cells

Topographic parameters
Z factor:is to adjusts the units of measure for the z units (the height attribute in the input polygon) when they are different from the x,y units
Slope and Aspect input type: provide information to the program about how slope and aspect information should be derived for each 3D point for analysis
Calculation direction: provides information to the algorithm regarding the number of azimuth directions to be used when calculating the viewshed

Topographic parameters
Zenith division: specifies the number of divisions in zenith direction to be used to create sky sectors in the sky map. The default is eight divisions (relative to zenith). Values must be greater than zero and less than half the sky size value.
Azimuth division: specifies the number of divisions in azimuth direction to be used to create sky sectors in the sky map
Diffuse model type: gives information to the algorithm about the type of sky for the time duration of solar in-solation calculation.
Diffuse proportion: the proportion of global normal radiation flux that is diffuse is specified
Transmittivity:The amount of solar radiation that is received by the surface is only a portion of what would be received outside the atmosphere 



