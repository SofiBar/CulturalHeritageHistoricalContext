# Ephemeral Module overview

This module describes how some characteristics of ephemeral events can be captured by existing models and annotations, mainly by reusing the class crm:E5 Event and crm:E52 Time-Span combined with representation of time according to the Extended Date/Time Format (EDTF) defined by the Library of Congress.   
Ephemeral events can be generally described as crm:E5_Event instances. The duration of a temporal entity can be expressed through a crm:E52 Time Span class, representing abstract temporal extents. It is noteworthy that E52 Time Span does not express a computable time interval itself, but a description of the time extent of an observed phenomenon. Therefore, when information about the start, end, or duration of an event is present, the Time Ontology and the EDTF Ontology, which specifies the Time Ontology with unknown and uncertain times according to the Extended Date/Time Format (EDTF) Specification created by the Library of Congress. In particular, the qualifiers “?”, “\~” and “%” are included in the string indicating a date to mean “uncertain” (e.g., “1540?”), “approximate” (e.g., “1540\~”), and “uncertain” or “approximate” (e.g., “1540%”), are particularly useful in the context of the description of uncertainty related to ephemeral events. Furthermore, periods having an unknown beginning or end can be specified through an empty string (e.g., “‘1540/”), and periods having an open start or end are represented with two dots (e.g., “‘1540/..”).   
 The concept of ephemerality is also used to describe objects that are intentionally created to be temporary. For this reason, it is suggested to use type (crm:E55 Type) combined with the available terms for the description of ephemeral provided by the Getty Art and Architecture Thesaurus (AAT), which includes descriptors for ephemeral art and architecture.   
Specific types of ephemeral events and experiences, including odors, can be described by reusing the ODEuropa data model.   






## Reused classes
| `Name `| `          Description           `|
|-----------|----------------|
|`crm:E5_Event` | “This class comprises distinct, delimited and coherent processes and interactions of a material nature, in cultural, social or physical systems, involving and affecting instances of E77 Persistent Item in a way characteristic of the kind of process.” See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E5_Event|
|`crm:E52_Time_Span` |Abstract temporal extents, having a beginning, an end, and a duration. No semantic connotations are attributed to them. See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E52_Time-Span  
|`crm:E24_Physical_Human-Made_Thing`|“This class comprises all persistent physical items of any size that are purposely created by human activity.”  See the full scope note at: http://www.cidoc-crm.org/cidoc-crm/E24_Physical_Human-Made_Thing |
|`crm:E39_Actor` |“This class comprises people, either individually or in groups, who have the potential to perform intentional actions of kinds for which someone may be held responsible.” |
|`crm:E55_Type` |“This class comprises concepts denoted by terms from thesauri and controlled vocabularies used to characterize and classify instances of CIDOC CRM classes.” |
|`time:TemporalEntity` |“A temporal interval or instant” |
|`time:Interval` |“A temporal entity with an extent or duration” |
|`time:Instant`| “A temporal entity with zero extent or duration” |
|`od:L12_Smell_Emission` |“This class comprises events in which a specific smell has been generated, either by human intervention or because of natural phenomena”  |
|`od:L11_Smell` |“This class comprises all olfactory stimuli, or smells, considered as unique and un-repeatable, possibly existing in a specific time and place, to not be confused with possible generalisation”|
|`od:L13_Olfactory_Experience` |“This class comprises activities in which an actor (human or animal) is perceiving a smell”|





## Reused properties

| Property | Domain     | Range        |        Description         |
| ---------| -------| -------| -----------| 
| `crm:P4_has_time-span` |  `crm:E2_Temporal_Entity` |  `crm:E52_Time-Span` | “This property associates an instance of E2 Temporal Entity with the instance of E52 Time-Span during which it was on-going” |
|`crm:P82_at_some_time_within` |  `crm:E52_Time-Span` |  `crm:E61_Time_Primitive` | “This property describes the maximum period of time within which an E52 Time-Span falls.” |
|`crm:P81_ongoing_throughout` |  `crm:E52_Time-Span`|  `crm:E61_Time_Primitive` |“This property associates an instance of E52 Time-Span with an instance of E61 Time Primitive specifying a minimum period of time covered by it.” |
|`crm:P79_beginning_is_qualified_by`|  `crm:E52_Time-Span` |  `crm:E62` |  “This property associates an instance of E52 Time-Span with a note detailing the scholarly or scientific opinions and justifications about the certainty, precision, sources etc. of its beginning.” |
|`crm:P80_end_is_qualified_by` |  `crm:E52_Time-Span` |  `crm:E62` | “This property associates an instance of E52 Time-Span with a note detailing the scholarly or scientific opinions and justifications about the end of this time-span concerning certainty, precision, sources etc.” |
|`crm:P11_had_participant` |  `crm:E5_Event` |  `crm:E39_Actor` | “This property describes the active or passive participation of instances of E39 Actors in an instance of E5 Event.” |
|`crm:P2_has_type` |  `crm:E1_Entity` |  `crm:E55_Type` | “This property allows sub typing of CIDOC CRM entities –a form of specialisation – through the use of a terminological hierarchy, or thesaurus” |
|`crm:P10_falls_within` |  `crm:E92_SpacetimeVolume` |  `crm:E92_SpacetimeVolume` | “This property associates an instance of E92 Spacetime Volume with another instance of E92 Spacetime Volume that falls within the latter. In other words, all points in the former are also points in the latter” |
|`time:before`  |  `time:TemporalEntity` |  `time:TemporalEntity` |“Gives directionality to time. If a temporal entity T1 is before another temporal entity T2, then the end of T1 is before the beginning of T2.” |
|`time:after`|  `time:TemporalEntity` |  `time:TemporalEntity` |“Gives directionality to time. If a temporal entity T1 is after another temporal entity T2, then the beginning of T1 is after the end of T2.” |
|`time:hasEnd` |  `time:TemporalEntity` |  `time:Instant` | “End of a temporal entity” |
|`time:hasBeginning` |  `time:TemporalEntity` |  `time:Instant`  |“Beginning of a temporal entity” |
|`edtfo:hasEDTFDateTimeDescription` |   `time:TimeInterval`  |  EDTF datatype |“Value of an interval, expressed using EDTF” |
| `od:F1_generated` |   `od:L2_Stimulus_Generation` |   `od:L1_Sensory_Stimulus` |“This property associates an instance of L2 Stimulus Generation with the L1 Sensory Stimulus which was created by the event.”|
|`od:F2_perceived` |  `od:L3_Sensory_Experience` |  `od:L1_Sensory_Stimulus`  |“This property associates an instance of L3 Sensory Experience with the L1 Sensory Stimulus which was experienced” |
|`od:F6_evoked`|  `od:L3_Sensory_Experience` | |“This property associates an instance of L3 Sensory Experience with a (material or conceptual) entity which is evoked during the experience itself. This includes memories of people or situations, comparison to similar stimuli, references, etc”  |



## Notes
Definitions of terms from the reused ontologies are taken from the respective documentations. 