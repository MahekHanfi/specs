#####Use Case ID: UC-PCS49
#####Use Case Name: Get Alert Criteria

**Level:**                     User Level Goal

**Primary Actors:**            Physician

**Stakeholders:**              Physician, Healthcare Provider

**Purpose:**                   The main intent of this use case is to get alert criteria.

**Pre Condition:**             Physician must be identified and authenticated.

**Post Condition:**            Alert Criteria details will be displayed successfully.

**Frequency of Occurrence:**   High
__________________________________________________________
**Main Success Scenario: (Get Alert Criteria)**

1. Physician requests to get alert criteria details.
2. System displays the list of alert criteria related to a guideline.
3. Physician selects appropriate alert criteria.
4. System displays the details of alert criteria.

________________________________________________________________________
**Reference Hl7 V3 Interaction Identifiers:**

N/A
_______________________________________________________________
**Reference CCHIT Criteria:**

N/A
_______________________________________________________________
**Reference Hl7 RMIM :** [More Details](http://www.hl7.org/implement/standards/product_brief.cfm?product_id=306)

N/A

_______________________________________________________________
**Reference FHIR Resource:** [More Details](http://www.hl7.org/implement/standards/fhir/resourcelist.html)

![alert fhir resource](https://f.cloud.github.com/assets/5391320/1378793/5980c5d4-3ada-11e3-87e2-d958f8f02fdf.png)
_______________________________________________________________
**Reference CDA Template:** [More Details](http://www.hl7.org/Special/committees/structure/index.cfm)

N/A
_______________________________________________________________
**Reference OpenEHR Archetypes (Version 1.4):** [More Details](http://www.openehr.org/ckm/)

Alert (openEhr Archetype)
```Archetype
archetype (adl_version=1.4)
	openEHR-EHR-EVALUATION.alert.v1

concept
	[at0000]	-- Alert
language
	original_language = <[ISO_639-1::en]>
	translations = <
		["de"] = <
			language = <[ISO_639-1::de]>
			author = <
				["name"] = <"Jasmin Buck, Sebastian Garde">
				["organisation"] = <"University of Heidelberg, Central Queensland University">
			>
		>
		["ar-sy"] = <
			language = <[ISO_639-1::ar-sy]>
			author = <
				["name"] = <"Mona Saleh">
			>
		>
	>
description
	original_author = <
		["name"] = <"Sam Heard">
		["organisation"] = <"Ocean Informatics">
		["email"] = <"sam.heard@oceaninformatics.com">
		["date"] = <"2006-04-23">
	>
	details = <
		["de"] = <
			language = <[ISO_639-1::de]>
			purpose = <"Zur Dokumentation beliebiger Warnungen in der Patientenakte">
			use = <"">
			keywords = <"notabene", "Warnung">
			misuse = <"">
			copyright = <"© openEHR Foundation">
		>
		["en"] = <
			language = <[ISO_639-1::en]>
			purpose = <"To record an assertion of potential threat to the welfare of the subject of care, carer or healthcare provider.">
			use = <"Use to record any assertion of potential threat to the welfare of the subject of care, to their carers or to their healthcare providers that needs to be flagged visually in a clinical application or to drive automated clinical decision support.
It will usually be entered manually, but in some clinical systems it may be automatically generated according to business rules and based on existing data or as new data is entered elsewhere in the system.">
			keywords = <"warning", "risk">
			misuse = <"Not to be used for recording notes (nota bene) or routine notifications, recalls or reminders.">
			copyright = <"© openEHR Foundation">
		>
		["ar-sy"] = <
			language = <[ISO_639-1::ar-sy]>
			purpose = <"لتسجيل الإنذارات من أي نوع في السجل الطبي.">
			use = <"*Use to record any assertion of potential threat to the welfare of the subject of care, to their carers or to their healthcare providers that needs to be flagged visually in a clinical application or to drive automated clinical decision support.
It will usually be entered manually, but in some clinical systems it may be automatically generated according to business rules and based on existing data or as new data is entered elsewhere in the system.(en)">
			keywords = <"ملحوظة", "تحذير">
			misuse = <"*Not to be used for recording notes (nota bene) or routine notifications, recalls or reminders.(en)">
			copyright = <"© openEHR Foundation">
		>
	>
	lifecycle_state = <"AuthorDraft">
	other_contributors = <"Gustavo Bacelar, Brazil", "Ian McNicoll, Ocean Informatics, UK", "Heather Leslie, Ocean Informatics, Australia">
	other_details = <
		["MD5-CAM-1.0.1"] = <"1CB0558AE05615742E83030544DBE483">
	>

definition
	EVALUATION[at0000] matches {	-- Alert
		data matches {
			ITEM_LIST[at0001] matches {	-- List
				items cardinality matches {1..*; unordered} matches {
					ELEMENT[at0015] occurrences matches {0..1} matches {	-- Alert
						value matches {
							DV_TEXT matches {*}
						}
					}
					ELEMENT[at0002] occurrences matches {0..1} matches {	-- Category
						value matches {
							DV_TEXT matches {*}
						}
					}
					ELEMENT[at0003] matches {	-- Description
						value matches {
							DV_TEXT matches {*}
						}
					}
					ELEMENT[at0009] occurrences matches {0..1} matches {	-- Status
						value matches {
							DV_CODED_TEXT matches {
								defining_code matches {
									[local::
									at0011, 	-- Active
									at0012, 	-- Inactive
									at0013]	-- Resolved
								}
							}
						}
					}
					ELEMENT[at0004] occurrences matches {0..1} matches {	-- Start Date
						value matches {
							DV_DATE_TIME matches {*}
						}
					}
					ELEMENT[at0010] occurrences matches {0..1} matches {	-- Review Date
						value matches {
							DV_DATE_TIME matches {*}
						}
					}
					ELEMENT[at0014] occurrences matches {0..1} matches {	-- End Date
						value matches {
							DV_DATE_TIME matches {*}
						}
					}
				}
			}
		}
	}


ontology
	term_definitions = <
		["de"] = <
			items = <
				["at0000"] = <
					text = <"Warnung">
					description = <"Informationen, die eine zu behandelnde Person betreffen und besondere Betrachtung eines Klinikers benötigen, bevor über seine/ihre Handlungen entschieden wird, um ein ungewolltes Ereignis zu verhindern, oder Informationen bezüglich der Sicherheit der zu behandelnden Person oder der Gesundheitsdienstleister oder bezüglich besonderer Umstände, die für die Leistungserbringung von Bedeutung sind.">
				>
				["at0001"] = <
					text = <"Liste">
					description = <"@ internal @">
				>
				["at0002"] = <
					text = <"Kategorie">
					description = <"Die Kategorie der Warnung">
				>
				["at0003"] = <
					text = <"Beschreibung">
					description = <"Einzelheiten der Warnung">
				>
				["at0004"] = <
					text = <"Start der Warnung">
					description = <"Datum und Zeitpunkt, zu dem das Problem oder Ereignis begonnen hat">
				>
				["at0009"] = <
					text = <"Zustand">
					description = <"Ein Hinweis, ob die Warnung als aktives oder inaktives Problem angesehen wird">
				>
				["at0010"] = <
					text = <"Kontrollzeitpunkt">
					description = <"Das Datum und der Zeitpunkt, wann die Warnung eine Kontrolle erfordert">
				>
				["at0011"] = <
					text = <"Aktiv">
					description = <"Die Warnung ist aktiv">
				>
				["at0012"] = <
					text = <"Inaktiv">
					description = <"Die Warnung ist momentan inaktiv">
				>
				["at0013"] = <
					text = <"Aufgehoben">
					description = <"Die Warnung wurde aufgehoben">
				>
				["at0014"] = <
					text = <"Ende der Warnung">
					description = <"Das Ende das Warnzeitraumes, falls bekannt">
				>
				["at0015"] = <
					text = <"*New element(en)">
					description = <"**(en)">
				>
			>
		>
		["en"] = <
			items = <
				["at0000"] = <
					text = <"Alert">
					description = <"An assertion of potential threat to the welfare of the subject of care, carer or healthcare provider.">
				>
				["at0001"] = <
					text = <"List">
					description = <"@ internal @">
				>
				["at0002"] = <
					text = <"Category">
					description = <"The category of alert.">
					comment = <"Coding of the category of alert with a terminology is desirable, where possible. For example, Medical Device Insertion; Significant Organism; or Social Circumstance.">
				>
				["at0003"] = <
					text = <"Description">
					description = <"Narrative description of the alert.">
					comment = <"For example, insertion of a medical device such as a pacemaker in left chest wall; presence of a significant organism such as MRSA on swab at last hospital admission; or aggressive dog at home which creates a risk for home visits.">
				>
				["at0004"] = <
					text = <"Start Date">
					description = <"The date and optional time at which the alert became active.">
				>
				["at0009"] = <
					text = <"Status">
					description = <"An indication of whether the alert is considered to be an active, currently inactive, or resolved and not likely to impact on the patient again.">
				>
				["at0010"] = <
					text = <"Review Date">
					description = <"The date and optional time when the alert Status requires review.">
				>
				["at0011"] = <
					text = <"Active">
					description = <"The alert is active.">
				>
				["at0012"] = <
					text = <"Inactive">
					description = <"The alert is not active at present.">
				>
				["at0013"] = <
					text = <"Resolved">
					description = <"The alert has resolved.">
				>
				["at0014"] = <
					text = <"End Date">
					description = <"The date and optional time at which the alert became inactive, if known.">
				>
				["at0015"] = <
					text = <"Alert">
					description = <"Identification of the alert.">
					comment = <"For example, pacemaker, Methiciliin Resistant Staphylococcus Aureus(MRSA), or aggressive dog.">
				>
			>
		>
		["ar-sy"] = <
			items = <
				["at0000"] = <
					text = <"تنبيه">
					description = <"المعلومات المتعلقة بالشخص الذي يستقبل الرعاية و التي قد تحتاج إلى اعتبار خاص من مقدم الرعاية الصحية قبل اتخاذ قرار حول أفعاله/أفعالها بهدف تفادي واقعة صحية غير مرغوب فيها, أو ما يتعلق بسلامة الشخص أو مقدم الرعاية, أو ما يتعلق بالظروف الخاصة المتعلقة بتوصيل الرعاية الصحية.">
				>
				["at0001"] = <
					text = <"*List(en)">
					description = <"*@ internal @(en)">
				>
				["at0002"] = <
					text = <"الفئة">
					description = <"فئة التنبيه">
					comment = <"*Coding of the category of alert with a terminology is desirable, where possible. For example, Medical Device Insertion; Significant Organism; or Social Circumstance.(en)">
				>
				["at0003"] = <
					text = <"الوصف">
					description = <"تفاصيل التنبيه">
					comment = <"*For example, insertion of a medical device such as a pacemaker in left chest wall; presence of a significant organism such as MRSA on swab at last hospital admission; or aggressive dog at home which creates a risk for home visits.(en)">
				>
				["at0004"] = <
					text = <"حالة التنبيه">
					description = <"توقيت و تاريخ بداية القضية أو الواقعة الصحية">
				>
				["at0009"] = <
					text = <"الحالة">
					description = <"إشارة إلى ما إذا كان التنبيه هو لأمر نشط/حالي أو غير نشط/غير حالي">
				>
				["at0010"] = <
					text = <"توقيت المراجعة">
					description = <"الوقت و التاريخ الذان ينبغي أن تتم فيهما المراجعة">
				>
				["at0011"] = <
					text = <"نشط">
					description = <"التنبيه نشط">
				>
				["at0012"] = <
					text = <"غير نشط">
					description = <"التنبيه غير نشط">
				>
				["at0013"] = <
					text = <"تم حله">
					description = <"تم حله">
				>
				["at0014"] = <
					text = <"نهاية التنبيه">
					description = <"نهاية فترة التنبيه إذا عُرِفَت">
				>
				["at0015"] = <
					text = <"*Alert(en)">
					description = <"*Identification of the alert.(en)">
					comment = <"*For example, pacemaker, Methiciliin Resistant Staphylococcus Aureus(MRSA), or aggressive dog.(en)">
				>
			>
		>
	>

```
