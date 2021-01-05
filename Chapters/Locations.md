# Locations
Taking as an example the production of something we might describe as “a crop of barley”, data that will affect that process is often not directly, or uniquely related to it.  For example:
- in spatial terms, operations and observations may relate to an area which intersects with that of the crop, but is not coterminous with it, 
- in temporal terms, the growth of the crop will be affected by soil type, and previous cropping.
-   
However, the relationship between the crop and all these factors can be established via location. 

## Point
The simplest kind of location is a point on the surface of the earth.  Point is defined with two Properties, Latitude and Longitude.  
>Point is an example of a Class, in the sense that it is a "class of things", there being either a finite, or an infinite number of "things in the class".  Classes are the key nodes in this model.


These properties need to be of specific types: LatitudeType is defined as a decimal number between -90 and 90 and LongitudeType as a decimal number between -180 and 180. 

In each case the precision of the decimal number needs to be limited.  One x 10<sup>-1</sup> degree of longitude at the equator and of latitude anywhere on the globe is in the order of one centimetre, so seven decimal places should be adequate.

There is little opportunity for crop production on the anti-meridian (-180 and 180 longitude), or at the poles (-90 and 90 latitude), so locations can be set in a two-dimensional space, although adjustment for latitude will need to be applied when calculating horizontal distances.
This will be a Method of Point which takes as a parameter another Point.
>In this UML model, Classes will only be given Methods where it is necessary (1) to acknowledge that it is required in order to be able adequately to process the data 
>and (2) to confirm that it can be performed using the Properties of the Class and of any Class, or Type in the parameter list.
>The list of Methods for any Class is not exhaustive.

A number of geographical information systems give three co-ordinates for a point – longitude, latitude and altitude, but altitude seems to be an unnecessary overhead, given the role of location in this domain.

![Point](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://github.com/Charles1625/crop-production-ontology/raw/main/uml/point.puml)

*Figure 1 - The Point Class and the Types it depends on*
## Path
A Path can be defined as of an ordered list of two or more Points. 
The use of a Path in this domain is limited, but might be of value for an observation made along a transect. 
It is possible to compute the Length of a Path from its set of Points. 

![Path](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/uml/path.puml)

*Figure 2 - Path Class*

## Polygon
By far the more common use of an ordered list of points will be a Polygon.  To turn a Path into the perimeter of a polygon only requires the last point in the ordered list to be joined to the first.
Tracing a series of point could result in crossed lines, e.g.Figure 3.

![Self intersecting polygon](https://raw.github.com/Charles1625/crop-production-ontology/main/images/self-intersecting-polygon.png)

*Figure3 - Self-intersecting polygon*

Whilst mathematicians are happy to treat this as a polygon, it will be inconvenient in this domain.

![Path](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/uml/polygon.puml)
*Figure 4 - Polygon Class*
