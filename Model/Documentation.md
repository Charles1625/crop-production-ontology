# Documentation of the UML Model

Full definitions of all of the elements in the UML Model are provided here.
The full Model is also provided in PlantUML (model.puml) for completeness.

## LatitudeType 
A decimal number between -90 and 90 with a precision of no more than 7.

## LongitudeType 
A decimal number between -180 and 180 with a precision of no more than 7.

## Path
A path on the Earth's surface
|Method | |
|--------|------|
|Length() : number|Sum of the lengths of the straight lines joining consecutive pairs of Points.|

*Aggregation**
Path has Points


## Point 
A point in a rectangle representing an Equirectangular projection of the Earth's surface.

| Properties | |
|------------|---------|
|Latitude : LatitudeType |the y-coordinate of the Point|
|Longitude : LongitudeType|the x-coordinate of the Point|

| Method| |
|----------|----------|
|DistanceFrom(point : Point) : number|The actual distance on the Earth's surface between this point and the given point.|

**Aggregated**
See:
- Path
- Polygon

## Polygon
A non-self-intersecting polygon on the Earth's surface.

|Methods| |
|-------|------|
|Area() : number|the area of this Polygon|
|Intersection(polygon : Polygon) : Polygon|
a Polygon, if any, that represents the overlapping of this Polygon and the given Polygon.|
|Contains(point : Point) : boolean|True if this Polygon contains the given Point.|

*Aggregation**
|---------|--------|
Polygon has Points
