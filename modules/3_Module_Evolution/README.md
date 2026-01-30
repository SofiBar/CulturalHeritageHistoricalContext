# Evolution Module overview
The module to express the evolution of material and immaterial objects and their functions combines the Art and Architectural Argumentation Ontology (AAAo) with CIDOC-CRM and GA Storylines. It describes three types of evolution, namely the evolution of the function, of the material, and of immaterial aspects of the object in question.  
To represent the change of function, the class `aaao:ZE_Function_Status`, introduced in the Object in Situation module, is reused. Being defined as a temporal entity, the evolution of the function can be expressed by declaring multiple instances of the class, each associated with a different time-span, and indicating the chronological order in which they occur through the relation `aaao:ZP113_has_successor_status`. 
CIDOC-CRM is reused to describe the physical change of the object. crm:E79_Part_Adition and crm:E80_Part_Removal indicate that a physical part that was added or removed from the object (respectively through the relations crm:P111 added and crm:P113 removed), augments or diminishes (`crm:P110 augmented`/`crm:P11 diminishes`) the same object, but that is preserves its identity. On the other hand, `crm:E81_Transformation` indicates that the physical modification had an impact on the identity of the object, therefore transforming the object into a new one.  The property :manifestsIn is newly introduced to relate the same physical object to multiple physical versions of it. 
The immaterial changes to the immaterial part of the object, namely, the visual representation (`crm:E36 Visual Item`), are described by the class class :ConceptualVariation, which modifies (`:modifies`) a previous version and creates a new one (`:creates`).   
The evolution of material and immaterial variations of the object can be modeled by reusing the GA model of storylines [1], in which the storyline is defined as a chain of events (perdurants) in which the observed CH object participates.





## New classes

| `Class` | `Alignment`|`            Description             `|
|------------|--------|----------------|
| :ConceptualVariation | subclass of crm:E7_Activity | The class identifies an activity that modifies immaterial visual traits of a CH object, such as the subject depicted, creating two versions of the immaterial object, which correspond to the version preceding the intervention and the one resulting from it. | 



## Reused classes
| Name |          Description          |
|-----------|----------------|
|`aaao:ZE5_Function Status` | "An instance of function status is the collective ascription of an operative functionality to an object by a community. The substance of the function status is the communal commitment to relating to and / or using the object in question according to a designated function." |
|`crm:E52_Time-Span` |“	This class comprises abstract temporal extents, in the sense of Galilean physics, having a beginning, an end, and a duration.”  See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E52_Time-Span |
|`crm:E5_Event` | "This class comprises distinct, delimited and coherent processes and interactions of a material nature, in cultural, social or physical systems, involving and affecting instances of E77 Persistent Item in a way characteristic of the kind of process. Typical examples are meetings, births, deaths, actions of decision taking, making or inventing things, but also more complex and extended ones such as conferences, elections, building of a castle, or battles." |
|`crm:E36_Visual_Item` |“This class comprises the intellectual or conceptual aspects of recognisable marks, images and other visual works”. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E36_Visual_Item |
|`crm:E80_Part_Removal`| “This class comprises the activities that result in an instance of E18 Physical Thing being decreased by the removal of a part”. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E80_Part_Removal |
|`crm:E79_Part_Addition` |“This class comprises activities that result in an instance of E18 Physical Thing being increased, enlarged or augmented by the addition of a part”. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E79_Part_Addition |
|`crm:E11\_Modification` | “This class comprises instances of E7 Activity that are undertaken to create, alter or change instances of E24 Physical Human-Made Thing.” See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E11_Modification |
|`crm:E24_Physical_Human-Made_Thing` |“This class comprises all persistent physical items of any size that are purposely created by human activity.”  See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E24_Physical_Human-Made_Thing |
|`crm:E55_Type` |“This class comprises concepts denoted by terms from thesauri and controlled vocabularies used to characterize and classify instances of CIDOC CRM classes”  See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E55_Type |
|`ga:Storyline` | “Storyline is a UFO:ComplexEvent that can be split into (i) ga:Object-Storyline, which is composed of participations of a single UFO:Object, and (ii) ga:Bundle-Storyline (Kublers’ “fibers of duration”), in which two or more UFO:Objects participate." See the UML model of Storylines defined in [1]|


## New properties

| Property | Domain     | Range        |            Description              |
|-------|-----|--------|----------------|
| `:conceptuallyModifies`| `:ConceptualVariation`| `crm:E36_Visual_Item` | The property relates the :ConceptualVariation to the Visual Item it modifies, i.e., the version of the work before the intervention |
|`:createsConceptualVersion` | `:ConceptualVariation` | `crm:E36_Visual_Item` | The property relates the :ConceptualVariation to the Visual Item version resulting from intervention |
|`:createsPhysicalVersion` | `crm:E11_Modification` | `crm:E36_Visual_Item` | The property relates the crmE11 Modification to the physical version resulting from the intervention |
|`:manifestsIn` | `crm:E24_Physical_ human_made_Thing` | `crm:E24_Physical _human_made_Thing` | The property relates a CH artifact to the physical versions that are created by a physical act that consistently modifies the artifact but without affecting its identity. It is the result of the action of a `crm:E11_Modification` that generates a new version of the item (and not a fully new item). | 




## Reused properties

| Property | Domain     | Range        |        Description        |
| ---------| -------| -------| -----------| 
| `aaao:ZP113_has_ successor_status` | `aaao:ZE1_ Institutional_Fact` | `aaao:ZE1_ Institutional_Fact` | "This property links one instance of institutional fact with another where the latter succeeds the former as a formal continuation." | 
| `aaao:ZP111_initiated` | `crm:E5_Event` | `aaao:ZE1_ Institutional_Fact` | "This property is used to connect the instance of event to the instance of institutional fact which it brought into existence by fiat thanks to its accordance to a socially defined norm. " | 
|`dul:precedes` | `dul:Entity` | `dul:Entity` |A relation between entities, expressing a 'sequence' schema” |
|`crm:P65_shows _visual_item` | `crm:E24_Physical _Human-Made_Thing` | `crm:E36_Visual_Item` | This property documents an instance of E36 Visual Item shown by an instance of E24 Physical Human-Made Thing. In the current model, it is used to relate the physical part of the object to the immaterial, visual one. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/P65_shows_visual_item |
|`crm:P31_has_modified` | `crm:E11_Modification` | `crm:E18_Physical_Thing` |“This property identifies the instance of E18 Physical Thing modified in an instance of E11 Modification.” It is superproperty of `crm:P110_augmented` and `crm:P112_diminished`. |
| `crm:P110_augmented` | `crm:E79_Part_Addition` | `crm:E18_Physical_Thing` | “This property identifies the instance of E24 Physical Human-Made Thing that is added to (augmented) in an instance of E79 Part Addition” |
|`crm:P113_removed` | `crm:E80_Part_Removal` | `crm:E18_Physical_Thing` | “This property identifies the instance of E18 Physical Thing that is removed during an instance of E80 Part Removal activity.” It is subproperty of `crm:P112_diminished`.|
|`crm:P112_diminished` | `crm:E80_Part_Removal` | `crm:E18_Physical_Thing` |“This property identifies the instance of E18 Physical Thing that was diminished by an instance of E80 Part Removal.” |
|`crm: P111_added` | `crm:E79_Part_Addition` | `crm:E18_Physical_Thing` | “This property identifies the instance of E18 Physical Thing that is added during an instance of E79 Part Addition activity”  |
|`crm:P12i_ was_present_at` | `crm:E77_Persistent_Item` | `crm:E5_Event` | “This property describes the active or passive presence of an E77 Persistent Item in an instance of E5 Event without implying any specific role.” In this context, it is reused to indicate the participation of an object (endurant) in a storyline (perdurant). See the full scope at: http://www.cidoc-crm.org/cidoc-crm/P12i_was_present_at |
|`crm:crm:P4_has_time-span` | `crm:E2_Temporal_Entity` | `crm:E52_Time-Span` | “This property associates an instance of E2 Temporal Entity with the instance of E52 Time-Span during which it was on-going”. See the full scope at: http://www.cidoc-crm.org/cidoc-crm/P4_has_time-span |



## References and notes

[1] van den Heuvel, C., & Zamborlini, V. (2021). Chapter 6. Modeling and Visualizing Storylines of Historical Interactions. Kubler’s Shape of Time and Rembrandt’s Night Watch. In R. P. Smiraglia & A. Scharnhorst (Eds.), *Linking Knowledge* (pp. 99–141). Ergon – ein Verlag in der Nomos Verlagsgesellschaft. https://doi.org/10.5771/9783956506611-99  
