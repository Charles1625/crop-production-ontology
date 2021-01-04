# Documentation of the UML Model

Full definitions of all of the elements in the UML Model are provided here.
The full Model is also provided in PlantUML (model.puml) for completeness.

## LatitudeType {#latitude-type}
A decimal number between -90 and 90 with a precision of no more than 7.

## LongitudeType {#longitude-type}
A decimal number between -180 and 180 with a precision of no more than 7.

## Point {#point}
A point in a rectangle representing an Equirectangular projection of the Earth's surface.

| Properties | |
|------------|---------|
|Latitude|a value of [LatitudeType]{#latitude-type}, being the y-coordinate of the Point|
|Longitude|a valud of [LongitudeType]{#longitude-type}, being the x-coordinate of Point|

| Method| |
|----------|----------|
|DistanceFrom(point : Point)|The actual distance between this point and the given point.