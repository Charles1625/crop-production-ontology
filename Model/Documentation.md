# Documentation of the UML Model

Full definitions of all of the elements in the UML Model are provided here with Classes in alphabetical order.

See [here](https://github.com/Charles1625/crop-production-ontology/blob/main/Model/UML.md) for information on the formal definition of the Model.

## Batch
A batch of material.

|Property| |
|----------|----------|
|Reference : text | A reference for the batch|

**Association**

See:
- [Material](#material)

## Compound
A chemical compound

|Property| |
|-----------|------------|
|Name : text|Name of the compound|

**Association**

See:
- [Substance](#substance)

## Content
The content of a particular chemical compound in a particular substance

**Association Class for**

[Substance](#substance) contains Compound

|Property| |
|-----------|-----------|
|Concentration : number|The concentration of the chemical compound in the substance|


## ExcludedPolygon
A Polygon (see "IncludedPolygon has ExcludedPolygon" aggregation).

**Aggregated by**

- [IncludedPolygon](#includedpolygon)

**Generalization**
- [Polygon](#polygon)

## IncludedPolygon
A polygon that is part of a Region (see also ExcludedPolygon).

|Aggregation| |
|--------------|-------------|
|IncludedPolygon has [ExcludedPolygon](#excludedpolygon)|An IncludedPolygon may have any number of ExcludedPolygons, each of which exclude that part of it from the Region to which it belongs, but does not exclude part of any other IncludedPolygon of that Region.|

**Aggregated by**
-[Region](#region)

**Generalization**
-[Polygon](#polygon)

## LatitudeType 
A decimal number between -90 and 90 with a precision of no more than 7.

**Stereotype**

dataType

## *Location*
A location on the Earth's surface with some relation to crop production.

**Specializations**
- [Path](#path)
- [Point](#point)
- [Region](#region)

## LongitudeType 
A decimal number between -180 and 180 with a precision of no more than 7.

**Stereotype**

dataType

## *Material*
A kind of material.

|Association| |
|----------|------------|
|[Batch](#batch) of Material|Any number of batches may be of a single material.|

## Path
A path on the Earth's surface with some relation to crop production.
|Method | |
|--------|------|
|Length() : number|Sum of the lengths of the straight lines joining consecutive pairs of Points.|

|Aggregation| |
|------------|------------|
|Path has [Point](#point)|A Path has an ordered set of Points


## Point 
A point in a rectangle representing an Equirectangular projection of the Earth's surface with some relation to crop production.

| Properties | |
|------------|---------|
|Latitude : [LatitudeType](#latitudetype) |the y-coordinate of the Point|
|Longitude : [LongitudeType](#longitudetype)|the x-coordinate of the Point|

| Method| |
|----------|----------|
|DistanceFrom(point : Point) : number|The actual distance on the Earth's surface between this point and the given point.|

**Aggregated by**
- [Path](#path)
- [Polygon](#polygon)

## *Polygon*
A non-self-intersecting polygon on the Earth's surface with some relation to crop production.

|Methods| |
|-------|------|
|Area() : number|the area of this Polygon|
|Intersection(polygon : Polygon) : Polygon|a Polygon, if any, that represents the overlapping of this Polygon and the given Polygon.|
|Contains(point : Point) : boolean|True if this Polygon contains the given Point.|

|Aggregation| |
|-------------|--------------|
|Polygon has [Point](#point)|A polygon has an ordered set of Points, such that no straight line between any two consecutive points is allowed to cross any other straight line between two consecutive points or between the first point and the last point.|

**Specializations**
- [ExcludedPolygon](#excludedpolygon)
- [IncludedPolygon](#includedpolygon)

## Produce
The produce of a crop.

|Properties| |
|-----------|------------|
|Species : text|The species of the producing crop.|
|Variety : text|The variety (cultivar) of the producing crop|
|Part : text|The part of the plant (e.g. grain, or straw)|


## Region
A region of the Earth's surface with some relation to crop production which may consist of any number of non-contiguous parts.

|Properties| |
|--------|------|
|Reference : [RegionReference](#regionreference)|A reference for the Region consisting of any number of parts of a variety of types.|

Methods| |
|---------|----------|
|Area() : number|Total area covered by the Region|
|Intersection(region : Region) : Region|The Region if any that represents the overlap between this Region and the given Region.|
|Contains(location : [Location](#location) : boolean |True if the given Location is contained by this Region.|

|Aggregation| |
|-----------|------------|
|Region has [IncludedPolygon](#includedpolygon)|A Region may have any number of IncludedPolygons|

## *RegionReference*
A reference for a region.

**Stereotype**

dataType

## Substance

A substance involved in crop production.

|Property| |
|----------|-------|
|ProductName : text|A product name for the Substance.|

|Association| |
|-------------|-----------|
|Substance contains [Compound](#compound)|A substance may contain a number of compounds.  A compound may be contained by a number of substances.|

## UKFieldReference
An example of a [RegionReference](#regionreference).
