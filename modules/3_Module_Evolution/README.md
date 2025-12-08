# Evolution Module overview
The module to express the evolution of material and immaterial objects and their functions combines DOLCE+ D&S Ultralite with CIDOC-CRM and GA Storylines. It describes three types of evolution, namely the evolution of the function, of the material, and of immaterial aspects of the object in question.  
The change of the function of an object is described through the class dul:Transition, subclass of dul:Situation, which is aimed at defining changes of a state, creating a previous and a following situation. As the previously introduced :ObjectInSituation class is a subclass of Situation, it can be reused in combination with a Transition to indicate the change of situation in which the object appears. The two :ObjectInSituation instances shall be related respectively to the previous and the new :Function adopted by the object through the relation :includesObjectFunction.  
CIDOC-CRM is reused to describe the physical change of the object. crm:E79_Part_Adition and crm:E80_Part_Removal indicate that a physical part that was added or removed from the object (respectively through the relations crm:P111 added and crm:P113 removed), augments or diminishes (crm:P110 augmented/crm:P11 diminishes) the same object, but that is preserves its identity. On the other hand, crm:E81_Transformation indicates that the physical modification had an impact on the identity of the object, therefore transforming the object into a new one.  The property :manifestsIn is newly introduced to relate the same physical object to multiple physical versions of it. 
The immaterial changes to the immaterial part of the object, namely, the visual representation (crm:E36 Visual Item), are described by the class class :ConceptualVariation, which modifies (:modifies) a previous version and creates a new one (:creates).   
The evolution of material and immaterial variations of the object can be modeled by reusing the GA model of storylines [1], in which the storyline is defined as a chain of events (perdurants) in which the observed CH object participates.





## New classes

| `Class` | `Alignment`|`            Description             `|
|------------|--------|----------------|
| :ConceptualVariation | subclass of crm:E7_Activity | The class identifies an activity that modifies immaterial visual traits of a CH object, such as the subject depicted, creating two versions of the immaterial object, which correspond to the version preceding the intervention and the one resulting from it. | 



## Reused classes
| `Name `| `          Description           `|
|-----------|----------------|
|dul:Transition | “A transition is a Situation that creates a context for three TimeInterval(s), two additional different Situation(s), one Event, one Process, and at least one Object: the Event is observed as the cause for the transition, one Situation is the state before the transition, the second Situation is the state after the transition, the Process is the invariance under some different transitions (including the one represented here), in which at least one Object is situated.” In the current module, it is reused to describe the changes of an object occurring in specific situations (e.g., a change of function). |
|:ObjectInSituation |“A specific type of Situation in which an object presents special, relevant features that cannot be described as a modification of the object (e.g., the change of its function)”. The class is introduced in the Object in Situation module. |
|dul:Process |“placeholder for events that are considered in their evolution” |
|dul:TimeInterval | “A temporal entity with an extent or duration” |
|:Function |“A class identifying the function that an object acquires”. The class is introduced in the Object in Situation module. |
|crm:E36_Visual_Item |“This class comprises the intellectual or conceptual aspects of recognisable marks, images and other visual works”. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E36_Visual_Item |
|crm:E80_Part_Removal| “This class comprises the activities that result in an instance of E18 Physical Thing being decreased by the removal of a part”. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E80_Part_Removal |
|crm:E79_Part_Addition |“This class comprises activities that result in an instance of E18 Physical Thing being increased, enlarged or augmented by the addition of a part”. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E79_Part_Addition |
|crm:E81_Transformation | “This class comprises the events that result in the simultaneous destruction of one or more than one E18 Physical Thing and the creation of one or more than one E18 Physical Thing that preserves recognizable substance and structure from the first one(s) but has fundamentally different nature or identity”. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E81_Transformation |
|crm:E24_Physical_Human-Made_Thing |“This class comprises all persistent physical items of any size that are purposely created by human activity.”  See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E24_Physical_Human-Made_Thing |
|ga:Storyline | “Storyline is a UFO:ComplexEvent that can be split into (i) ga:Object-Storyline, which is composed of participations of a single UFO:Object, and (ii) ga:Bundle-Storyline (Kublers’ “fibers of duration”), in which two or more UFO:Objects participate. “ See the UML model of Storylines defined in [1]|


## New properties

| `Property` | `Domain`     | `Range`        |`             Description             ` |
|-------|-----|--------|----------------|
| :modifies| :ConceptualVariation| crm:E36_Visual_Item | The property relates the :ConceptualVariation to the Visual Item it modifies, i.e., the version of the work before the intervention |
|:creates | :ConceptualVariation | crm:E36_Visual_Item | The property relates the :ConceptualVariation to the Visual Item version resulting from intervention |
|:manifestsIn | crm:E24_Physical_human_made_Thing | crm:E24_Physical_human_made_Thing | The property relates a CH artifact to the physical versions that are created by a physical act that consistently modifies the artifact but without affecting its identity. It is the result of the action of a crm:E81_Transformation that generates a new version of the item (and not a fully new item). | 




## Reused properties

| `Property` | `Domain`     | `Range`        |`        Description        ` |
| ---------| -------| -------| -----------| 
| dul:isSettingFor | dul:Situation | dul:Entity | A relation between situations and entities |
|dul:precedes | dul:Entity | dul:Entity |A relation between entities, expressing a 'sequence' schema” |
|dul:includesTime | dul:Situation | dul:TimeInterval | A relation between situations and time intervals |
|dul:includesEvent | dul:Situation | dul:Event | A relation between situations and events |
|dul:hasRole | dul:Object | dul:Role | A relation between an object and a role |
|dul:isPartOf | dul:Entity | dul:Entity | A relation between any entities, e.g. 'brain is a part of the human body'. |
|dul:isParticipantIn | dul:Object | dul:Event | A relation between an object and a process [2] |
|crm:P65_shows_visual_item | crm:E24_Physical_Human-Made_Thing | crm:E36_Visual_Item | This property documents an instance of E36 Visual Item shown by an instance of E24 Physical Human-Made Thing. In the current model, it is used to relate the physical part of the object to the immaterial, visual one. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/P65_shows_visual_item |
|crm:P113_removed | crm:E80_Part_Removal | crm:E18_Physical_Thing | “This property identifies the instance of E18 Physical Thing that is removed during an instance of E80 Part Removal activity” |
|crm:P112_diminished | crm:E80_Part_Removal | crm:E18_Physical_Thing |“This property identifies the instance of E18 Physical Thing that was diminished by an instance of E80 Part Removal.” |
|crm:P124_transformed | crm:E81_Transformation | crm:E18_Physical_Thing | “This property identifies the instance or instances E18 Physical Thing that have ceased to exist due to an instance of E81 Transformation.The item that has ceased to exist and was replaced by the result of the Transformation. The continuity between both items, the new and the old, is expressed by the links to the common instance of E81 Transformation” |
|crm:P123_resulted_in | crm:E81_Transformation | crm:E18_Physical_Thing | “This property identifies the instance or instances of E18 Physical Thing that are the result of an instance of E81 Transformation” |
| crm:P110_augmented | crm:E79_Part_Addition | crm:E18_Physical_Thing | “This property identifies the instance of E24 Physical Human-Made Thing that is added to (augmented) in an instance of E79 Part Addition” |
|crm: P111_added | crm:E79_Part_Addition | crm:E18_Physical_Thing | “This property identifies the instance of E18 Physical Thing that is added during an instance of E79 Part Addition activity”  |



## References and notes

[1] van den Heuvel, C., & Zamborlini, V. (2021). Chapter 6. Modeling and Visualizing Storylines of Historical Interactions. Kubler’s Shape of Time and Rembrandt’s Night Watch. In R. P. Smiraglia & A. Scharnhorst (Eds.), *Linking Knowledge* (pp. 99–141). Ergon – ein Verlag in der Nomos Verlagsgesellschaft. https://doi.org/10.5771/9783956506611-99  
[2] Note: this property is present in DUL 3.5, available online, but not in version 4.1
