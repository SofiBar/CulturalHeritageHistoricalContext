# Historical Frame Module overview

The Historical Frame module is intended to relate the CH object observed to the cross-cultural system identified in Anderson’s model.
Historical frames in the proposed model express more detailed and less generic situations that can be identified as a cultural context of an artwork. It captures the space-time continuum to relate the observed cultural object(s) to socio-cultural characteristics of the same context(s). Its definition partially reflects the one given for the E4 Period class, in which a period is recognized as having its own identity (e.g., Renaissance). However, in case a specific object needs to be examined in more detail, the focus can be on the identities of specific groups or subcultures co-existing in the same period, which may not be commonly recognized as having their own identity (e.g., the culture of the circle of intellectuals in Rome).



## New classes

| `Class` | `Alignment`|`            Description             `|
|------------|--------|----------------|
| :Historical Frame |  subclass of crm: E92_Spacetime_Volume  | The Historical Frame captures the space-time continuum to relate the observed CH object(s) to socio-cultural characteristics of the same context(s). In this way, they identify sets of traits that are commonly recognized as existing in specific time-space contexts. In this sense, they are an observation and selection of the fuzzy reality of culture, isolating salient traits.  |
| :Culture |  SDHSS (when it will be published) C26 Representation Fuzzy class to indicate the broad concept of culture, of which the frame observes some features (e.g., the belief that St. Servatius drank from the drinking cup) | Fuzzy class to indicate the broad concept of culture, of which the frame observes some features (e.g., the belief that St. Servatius drank from the drinking cup)| 


## Reused classes
| `Name `| `          Description           `|
|-----------|----------------|
|crm:E53_Place | “This class comprises extents in the natural space where people live [...] They may serve describing the physical location of things or phenomena or other areas of interest.” See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E53_Place   | 
 | crm:E52_Time_Span  | Abstract temporal extents, having a beginning, an end, and a duration. No semantic connotations are attributed to them. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E52_Time-Span   | 
 | icon:CulturalPhenomenon  | “The cultural phenomenon entity expresses the cultural, social, and historical aspects of which the work of art can be a document”. See the full scope note at: https://w3id.org/icon/ontology/CulturalPhenomenon   | 
| icon:Belief  | Specification of a cultural phenomenon as a belief  | 
| icon:Attitude  | Specification of a cultural phenomenon as an attitude  | 
| icon:CulturalValue |Specification of a cultural phenomenon as a cultural value |
icon:Tendency |Specification of a cultural phenomenon as a tendency|


## New properties

| `Property` | `Domain`     | `Range`        |`             Description             ` |
|-------|-----|--------|----------------|
| :hasContext|  Entity| :HistoricalFrame | Relation betwee objects, events or situations in which they participate, and a :HistoricalFrame which identifies the socio-cultural context in which the object existed | 
| :hasCreationContext |  Entity | HistoricalFrame | Subproperty of :hasContext to specifically express that the object examined is related to the cultural context in which it was created (e.g., “Roman culture, is the creation context of the Roman cup created in I Century) | 
| :includesculturalTrait |  :HistoricalFrame| icon:CulturalPhenomenon | The property relates a Historical Frame with the immaterial traits of a culture that are relevant for the understanding of the objects. Once ontologies for societal aspects (e.g., SDHSS) will be fully worked out, the range of this property will be updated. 
| :refersToCulture |  :HistoricalFrame| :Culture| Relation of historical frame to the fuzzy culture it observes|
:motivates|  crm:E1_Entity|  crm:E1_Entity| Generic relation that expresses that an entity motivates the existence or characteristics of another one (e.g., the belief that St. Servatius drunk from the cup motivates the healing function of the cup) | 
| :believedThing |  icon:Belief|  crm:E1_Entity| A relation specifying the thing believed in the belief system of the culture in question.| 




## Reused properties

| `Property` | `Domain`     | `Range`        |`        Description        ` |
| ---------| -------| -------| -----------| 
| crm:P10_falls_within | crm:E92_SpacetimeVolume | crm:E92_SpacetimeVolume | “This property associates an instance of E92 Spacetime Volume with another instance of E92 Spacetime Volume that falls within the latter. In other words, all points in the former are also points in the latter. This property is transitive and reflexive.” |
|crm:P132_spatiotemporally_overlaps_with | crm:E92_SpacetimeVolume  | crm:E92_SpacetimeVolume |“This symmetric property associates two instances of E92 Spacetime Volume that have some of their extents in common”. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/P132_spatiotemporally_overlaps_with |
|crm:P133_spatiotemporally_separated_from | crm:E92_SpacetimeVolume | crm:E92_SpacetimeVolume  | “This symmetric property associates two instances of E92 Spacetime Volume that have no extents in common”. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/P133_spatiotemporally_separated_from |
|crm:P161_has_spatial_projection| crm:E92_SpacetimeVolume| crm:E53_Place | “This property associates an instance of E92 Spacetime Volume with an instance of E53 Place that is the result of the spatial projection of the instance of the E92 Spacetime Volume on a reference space”. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/P161_has_spatial_projection |
|crm:P160_has_temporal_projection | crm:E92_SpacetimeVolume | crm:E52_Time_Span | “This property describes the temporal projection of an instance of E92 Spacetime Volume” |
