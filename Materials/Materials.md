# Materials

Crop production, like most production systems, consumes and produces materials.  As a biological production
system, crop production can consume the material that it produces (seed etc.).

Materials may be referred to in two ways.  Consider the following statements:

- Wheat is being grown in Long Field.
- Nitram has been spread on Long Field.
- The wheat in the first bay of the barn at Green Farm was grown in Long Field.
- The Nitram delivered to Green Farm on February 15 was spread on Long Field.

The first pair of these refer to the kind of material being grown, or spread while the second pair refer
to actual batches of material.  The relationship between the Classes, Material and Batch, is shown in Figure 1 with the
properties one would expect for these Classes.

![Material and Batch](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Materials/batch-material.puml)

*Figure 1 - Material and Batch*

The role of Batch needs to be considered in relation to Events, so the rest of this 
documented is devoted to Material

Material is abstract, because the type of data required varies.  The following two 
specializations of Material have been identified:

- Substances - whether agrochemicals, or fertilizers, require information on their active 
ingredients.  They will be identified by product name

- The Produce of a crop may also be used as seed, or other propagative material, and the history of that material will 
be relevant to the crop grown from it.  Batches
of it will be associated with sowing/planting and harvest (see Events).  Whether, or not
it is used as seed, it is potentially subject to a number of processing events, e.g. drying,
cleaning, chemical treatment.  Produce will be identified by species, variety (cultivar) and the part of the plant, 
e.g. grain, or straw.

It might be argued that there is no need to generalize these two classes - that
they are two unrelated Classes. However, they both require Batches and, after discussion,
there may be other specializations of Material identified.

Data on materials will be provided centrally - data from individual production units will only refer to materials 
via batches.

Material and its specializations are illustrated in Figure 2.

![Materials](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/Charles1625/crop-production-ontology/main/Materials/materials.puml)

*Figure 2 - Materials*










