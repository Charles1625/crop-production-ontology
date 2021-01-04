# A Crop Production Ontology
As for many domains, there will presently be a need for large datasets (Big Data) to assist the development of artificial intelligence (AI) based solutions for crop production.  Data in this domain currently exists in a wide range of formats, including those managed by a number of different applications in use by farmers.  The first step in building the necessary datasets will be to agree a standard ontology.  The challenge is to create a common language about crop production which can be used in a wide variety of situations, including those which might develop in the future.  

The output of this project will be:
- A Dictionary describing things involved in crop production and how they relate to each other.
- A machine readable format so that datasets can be combined.  Technically, this will be a JavaScript Object Notation (JSON) schema.

The sharing of this project through GitHub, allows collaboration between domain experts (e.g. farmers, agronomists, crop scientists) and data scientists who may raise Issues, or may make a more hands-on contribution.  (Those wishing to do the latter will need to be, or become familiar with the [GitHub process](https://github.com/firstcontributions/first-contributions) and [Markdown](https://www.markdownguide.org/getting-started/).  Additionally, [PlantUML](https://plantuml.com/) is needed to modify, or contribute UML diagrams.)

Continue reading for a discussion of the rationale behind the terms and definitions chose for the Dictionary.

## Methodology
The Universal Modeling Language (UML) is a concise and precise means of documenting semantics. 
A UML model can be viewed as a series of diagrams containing standard symbols.  For this ontology one type of UML diagram, the UML Class Diagram, is used to show the relationship between the terms defined in the Dictionary.

However, no initial familiarity with UML is required - the meaning of the symbols in the diagrams will become obvious from the text.

## Location
Taking as an example the production of something we might describe as “a crop of barley”, data that will affect that process is often not directly, or uniquely related to it.  For example:
- in spatial terms, operations and observations may relate to an area which intersects with that of the crop, but is not coterminous with it, 
- in temporal terms, the growth of the crop will be affected by soil type, and previous cropping.
-   
However, the relationship between the crop and all these factors can be established via location. 

### Point
The simplest kind of location is a point on the surface of the earth.  Point is defined with two Properties, Latitude and Longitude.  

These properties need to be of specific types: LatitudeType is defined as a decimal number between -90 and 90 and LongituedType as a decimal number between -180 and 180. 

In each case the precision of the decimal nummber needs to be limited.  One x 10<sup>-1</sup> degree of longitude at the equator and of latitude anywhere on the globe is in the order of one centimetre, so seven decimal places should be adequate.

There is little opportunity for crop production on the anti-meridian (-180 and 180 longitude), or at the poles (-90 and 90 latitude), so locations can be set in a two-dimensional space, although adjustment for latitude will need to be applied when calculating horizontal distances.

A number of geographical information systems give three co-ordinates for a point – longitude, latitude and altitude, but altitude seems to be an unnecessary overhead, given the role of location in this domain.

