#####Use Case ID: UC-PCS62
####Use Case Name: List Medications

**Level:**                     User Level Goal

**Primary Actors:**            Doctor/ Physician/ Clinician 

**Stakeholders:**              Patient Charting User

**Purpose:**                   The main intent of this use case is to list the medications associated with particular patient.

**Pre Condition:**             Doctor/ Physician/ Clinician must be identified and authenticated.  

**Post Condition:**            Medication listed successfully.  

**Frequency of Occurrence:**   High

**Priority:**                  High
__________________________________________________________
**Main Success Scenario: (List Medications)**

1.	Physician will request to list the medication of particular patient.
2.	System will respond with the current list of medications.

**Alternate Flow**

1.	Physician will request for medication list.
2.	System will respond with patient takes no medication.

_______________________________________________________________
**Open Issues**

-NA-
_______________________________________________________________
**Reference Hl7 V3 Interaction Identifiers (Domain: Pharmacy):**

-NA-
_______________________________________________________________
**Reference CCHIT Criteria:**

IP 06.11, FN 06.02, FN 06.05
_______________________________________________________________
**EHR Functional Criteria:**

DC 1.4.2

_______________________________________________________________
**Reference Hl7 RMIM (Domain: Pharmacy):** [More Details](http://www.hl7.org/implement/standards/product_brief.cfm?product_id=306)

-NA-

_______________________________________________________________
**Reference FHIR Resource:** [More Details](http://www.hl7.org/implement/standards/fhir/resourcelist.html)

![image](https://f.cloud.github.com/assets/4283040/1379484/4c27c2ce-3aef-11e3-9a31-adc14ba004a4.png)
_______________________________________________________________
**Reference CDA Template:** [More Details](http://www.hl7.org/Special/committees/structure/index.cfm)

Section Level Template **"Medications Section (entries optional) (V2)"**
_______________________________________________________________
**Reference OpenEHR Archetypes (Version 1.4):** [More Details](http://www.openehr.org/ckm/)

Procedure (openEhr Archetype)
```Archetype
archetype (adl_version=1.4)
	openEHR-EHR-COMPOSITION.medication_list.v1
concept
	[at0000]	-- Medication List
language
	original_language = <[ISO_639-1::en]>
	translations = <
		["es-ar"] = <
			language = <[ISO_639-1::es-ar]>
			author = <
				["name"] = <"Edgardo Vazquez">
				["organisation"] = <"VinculoMedico">
				["email"] = <"edgardo.vazquez@vinculomedico.com">
			>
			accreditation = <"Medical Doctor">
		>
	>
description
	original_author = <
		["name"] = <"Chunlan Ma">
		["organisation"] = <"Ocean Informatics, Australia">
		["email"] = <"chunlan.ma@oceaninformatics.com">
		["date"] = <"2006-11-06">
	>
	details = <
		["en"] = <
			language = <[ISO_639-1::en]>
			purpose = <"To record a persistent and managed list of medicines that are reasonably assumed to be taken by the subject, and that may influence clinical decision-making and care provision. The medicines may be prescribed or acquired 'over the counter'.">
			use = <"Use to record a persistent and managed list of all medicines, both prescribed and 'over the counter', that are assumed to be taken by the subject. 

This list can be utilised as a source of up-to-date medicine data for exchange or as the basis for decision support. 

This list can be comprised of three types of archetype:
- statements about the positive use of medications are recorded using the INSTRUCTION.medication and/or ACTION.medication archetypes; OR
- a statement about the positive exclusion of medication use can be recorded using the specific EVALUATION.exclusion-medication archetype - for example: \"Not currently taking any medications\"; OR
- a statement about no information being available - neither a positive known use of medication nor a positive exclusion - can be recorded using the EVALUATION.absence archetype.

There can be a subtle but important difference between types of medication lists. Some examples include: 'Current Medications' or 'Regular Medications'. A 'Current Medication List' may be regarded as a list of all medicines that the subject would have in their body at a given time, including a stat dose of a medicine that should be considered when prescribing an additional medication to ensure that drug-drug interaction checking continues for the duration of it's physiological influence. A 'Regular Medication List' may only include those medicines that are prescribed or used on a regular and ongoing basis. 
In clinical practice it is common to create Medication Lists that have contextual or temporal constraints, including 'Admission Medication List' and 'Discharge Medication List', which will be accurate at a point in time and not managed.  It is probably better practice to record these explicitly, for example as the result of a query, to record and/or exchange the precise data applicable for that time and place and not use this archeytpe in this situation.
In order for this list to be accurate and safe to use as the basis for decision support activities and for exchange, this Medication List should ideally be curated by a clinician responsible for the health record, rather than managed automatically by the clinical system through business rules alone.">
			keywords = <"medication", "medicine", "list", "ongoing", "drug">
			misuse = <"Not to be used to record non-persisting Medication Lists.
Not to be used to record vaccinations administered.">
			copyright = <"© openEHR Foundation">
		>
		["es-ar"] = <
			language = <[ISO_639-1::es-ar]>
			purpose = <"Registrar un listado gestionado y persistente  de medicaciones razonablemente asumidas como que estan siendo tomadas por la persona, y que pueden influenciar la toma de decisiones y la provision del cuidado. Las medicinas pueden ser precriptas o adquiridas libremente.">
			use = <"Utilizado para registrar un listado persistente y gestionado de todos los medicamentos , tanto los prescriptos como los de venta libre, que se asumen estan siendo tomados por la persona.
Este listado puede ser utilizado como una fuente de actualizacion de data sobre medicamentos para intercambio o como base para una toma de decisiones.
Este listado puede comprender tres tipos de arquetipos:
-los enunciados sobre el uso positivo de medicaciones son registrado utilizando los arquetipos INSTRUCTION. medication y/o ACTION. medication; O - un enunciado positivo sobre una exclusion de medicacion puede ser registrado utilizando el arquetipo específico EVALUATION.exclusion-medication - por ejemplo \" Actualmente no se encuetra tomando medicaciones\"; O
- un enunciado sobre la falta de disponibilidad de iformacion- ni un uso positivo de medicacion ni una exclusion positiva- puede ser registrado utilizando el arquetipo de EVALUATION. absence.
Puede existir una diferencia sutil pero importante entre tipos de listados de medicaciones. Algunos ejemplos incluyen \"Medicacion Presente\" o \"Medicacion Habitual\". Un \"listado de Medicacion Presente\" puede ser considerado como un listado de todas los medicamentos que la persona deberia tener en su cuerpo en un momento determinado, incluyendo una dosis stat de un medicamento que deberia ser considerado cuando se prescribe un medicamento adicional para asegurar que continua el control de interaccion droga-droga durante la duracion de su influencia fisiologica.
Un \"Listado de Medicacion Habitual\" puede incluir solamente aquellos medicamentos que son prescriptos o utilizados de manera regular y permanente.  
En la práctica clinica es comun crear Listado de Medicamentos que tienen una restriccion contextual o temporal, incluyendo 'Listado de Medicamentos en Admision' y 'Listado de Medicamentos en el Alta', los cuales seran precisos en un punto en el tiempo pero no seran gestionados.  Probablemente sea una mejor practica registrar los mismos de manera explicita, por ejemplo como el resultado de un query, registrar y/o intercambiar la data precisa aplicable para esa instancia temporal y lugar y no utilizar este arquetipo en esta situacion.
Con la finalidad que esta lista sea precisa y segura de usar como base de actividades de apoyo a las decisiones y para intercambio, este Listado de Medicamentos deberia idealmente ser curada por el clinico responsable por el registro de la salud, en ves de ser solamente gestionada automaticamente por el sistema clinico a traves de reglas de negocio.
">
			keywords = <"medicacion", "medicina", "listado", "en curso", "droga">
			misuse = <"No debe ser utilizado para el registro de Listado de Medicamentos no persistentes

No debe ser utilizado para registrar vacunaciones administradas.">
			copyright = <"© openEHR Foundation">
		>
	>
	lifecycle_state = <"CommitteeDraft">
	other_contributors = <"Ian McNicoll, Ocean Informatics, United Kingdom", "Sam Heard, Ocean Informatics, Australia", "Sistine Barretto-Daniels, Ocean Informatics, Australia", "Heather Leslie, Ocean Informatics, Australia">
	other_details = <
		["current_contact"] = <"Heather Leslie, Ocean Informatics, heather.leslie@oceaninformatics.com">
		["MD5-CAM-1.0.1"] = <"97B6899EA00EBED30CCE883E100CBFD4">
	>

definition
	COMPOSITION[at0000] matches {	-- Medication List
		category matches {
			DV_CODED_TEXT matches {
				defining_code matches {[openehr::431]}
			}
		}
		content cardinality matches {1..*; unordered} matches {
			allow_archetype INSTRUCTION[at0002] occurrences matches {0..*} matches {	-- Medication Instruction
				include
					archetype_id/value matches {/openEHR-EHR-INSTRUCTION\.medication(-[a-zA-Z0-9_]+)*\.v1/}
			}
			allow_archetype ACTION[at0001] occurrences matches {0..*} matches {	-- Medication Action
				include
					archetype_id/value matches {/openEHR-EHR-ACTION\.medication(-[a-zA-Z0-9_]+)*\.v1/}
			}
			allow_archetype EVALUATION[at0003] occurrences matches {0..*} matches {	-- Exclusion Statement
				include
					archetype_id/value matches {/openEHR-EHR-EVALUATION\.exclusion-medication(-[a-zA-Z0-9_]+)*\.v1/}
			}
			allow_archetype EVALUATION[at0004] occurrences matches {0..*} matches {	-- Absent Information
				include
					archetype_id/value matches {/openEHR-EHR-EVALUATION\.absence(-[a-zA-Z0-9_]+)*\.v1/}
			}
		}
	}
ontology
	term_definitions = <
		["en"] = <
			items = <
				["at0000"] = <
					text = <"Medication List">
					description = <"A persistent and managed list of medications that are reasonably assumed to be taken by the subject, and that may influence clinical decision-making and care provision.">
				>
				["at0001"] = <
					text = <"Medication Action">
					description = <"Details about the medications actively in use, including the pathway state.">
					comment = <"For example: details about the actual Medication prescribed or administered, which may be subtley different to the original Medication order itself for various reasons.">
				>
				["at0002"] = <
					text = <"Medication Instruction">
					description = <"Details about the medications ordered for use.">
				>
				["at0003"] = <
					text = <"Exclusion Statement">
					description = <"Positive statement about the known exclusion of medication use.">
				>
				["at0004"] = <
					text = <"Absent Information">
					description = <"Positive statement that no information is available about medication use.">
				>
			>
		>
		["es-ar"] = <
			items = <
				["at0000"] = <
					text = <"Listado de Medicacion">
					description = <"Un listado persitente y gerstionado de medicamentos que razonablemente se asume son tomados por la persona, y que pueden influenciar la toma de decisiones clinicas o la provision de cuidado.">
				>
				["at0001"] = <
					text = <"Accion de la Medicacion">
					description = <"Detalles sobre la medicacion activamente utilizada, incluyendo el estado de la via">
					comment = <"Por ejemplo: detalles sobre la Medicacion actual prescripta o administrada, que podria ser sutilmente diferente a la Medicacion orginal indicada  por varias razones.">
				>
				["at0002"] = <
					text = <"Instrucciones sobre medicamentos">
					description = <"Detalles para utilizar sobre las medicaciones indicadas">
				>
				["at0003"] = <
					text = <"Enunciados de exclusion">
					description = <"Enunciados positivos sobre las exclusiones conocidas de la medicacion utilizada.
">
				>
				["at0004"] = <
					text = <"Informacion Ausente">
					description = <"Enunciado positivo que no hay informacion disponible sobre el uso de la medicacion
">
				>
			>
		>
>
```
