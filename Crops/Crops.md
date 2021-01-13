# Crops
Like most production systems, crop production consumes and produces materials.

In Figure 1, Crop refers to the kind of crop, as in "Wheat is being grown in Long Field" and Batch refers to some actual
produce of a crop, as in "The wheat in the first bay of the barn at Green Farm was grown in Long Field".

A Crop is identified by species, variety (cultivar) and the part of the plant, such as grain, or straw.


![Crop and Batch](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Materials/batch-crop1.puml)

*Figure 1 - Crop and Batch*

Data on Crop will be provided centrally - data from individual production units will only refer to Crop 
via Batch.

The produce of a crop may also be used as seed, or other propagative material, and the history of that material will 
be relevant to the crop grown from it.  Batches
of it will be associated with sowing/planting and harvest, both of which require a location.  Whether, or not
it is used as seed, it is potentially subject to a number of treatments, e.g. drying,
cleaning, chemical treatment.

Tests for quality etc. are made on batches.

Figure 2 shows the Batch class and the events that happen to batches.

![Batch and events](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Materials/batch-events.puml)










