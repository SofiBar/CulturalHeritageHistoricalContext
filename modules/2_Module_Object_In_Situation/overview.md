# Object in Situation Module overview

## New classes

| Class | Alignment | Description |
|------------|--------|----------------|
|:ObjectInSituation | subclass of dul:Situation | A specific type of Situation in which an object presents special, relevant features that cannot be described as a modification of the object (e.g., the change of its function). It is meant to be related to a :HistoricalFrame which provides the relation to the belief system in which the object is situated or to a dul:Event in which such characteristics are shown. |
|:ObjectInEvent | | |
|:ObjectInRecurrent Event | subclass of :ObjectInSituation, dul:Collection | Objects observed in situations of events repeated over time, either in regular or irregular intervals, presenting unifying characteristics. |
|:ObjectInUniqueEvent  | Subclass of :ObjectInEvent | A situation to observe certain traits of an object present in an event that occurs only once (e.g., a function that the object acquiress in that specific event). |
|:ObjectInRecurrent IrregularEvent  | subclass of :ObjectInRecurrentEvent | A situation grouping events in which the same object participates having similar, unifying characteristics over time (e.g., function). |
|:ObjectInRecurrentRegularEvent | subclass of :ObjectInRecurrentEvent; owl:sameAs res:RecurrentEventSeries | A situation in which unifying characteristics of events regularly recurring over time are identified, and the time interval with which they are repeated can be indicated.  |
|:Function | subclass of dul:Role | A class identifying the function that an object acquires (e.g., the “drinking” function of a vessel or a liturgic function of a religious object) |
|:PracticalFunction | subclass of :Function | A class identifying the practical function that an object acquires (e.g., the “drinking” function of a vessel)|
|:SocialFunction | subclass of :Function | A class identifying the socially attributed, non strictly practical function that an object acquires (e.g., the healing function of St. Servatius cup in a catholic context) |

## Reused classes


## New properties


## Reused properties