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

![Point](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/uml/point2.puml)

*Figure 1 - The Point Class and the Types it depends on*
## Path
A Path can be defined as an ordered list of two or more Points. 
The use of a Path in this domain is limited, but might be of value for an observation made along a transect. 
It is possible to compute the Length of a Path from its set of Points. 

![Path](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/uml/path2.puml)

*Figure 2 - Path Class*

## Polygon
By far the more common use of an ordered list of points will be a Polygon.  To turn a Path into the perimeter of a polygon only requires the last point in the ordered list to be joined to the first.
Tracing a series of point could result in crossed lines, e.g.Figure 3.

![Self intersecting polygon](https://raw.github.com/Charles1625/crop-production-ontology/main/images/self-intersecting-polygon.png)

*Figure3 - Self-intersecting polygon*

Whilst mathematicians are happy to treat this as a polygon, it will be inconvenient in this domain.

![Path](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/uml/polygon2.puml)

*Figure 4 - Polygon Class*

## Region
A simple Polygon is not necessarily going to be sufficient to describe the kind of region which a crop may occupy,
 or on which operations, or observations are made.  Figure 5 illustrates the kind of complex situation that 
can arise.

![Complex field layout](https://raw.github.com/Charles1625/crop-production-ontology/main/images/field-layout.png)

*Figure 5 - Complex field layout*

The narrative for this map, involving five Polygons, might be:
>The field is divided into two parts by a track.  In the larger part there are two areas where the crop failed to establish, but, in one of them, a small patch of crop did establish.
>
This collection of Polygons can be referred to as a Region and two types of Polygon are recognised, 
an IncludedPolygon and an ExcludedPolygon.  An IncludedPolygon may, or may not 
contain one, or more ExcludedPolygons.   
A Region will contain one, or more IncludedPolygons and (indirectly) any Excluded Polygons contained by 
those IncludedPolygons.
>This is a simlar approach to that described in [sub-section 2.7.2 of the Oracle Spatial and Graph Developer’s Guide – “Polygon with a Hole”](https://docs.oracle.com/database/121/SPATL/polygon-hole.htm#SPATL520 ), except that it avoids the complications that would arise if the co-ordinates of a polygon were placed in the same list as those of its holes.

In Figure 5, there are three IncludedPolygons of which one has two ExcludedPolygons.

Regions will often need some sort of reference.  It is not known at this stage how many different types of 
reference there will be, but a UK farmer, for example, might reference a field with an OS Parcel ID, a 
traditional field name and possibly a number.  Region therefore has a Reference attribute with an abstract 
RegionReference type which acts as a generalization of any number of reference types that are required.  
Figure 6 shows 
this abstract class with a possible specialization (opposite of generalization).

![RegionReference](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/uml/region-reference.puml)

*Figure 6 - Region Reference Abstract Type*

>RegionReference is referred to as "abstract" and its name italicised in the diagram, because it is only a
>generalization - it has to be specialized, as exemplified in Figure 6 - there cannot be an actual instance 
>of a RegionReference.

![Region](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/uml/region.puml)

>The Location Class referred to in the Contains Method is discussed below.

Aspects of crop production may relate to Point, Path, or Region and can be generalized as Location.  

Figure 7 summarises what is understood about location.

![Location](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/uml/location.puml)

*Figure 7 - Location*






