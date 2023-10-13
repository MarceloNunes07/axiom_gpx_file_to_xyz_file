# axiom_gpx_file_to_xyz_file
Step-by-step guide on how to use Track information registered on a Raymarine Axiom MFD to build a XYZ file, which may be used to prepare a personal non-oficial bathymetric map, specially for non-surveyed areas or for regions with outdated survey

Important: this method has limitations and it is not intended to replace a formal survey process, which is executed with much higher degree of accuracy. On the other hand, the formal method is generally very expensive, being not feasible in some instances. The present process is therefore recommended if you have a particular area that has either no bathymetric information, or for regions with outdated survey (more common in developing countries). The outcomes must be used with caution, and we recommend that you consider adding some margin of safety to the final results (they will be more reliable in sheltered regions, where boat movements due to the waves' action are reduced).

The full process is divided into three major parts:
1. Collecting the data and saving it on a MicroSD as a GPX file.
2. Using the Pyhton algorithm to extract details from the GPX file, in order to prepare do XYZ file. This stage will also consider the boat's draft and the tidal information during the "Survey"
3. Use the XYZ file with a GIS Software (e.g. QGIS) to create your bathymetric map.


- The first stage will be conducted on board your boat:
a) sail towards the place you intend to register the depth data.
b) On your AXIOM MFD, having a MicroSD on it, go to Home >> My Data >> Tracks
c) Choose the "time" option and set the interval to "2 seconds".
d) Select "Start Track"
e) Register the exact time you are starting the survey process, because the GPX file has no timestamp information. We will need this later, in order to consider the tidal information for calculating the real depth.
f) Sail through the desired region, if possible at low speeds and trying to follow paralell paths.
g) Select "Stop track"
h) On your AXIOM MFD, go to Home >> My data >> import/export >> Button "Save my data" >> Save tracks (choose the track you have just registered)
i) Select Eject card to safely remove the memory card
j) Remove your MicroSD from your AXIOM MFD and copy the file to your personal notebook. Then return the MicroSD to your AXIOM MFD.

- Having your GPX file, you will be able to use the python algorithm to extract the desired details. You will also need the time you have started your survey (t0); your boat's draft (vertical distance between your transducer and the waterlevel); and the tide information between t0 and tn (n is the number of observations. By using the script, you will receive as outcome the XYZ file, that can be used in a GIS software to prepare a map.

- Import the XYZ file to a GIS software, such as QGIS, and use it as a base for building bathymetric map for your region of interest. When importing the file, you have to define the X and Y columns as the geographic coordinates, and Z as the feature that will be used for the maps (interpolation methods may be used) 
