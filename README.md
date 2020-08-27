# SLEUTsH
This contains modifications in the source code of the SLEUTH Urban Growth Model to consider railway-induced urban growth.

SLEUTsH is a branch from the SLEUTH source code downloaded from http://www.ncgia.ucsb.edu/projects/gig/index.html
The "s" inserted between "T" and "H" means that an additional input layer is needed to determine locations of stations and their surroundinf buffers.
Details of this model can be found in the paper: https://www.mdpi.com/2071-1050/12/17/6801

From the commit description, labels are written which files were modified from the original SLEUTH source code.
Specifically, the files (or source codes) with labels "SLEUTsH version" contains the revision.

Replacing the files in your source code with the files labeled "SLEUTsH version" will enable the railway-induced urban growth.
After compiling, the following procedure may be done to introduce the railway-induced urban growth (i.e. urban growth attractivity is increased surrounding stations).

## 1. Create a station (additional input) Layer

This input layer must be in 'gif' format having the same dimensions as the other input layers (e.g. transporation, urban).
The stations and the buffers surrounding them must be set to an integer value of 1; elsewhere must be set to an integer value of 0.
Save the input layer following the format <location>.station.<date>.[<user info>].gif (note: similar to other input files except for the keyword "station")
in the Input folder.
  
## 2. Modify the scenario file

Link the station layer to the model through the scenario files of all model stages or phases of growth (e.g. calibrate, predict) by
inserting the following in the scenario file (see example in the "Scenario" folder):
```
STATION_DATA= TOD.station.1997.gif
STATION_DATA= TOD.station.2000.gif
```

## 3. Run the model as usual
