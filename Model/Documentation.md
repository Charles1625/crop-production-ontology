# Documentation of the UML Model

Full definitions of all of the elements in the UML Model are provided here with Classes in alphabetical order.  However, the definitive Model is in the PlantUML files (see [here](https://github.com/Charles1625/crop-production-ontology/blob/main/Model/Definitive-model.md)).

## Application
Application of a substance in an operation.

|Property| |
|:----|:----|
|Quantity : number|Quantity of substance applied, in kilogrammes for solids, or litres for liquids (and possibly gases).|

**Association class for**
[Operation](#operation) applies [Substance](#substance)

## Batch
A batch of produce of a crop.

|Property| |
|:----------|:----------|
|Reference : text | A reference for the batch.|

|Associations| |
|:---------|:------------|
|[Harvest](#harvest)|Any number of Harvests may be delivered into a batch.|
|[Planting](#planting) from Batch|Any number of Plantings may be made from a batch.|
|Batch of [Produce](#produce)|Any number of Batches may be of a Produce.|
|[Processing](#processing) of Batch|Any number of processings may be made of a batch.|
|[Purchase](#purchase) into Batch|Any number of purchases may be made into a batch.|
|[Sale](#sale) from Batch|Any number of sales may be made from a batch|
|[Test](#test) on Batch|Any number of tests may be made on a batch|
|[Transfer](#transfer) from Batch|Any number of transfers may be made from a batch.|
|[Transfer](#transfer) to Batch|Any number of transfers may be made to a batch.|

## Crop
A community of cultivated plants.

|Associations| |
|:-------|:------|
|[Planting](#planting)|A crop has at least one planting.|
|[Row](#row)|A crop may have an ordered pattern of rows (if it is not broadcast).|


## Harvest
Harvest of produce from a location.

|Properties| |
|:-----------|:-----------|
|DateTime : datetime|Date and time of the harvest.|
|Quantity : number|Quantity of crop harvested in kilogrammes.|

**Associated with**
- [Batch](#batch)
- [Location](#location)

## Ingredient
An ingredient of a substance.

|Properties| |
|:--------------|:-------------|
|Name : enumeration|One of an agreed list of names for ingredients of substances used in crop production.|
|Concentration : number|Percentage concentration of the ingredient in the substance.|

**Aggregated by**
- [Substance](#substance)

## Location
A location on the Earth's surface with some relation to crop production.

|Associations| |
|:------|:-------|
|[Harvest](#harvest) at Location|Any number of harvests can be made at a location.|
|[Observation](#observation) at Location|Any number of observations can be made at a location.|
|[Operation](#operation) at Location|Any number of operations can be carried out at a location.|
|[Planting](#planting) at Location|Any number of plantings/sowings can be made at a location.|
|Location contains Location|A Location may contain (include) any number of other locations.| 

## *Observation*
An observation at a location related to crop production.

|Property| |
|:-----------|:------------|
|DateTime : datetime| Date and time of the observation.|

**Associated with**
- [Location](#location)

## *Operation*
An operation at a location related to crop production.

|Property| |
|:------------|:------------|
|DateTime : datetime|Date and time that the operation was carried out.

|Association| |
|:-----|:-----|
|Operation applies [Substance](#substance)|An Operation may apply any number of different substances.|

**Associated with**
- [Location](#location)

## Planting
Planting/sowing of a crop

|Properties| |
|:---------|:-----------|
|DateTime : datetime|Date and time of the planting/sowing.|
|Quantity : number|Quantity of material planted/sown in kilogrammes.|
|Broadcast : boolean|True if the planting was random, or the sowing was broadcast.|

**Associated with**
- [Batch](#batch)
- [Crop](#crop)

## *Processing*
Some processing of a batch of produce.

|Property| |
|:------|:--------|
|DateTime : datetime|Date and time of the processing.|

**Associated with**
- [Batch](#batch)

## Produce
Description of plant material harvested for some use.

|Properties| |
|:-----------|:------------|
|Species : enumeration|The species of the plants.|
|Variety : enumeration|The variety (cultivar) of the plants.|
|Part : enumeration|The part of the plants (e.g. grain, or straw).|

**Associated with**
- [Batch](#batch)

## Purchase
A purchase of produce (possibly as seed), or other movement of produce to a Batch which is not from another Batch.

|Properties| |
|:----------|:------|
|DateTime : datetime|Date and time of movement of the produce to the Batch.|
|Quantity : number|Quantity of produced moved in kilogrammes.|

**Associated with**
- [Batch](#batch)

## Row
Row of crop within a pattern

|Property| |
|:---|:---|
|Distance : number|Distance in centimetres to the next row in the pattern.|

|Association| |
|:---|:---|
|[Planting](#planting)|A row is from a planting which must be one of the plantings of the crop of which it is a row|

**Associated with**
- [Crop](#crop)

## Sale
A sale of produce , or other movement of produce from a Batch which is not to another Batch.

|Properties| |
|:----------|:------|
|DateTime : datetime|Date and time of movement of the produce from the Batch.|
|Quantity : number|Quantity of produced moved in kilogrammes.|

**Associated with**
- [Batch](#batch)

## Substance

A substance used in crop production.

|Property| |
|:----------|:-------|
|Name : enumeration|One of an agreed list of names for substances used in crop production.|
|State : enumeration|Physical state in which the substance is used.|

|Aggregation| |
|:-------------|:-----------|
|[Ingredient](#ingredient) in Substance|A substance may contain a number of ingredients.|

## Test
A test on a batch of produce.

|Property| |
|:------|:--------|
|DateTime : datetime|Date and time of the sampling for the test.|

**Associated with**
- [Batch](#batch)

## Transfer
Transfer of produce from one batch to another.

|Properties| |
|:-----|:----|
|DateTime : datetime|Date and time of the transfer.|
|Quantity : number|Quantity transferred in kilogrammes.|

**Associated with**
- [Batch](#batch)

