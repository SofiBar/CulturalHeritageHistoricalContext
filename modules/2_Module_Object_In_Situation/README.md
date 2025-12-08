# Object in Situation Module overview

The Object in Situation module represents the object in its context(s) according to the theory proposed by Anderson. This module meets Anderson’s description of the object's interaction within the belief system, which gives it its specific functions and meanings. The object’s functions and social meanings can vary across time and space, and according to the situation, event, or culture in which they are used. To this end, the class :ObjectInSituation, declared as a subclass of dul:Situation, is introduced. It represents every observable Situation, intended as a relational context, in which an object, related to it through the property dul:includesObject, acquires specific characteristics, such as a new function.
Further newly created subclasses describe whether the object acquires specific characteristics in single or repeated events. 


## New classes

| `Class` | `Alignment`|`            Description             `|
|------------|--------|----------------|
|:ObjectInSituation | subclass of dul:Situation | A specific type of Situation in which an object presents special, relevant features that cannot be described as a modification of the object (e.g., the change of its function). It is meant to be related to a :HistoricalFrame which provides the relation to the belief system in which the object is situated or to a dul:Event in which such characteristics are shown. |
|:ObjectInEvent | subclass of :ObjectInSituation | A relational context representing the CH object and the event, unique or repeated over time,  in which the object presents special, relevant features (e.g., a specific function). |
|:ObjectInRecurrentEvent | subclass of :ObjectInSituation, dul:Collection | Objects observed in situations of events repeated over time, either in regular or irregular intervals, presenting unifying characteristics. |
|:ObjectInUniqueEvent  | Subclass of :ObjectInEvent | A situation to observe certain traits of an object present in an event that occurs only once (e.g., a function that the object acquiress in that specific event). |
|:ObjectInRecurrent IrregularEvent  | subclass of :ObjectInRecurrentEvent | A situation grouping events in which the same object participates having similar, unifying characteristics over time (e.g., function). |
|:ObjectInRecurrentRegularEvent | subclass of :ObjectInRecurrentEvent; owl:sameAs res:RecurrentEventSeries | A situation in which unifying characteristics of events regularly recurring over time are identified, and the time interval with which they are repeated can be indicated.  |
|:Function | subclass of dul:Role | A class identifying the function that an object acquires (e.g., the “drinking” function of a vessel or a liturgic function of a religious object) |
|:PracticalFunction | subclass of :Function | A class identifying the practical function that an object acquires (e.g., the “drinking” function of a vessel)|
|:SocialFunction | subclass of :Function | A class identifying the socially attributed, non strictly practical function that an object acquires (e.g., the healing function of St. Servatius cup in a catholic context) |

## Reused classes
| `Name `| `          Description           `|
|-----------|----------------|
|dul:Object | Any physical, social, or mental object, or a substance |
|dul:Event | Any physical, social, or mental process, event, or state. For a full description, see http://www.ontologydesignpatterns.org/ont/dul/DUL.owl |
|res:TimePeriod | Class indicating the “time period that has typically to elapse before the next event is held, which is usually approximate (e.g. yearly, monthly, etc.), and is different from the actual time between two events, which can be derived from the time intervals computed between any two members”. For a full description, see [1] |
| :HistoricalFrame |Class, defined in the Historical Frame module, which represents the socio-cultural context in space-time that is the context of the observed object.|





## New properties

| `Property` | `Domain`     | `Range`        |`        Description        ` |
|-------|-----|--------|----------------|
| :includesEventsOfType |  :ObjectInSituation  |  dul:EventType | Relate the event series with the type of event that is included (e.g., mass, procession). It is a property chain for :hasMemberEvent o dul:hasEventType.
:hasMemberEvent|  ObjectInRecurrentEvent  |  dul:Event | Property to indicate the events of a series based  on the model of the Recurrent Situation and Recurrent Event Series ODPs, which property cannot be directly reused as they have a different domain.|
|:includesObjectFunction  |  :ObjectInSituation  |  :Function |Property to specify which function an object acquires in a specific situation. It is a part of a path from dul:Object through :ObjectInSituation extends the relation dul:Object, dul:hasRole, dul:Role. |



## Reused properties

| `Property` | `Domain`     | `Range`        |`        Description        ` |
| ---------| -------| -------| -----------| 
| dul:hasRole | dul:Object | dul:Role | A relation between an object and a role| 
| dul:includesObject | dul:Situation |  dul:Object | A relation between situations and objects| 
| dul:includesEvent | dul:Situation | dul:Event | A relation between situations and events| 
| rss:hasUnifyingFactor | dul:Collection | owl:Thing | Property relating a collection to the recognizable patterns shared by all the members of a series, unifying them. For a more detailed description, see [2] | 
| :hasContext | crm:E1_Entity | :HistoricalFrame | Property defined in the Historical Frame module to relate the observed object, or the situations and events in which it appears, to a Historical Frame | 



## References
[1] Carriero, V. A., Gangemi, A., Nuzzolese, A. G., & Presutti, V. (2019). An Ontology Design Pattern for Representing Recurrent Events. *WOP@ ISWC*, 59–70. https://ceur-ws.org/Vol-2459/pattern1.pdf  
[2] Carriero, V. A., Gangemi, A., Nuzzolese, A. G., & Presutti, V. (2021). An Ontology Design Pattern for representing Recurrent Situations. In E. Blomqvist, T. Hahmann, K. Hahmann, P. Hitzler, R. Hoekstra, R. Mutharaju, M. Poveda-Villalón, C. Shimizu, M. G. Skjæveland, M. Solanki, V. Svátek, & L. Zhou (Eds.), *Advances in Pattern-Based Ontology Engineering* (pp. 166–182). IOS Press Ebooks. https://doi.org/10.3233/SSW210013