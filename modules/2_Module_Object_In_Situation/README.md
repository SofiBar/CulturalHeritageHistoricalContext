# Object in Situation Module overview

The Object in Situation module represents the object in its context(s) according to the theory proposed by Anderson. This module meets Anderson’s description of the object's interaction within the belief system, which gives it its specific functions and meanings. The object’s functions and social meanings can vary across time and space, and according to the situation, event, or culture in which they are used. To this end, the class `aaao:ZE5_Function_Status` is reused. It represents the function ascribed to the object by a community as an insitutional fact of a temporal nature. 

As CH immaterial practices are often repeated over time, in a regular or irregular way, this module extends DOLCE, and in particular the Recurrent Event Series pattern, to frame the situations in which an object acquires a specific function in the context of events repeating over time. This is done through the introduction of the `:ObjectInRecurrentEvent` class and its subclasses. 


## New classes

| Class | Alignment|            Description          |
|------------|--------|----------------|
|`:ObjectInRecurrentEvent` | subclass of `dul:Situation`, `dul:Collection` | Objects observed in situations of events repeated over time, either in regular or irregular intervals, presenting unifying characteristics. |
|`:ObjectInRecurrent IrregularEvent`  | subclass of :ObjectInRecurrentEvent | A situation grouping events in which the same object participates having similar, unifying characteristics over time (e.g., function). |
|`:ObjectInRecurrent RegularEvent` | subclass of `:ObjectInRecurrentEvent`; `owl:sameAs res:RecurrentEventSeries` | A situation in which unifying characteristics of events regularly recurring over time are identified, and the time interval with which they are repeated can be indicated.  |
|`:Function` | subclass of `crm:E55_Type` | A class identifying the function that an object acquires |
|`:PracticalFunction` | subclass of `:Function` | A class identifying the practical function that an object acquires (e.g., the “drinking” function of a vessel)|
|`:SocialFunction` | subclass of `:Function` | A class identifying the socially attributed, non strictly practical function that an object acquires (e.g., the healing function of St. Servatius cup in a catholic context) |

## Reused classes
| Name |           Description           |
|-----------|----------------|
|`aaao:ZE5_Function Status` | "An instance of function status is the collective ascription of an operative functionality to an object by a community. The substance of the function status is the communal commitment to relating to and / or using the object in question according to a designated function." |
|`crm:E74_Group` | "This class comprises any gatherings or organizations of human individuals or groups that act collectively or in a similar way due to any form of unifying relationship." |
|`crm:E5_Event` | "This class comprises distinct, delimited and coherent processes and interactions of a material nature, in cultural, social or physical systems, involving and affecting instances of E77 Persistent Item in a way characteristic of the kind of process. Typical examples are meetings, births, deaths, actions of decision taking, making or inventing things, but also more complex and extended ones such as conferences, elections, building of a castle, or battles." |
|`res:TimePeriod` | Class indicating the “time period that has typically to elapse before the next event is held, which is usually approximate (e.g. yearly, monthly, etc.), and is different from the actual time between two events, which can be derived from the time intervals computed between any two members”. For a full description, see [1] |
|`dul:EventType` | "A Concept that classifies an Event . An event type describes how an Event should be interpreted, executed, expected, seen, etc., according to the Description that the EventType isDefinedIn (or used in)" |
| `:HistoricalFrame` |Class, defined in the Historical Frame module, which represents the socio-cultural context in space-time that is the context of the observed object.|





## New properties

| Property | Domain     | Range       |        Description        |
|-------|-----|--------|----------------|
|`:hasFunction`  |  `crm:E1_Entity`  |  `crm:E55_Type` |Property expressing the function that a CH object has. It is a shortcut for the longer path `aaao:ZE5_Function Status` `aaao:ZP14_has_functional_subject`  `crm:E1_Entity`; `aaao:ZP15 _ascribes_function` `crm:E55_Type`. It is declared as subroperty of `crm:P2_has_type` and as a superproprerty of `crm:P103_was_intended_for`and `crm:P101_had_as_general_use`, which add more detail to the usage or function that the object has.  |
| `:includesEventsOfType` |  `:ObjectInRecurrentEvent`  |  `dul:EventType` | Relate the event series with the type of event that is included (e.g., mass, procession).|
`:hasMemberEvent`|  `ObjectInRecurrentEvent`  |  `crm:E5_Event` | Property to indicate the events of a series based  on the model of the Recurrent Situation and Recurrent Event Series ODPs, which property cannot be directly reused as they have a different domain.|
|`:includesFact`  | `:ObjectInRecurrentEvent`  |  `aaao:ZE1_Institutional_Fact` |Property expressing the fact that the indicated institutional fact (for example, the fact that the CH object holds a function) is included in the situation that represents a series of events repeating over time.  |



## Reused properties

| Property | Domain     | Range        |                      Description                        |
| ---------| -------| -------| ----------------------------------| 
| `aaao:ZP14_has_ functional_subject` | `aaao:ZE5_ Function_Status` | `crm:E1_Entity` | "This property is used to indicate the entity for which a certain functional classification is taken to hold by the instance of functional status." [3] | 
| `aaao:ZP15_ ascribes_function` | `aaao:ZE5_ Function_Status` | `crm:E55_Type` | "This property is used to indicate the type of function which is indicated as holding for the subject of the function status." [3] | 
| `aaao:Z75_applies _for_context` | `aaao:ZE1_ Institutional_Fact` | `crm:E5_Event` | "This property is used to indicate an event context which limits the temporal scope within which an instance of institutional fact is meant to hold. When indicated the event context stands as the frame in which the institutional fact is held to be valid by the associated group for whom it has significance." [3] | 
| `aaao:ZP4_holds_for` | `aaao:ZE1_ Institutional_Fact` | `crm:E74_Group` | "This property is used to indicate the community or group for whom an instance of institutional fact holds. Institutional facts have identity only relative to some group for whom they have a significance as formulated through a chosen symbolic system. "[3] | 
| `rss:hasUnifyingFactor` | `dul:Collection` | `owl:Thing` | Property relating a collection to the recognizable patterns shared by all the members of a series, unifying them. For a more detailed description, see [2] | 
| `res:hasTimePeriod` | `res:RecurrentEventSeries` | `res:TimePeriod` | Property relating a recurrent event series to the time frequency with which it occurs. For a full definition, see [1] | 
| `:hasContext` | `crm:E1_Entity` | `:HistoricalFrame` | Property defined in the Historical Frame module to relate the observed object, or the situations and events in which it appears, to a Historical Frame. In this context, it is reused to express the frame in which the function status is considered being valid, in a broader sense than the property `aaao:Z75_applies _for_context`, as it doesn't force to specify a specific event in which the function occurs.| 



## References
[1] Carriero, V. A., Gangemi, A., Nuzzolese, A. G., & Presutti, V. (2019). An Ontology Design Pattern for Representing Recurrent Events. *WOP@ ISWC*, 59–70. https://ceur-ws.org/Vol-2459/pattern1.pdf  

[2] Carriero, V. A., Gangemi, A., Nuzzolese, A. G., & Presutti, V. (2021). An Ontology Design Pattern for representing Recurrent Situations. In E. Blomqvist, T. Hahmann, K. Hahmann, P. Hitzler, R. Hoekstra, R. Mutharaju, M. Poveda-Villalón, C. Shimizu, M. G. Skjæveland, M. Solanki, V. Svátek, & L. Zhou (Eds.), *Advances in Pattern-Based Ontology Engineering* (pp. 166–182). IOS Press Ebooks. https://doi.org/10.3233/SSW210013

[3] https://ontome.net/namespace/336 