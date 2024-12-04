# A Crop Production Ontology

## Introduction
As for many domains, there is a need for large datasets (Big Data) to assist the 
development of machine-learning solutions for crop production. 
Data in this domain currently exists in a wide range of formats, 
including those managed by a variety of applications in use by farmers and growers. Often, there is a need for these applications to integrate.
The first step in building the necessary datasets and to achieve inter-application integration will be to agree a standard ontology; the challenge is to create a 
common set of terms for describing crop production data that will apply to a wide range of crops and production methods,
including those which might develop in the future.

The aim of machine-learning solutions for crop production will be to establish how what happens to crops affects what is produced from them.

Data on the former is often neither directly, nor uniquely related to the latter.  For example:

- in spatial terms, operations and observations may relate to an area which intersects with that of the crop, but is not coterminous with it, 
- in temporal terms, crop growth can be related to factors measured some time before the crop was established.

However, the relationship between the crop and these data can be established via their Location.

Similary, there are difficulties in relating data on what was produced (quality, quantity and subsequent processing) with the crop growing in the 
field.  Produce from different fields may be bulked together, or split up, so data needs to be related to a Batch of Produce.

Data is generated from a series of events:

- Planting and Harvest can be related to both a Location and a Batch.

- An *Operation*, or an *Observation* can be related to a Location.

- The following can be related to a Batch:

  - *Test* (on a sample),
  - *Processing*,
  - Transfer (between Batches)
  - Purchase,
  - Sale.

Some of the above are *generalizations* and through collaboration with domain experts (farmers, growers, agronomists and other crop scientists), it is hoped 
to improve the granularity of the terms used.

## Collaboration
The sharing of this project through GitHub allows collaboration between domain experts (e.g. farmers, agronomists, crop scientists) and data 
scientists who may raise Issues (see the menu), or may make a more hands-on contribution.  

>Those wishing to do the latter will need to be, or become familiar with the [GitHub process](https://github.com/firstcontributions/first-contributions) and [Markdown](https://www.markdownguide.org/getting-started/).  [PlantUML](https://plantuml.com/) will be helpful to those wishing to modify, or contribute UML diagrams.

Collaboration is needed both to improve and extend what is currently presented.

## Output
The output of this project will be:
- A formal description of terms and how they relate to each other, expressed as a Model built using the Unified Modeling Language (UML).
- A machine readable [Schema](Schema/Readme.md) based on the Model, against which datasets can be standardised so that they can be combined.

## Scope

The scope of the product must be limited to the measurement of:

- the quality and quantity of produce and
- the factors that affect the above.

This would exclude, for example, specific requirements for financial and stock control.


## Development of the Model
The following describes the thinking behind the [Model](https://github.com/Charles1625/crop-production-ontology/blob/main/Model/Documentation.md). 
A set of UML diagrams are presented, each followed by a set of explanatory statements.  There is no need to make any special study of UML, 
because the meaning of the various symbols and text in the diagrams should become obvious from the explanatory statements.
> The display of UML diagrams in documents in this repository is unstable, because it relies on the PlantUML server which is sometimes too slow for the GitHub server.  If a diagram is not displayed, click on the hyperlink displayed in its place.  It may be necessary to make several attempts at this.

### Location
![Point](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Diagrams/point.puml)

The simplest kind of Location is a point on the surface of the earth.  A Point has two Properties, Latitude and Longitude.  

There is little opportunity for crop production on the anti-meridian (-180 and 180 longitude), or at the poles (-90 and 90 latitude), so Locations can 
be set in a two-dimensional space.  Calculations of distances and thus areas will need to take account of latitude.

A number of geographical information systems give three co-ordinates for a point – longitude, latitude and altitude. Crops are assumed to be grown on the surface of the earth which is a plane, so altitude, if required can always be determined from existing geographical information systems.

![Path](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Diagrams/path.puml)

A Path can be defined as an ordered list of two or more Waypoints, represented by a minimum of two Points.

The use of a Path in this domain is limited, but might be of value for an observation made along a transect. 

![Path](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Diagrams/polygon.puml)

By far the more common use of an ordered list of points will be a Polygon.  Here, a Point takes the role of Vertex of which there must be at least three.
Tracing a series of points could result in crossed lines:

![Self intersecting polygon](https://raw.github.com/Charles1625/crop-production-ontology/main/Diagrams/self-intersecting-polygon.png)

While mathematicians are happy to deal with self-intersecting polygons, it will be inconvenient in this domain.

![Region](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Diagrams/region.puml)

A simple Polygon is not necessarily going to be sufficient to describe the kind of Region which a crop may occupy,
 or on which operations, or observations are made.  This is the kind of complex situation that can arise:

![Complex field layout](https://raw.github.com/Charles1625/crop-production-ontology/main/Diagrams/field-layout.png)

The narrative for this map, involving five Polygons, might be:
>The field is divided into two parts by a track.  In the larger part there are two areas where the crop failed to establish, but, in one of these, a small patch of crop did establish.

In crop production, a field is only one example of something that can have such a complex layout, so Region is suggested
as a name for this.  In the above map, the Region has three green areas which can be referred to as RegionParts.  Their external
boundaries are Polygons, but, in the case of the largest, there are Holes which are also Polygons.  A Hole belonging to
one RegionPart can only exclude land from that RegionPart, thus allowing islands to be created by other RegionParts,
e.g. the small green triangle in the map. 

In the map, there are three RegionParts of which one has two Holes.

>This is a similar approach to that described in 
>[sub-section 2.7.2 of the Oracle Spatial and Graph Developer’s Guide – “Polygon with a Hole”](https://docs.oracle.com/database/121/SPATL/polygon-hole.htm#SPATL520 ),
>(see the discussion about countries with lakes and islands in the lakes) except that the design of Region avoids the complication of
>placing the co-ordinates of a polygon and its holes in the same list.

![Location](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Diagrams/location.puml)

Aspects of crop production may relate to Point, Path, or Region and can be generalized as Location.  

There may also be
Locations where, although no co-ordinates are known, it is known that observations and operations have occurred there and it
may also be known that such a Location is contained within another Location.  This would be the case in IT systems for arable farming
that do not include any form of mapping.  Therefore, Locations will need to be linked to each other without recourse to geometry. 
An UnmappedPath
will have a Length and an UnmappedRegion will have an Area.

### Batch

![Produce and Batch](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Diagrams/batch-produce.puml)

A Batch is of a particular kind of Produce and there may be several Batches of any Produce.

Produce is identified by species, variety (cultivar) and the part of the plant, such as grain, 
or straw.  An agreed list of names (enumeration) for each of these three things will be required.

![Batch and events](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Diagrams/batch-events.puml)
Harvests will take place into Batches and will be at a Location.

Material from a Batch may also be used as seed, or other propagative material, and the history of that material may 
be relevant to what is grown from it.  Therefore Plantings will be made from Batches.  

Where there is intercropping there will be more than one Planting, even if these take place simultaneously.  Together such Plantings will make up a Crop which will be at a Location.  Unless it is all  either Broadcast, or randomly planted, the Crop will have a pattern of Rows with each Row belonging to one of the Plantings and being a certain Distance from the next Row.

Whether, or not
a batch is used as seed, it is potentially subject to Processing, e.g. drying, cleaning, chemical treatment.

Tests for quality etc. are made on batches, Transfers may be made from one Batch to another, and Purchases and Sales (or other movements of material
to, or from the production unit) may occur.

Processing and Test are classes that will require specialization.

### Observations and Operations
![Observation](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Diagrams/obs-op.puml)

An Observation is made at a Location.  The data observed will vary depending on the type of
Observation, so it will be an abstract, generalizing class whose specializations will need to be determined following
consultation with domain experts.

An Operation is performed at a Location, usually involving some kind of machine, or tool.  The settings of this machine will be
relevant, but the type of setting will vary according to machine; examples might be depth for a cultivator and volume per acre
for a sprayer, so Operation is an abstract class whose specializations will be determined in consultation with domain experts.

Operations may involve  the Application (spreading, or spraying) of Substances, such as pesticides, fertilizers and plant 
growth regulators each of which will contain one, or more active Ingredients.  An agreed list of Substances and their Ingredients 
will be required.
























