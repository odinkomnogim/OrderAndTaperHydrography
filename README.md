# OrderAndTaperHydrography
This is a QGIS plugin that helps to determine stream orders and visualize hydrography, taking flow direction into consideration (i.e. in a tapered way). 

![example](https://github.com/odinkomnogim/OrderAndTaperHydrography/blob/main/example_screenshots.png?raw=true)

Tapered hydrography mapping, in this case, involves changing the geometry of linear features. 
Every segment of a line (distance between two neighboring vertices) is bufferd, taking into account stream’s order, length and flow direction, using this equation: 

<p align="center">
  <img src="https://latex.codecogs.com/svg.image?B1=k\cdot\frac{1}{Or&plus;1}\cdot\textrm{lg}L\cdot\frac{N}{C}">
</p>

where B1 is the width of the buffer for a specific line segment; 
k is a custom (scale) coefficient; 
Or is the stream order; 
L is the river’s length; 
N is the ordinal number of a specific segment; 
C is the total number of the river segments.

However, there are streams whose source is located at the confluence of the other two. In such cases, the algorithm would still start displaying the river from the minimum value, which would violate the smoothness and integrity of the network visualization. In order to avoid such incorrect mapping, previous equation is applied only to some of the more remote tributaries whose order value does not exceed 80% of the maximum order. For example, if the network is represented by the main river and tributaries up to the 6th order, then the algorithm is applied only for 5 and 6.

When the tributary is larger, a rule is set: all segments lying in the first 40% of the total count (regardless of the N/C parameter) are displayed with a buffer of the same width calculated as:

<p align="center">
  <img src="https://latex.codecogs.com/svg.image?B2=0.4\cdot&space;k\cdot\frac{1}{Or&plus;1}\cdot\textrm{lg}L\cdot\frac{N}{C}">
</p>

where B2 is the width of the buffer set for the upper courses of larger rivers.

This approach makes it possible not only to solve the problem of visualizing rivers whose source is located at the confluence of two tributaries, but also to highlight a more important riverbed out of two in cases where the merging scheme is standard.

That is one of possibilities to quickly visualize hydrographic networks, taking into account the hierarchy of tributaries and the direction of their flow. The developed algorithm for mapping river systems can significantly reduce the time spent on preparing the hydrography layer: instead of manually processing or symbolizing each river. This approach can be recommended for small-scale mapping to visualize hydrography layer for thematic or general-purpose maps.

## Installation 
To install this plugin you have to download 'order_and_taper_hydrography.zip', then in QGIS go to Plugins -> Manage and Install Plugins -> Install from ZIP.

## Usage
To determine stream orders and visualize hydrography in a tapered way, you have to ***select*** (highlight) the main river, and then run this plugin.




