# Crops

In Figure 1, Crop refers to the kind of crop, as in "Wheat is being grown in Long Field" and Batch refers to some actual
produce of a crop, as in "The wheat in the first bay of the barn at Green Farm was grown in Long Field".

A Crop is identified by species, variety (cultivar) and the part of the plant, such as grain, or straw.


![Crop and Batch](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Materials/batch-crop.puml)

*Figure 1 - Crop and Batch*

The produce of a crop may also be used as seed, or other propagative material, and the history of that material will 
be relevant to the crop grown from it.  Batches
of it will be associated with sowing/planting and harvest (see Events).  Whether, or not
it is used as seed, it is potentially subject to a number of processing events, e.g. drying,
cleaning, chemical treatment.

Data on Crop will be provided centrally - data from individual production units will only refer to Crop 
via Batch.

It is possible for Batches to merge and split any number of times and this is handled by Transfers (see Figure 2).

![Batch and Transfer](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Materials/batch-transfer.puml)










