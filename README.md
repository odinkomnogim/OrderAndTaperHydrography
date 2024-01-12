# OrderAndTaperHydrography
This is a QGIS plugin that helps to determine stream orders and visualize hydrography, taking flow direction into consideration (i.e. in a tapered way). 

Tapered hydrography mapping, in this case, involves changing the geometry of linear features. 
Every segment of a line (distance between two neighboring vertices) is bufferd, taking into account stream’s order, length and flow direction. 

<p align="center">
  <img src="https://latex.codecogs.com/svg.image?B1=k\cdot\frac{1}{Or&plus;1}\cdot\textrm{lg}L\cdot\frac{N}{C}">
</p>

where B1 is the width of the buffer for a specific line segment; 
k is a custom (scale) coefficient; 
Or is the stream order; 
L is the river’s length; 
N is the ordinal number of a specific segment; 
C is the total number of the river segments.

## Installation 
To install this plugin you have to download 'order_and_taper_hydrography.zip', then in QGIS go to Plugins -> Manage and Install Plugins -> Install from ZIP.
