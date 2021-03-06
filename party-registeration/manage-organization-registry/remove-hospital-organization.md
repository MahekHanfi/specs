#####Use Case ID: UC-PRS13
#####Use Case Name: Remove Hospital Organization

**Level:**                     User Level Goal

**Primary Actors:**            Clerk 

**Stakeholders:**              Clerk, Provider, Provider Organization

**Purpose:**                   The main intent of this use case is to remove hospital organization.

**Pre Condition:**             Clerk must be identified and authenticated. 

**Post Condition:**            Hospital organization will be removed successfully.

**Frequency of Occurrence:**   Medium
__________________________________________________________
**Main Success Scenario: (Remove Hospital Organization)**

1. Clerk requests remove hospital organization option.
2. System returns the list of organizations available.
3. Clerk selects an appropriate organization and requests its removal.
4. System removes the specified organization.


________________________________________________________________________
**Reference Hl7 V3 Interaction Identifiers (Domain: Patient Administration):**

PRPM_ST403000UV01
_______________________________________________________________
**Reference CCHIT Criteria:**

N/A
_______________________________________________________________
**Reference Hl7 RMIM (Domain: Personnel Management):** [More Details](http://www.hl7.org/implement/standards/product_brief.cfm?product_id=306)

![prpm_rm402000uv organization event nullify](https://f.cloud.github.com/assets/5391320/1371318/b3f41d66-3a37-11e3-8e2d-a204cb5e70c2.png)
_______________________________________________________________
**Reference FHIR Resource:** [More Details](http://www.hl7.org/implement/standards/fhir/resourcelist.html)

![organization fhir resource](https://f.cloud.github.com/assets/5391320/1371208/be9b2f5a-3a34-11e3-8349-d8c4ec86328a.png)
_______________________________________________________________
**Reference CDA Template:** [More Details](http://www.hl7.org/Special/committees/structure/index.cfm)

N/A
_______________________________________________________________
**Reference OpenEHR Archetypes (Version 1.4):** [More Details](http://www.openehr.org/ckm/)

OpenEHR Archetype: (Organization)

``` Archetype
archetype (adl_version=1.4)
	openEHR-DEMOGRAPHIC-ORGANISATION.organisation.v1

concept
	[at0000]	-- Organização
language
	original_language = <[ISO_639-1::pt-br]>
	translations = <
		["en"] = <
			language = <[ISO_639-1::en]>
			author = <
				["name"] = <"Sergio Miranda Freire">
				["organisation"] = <"Universidade do Estado do Rio de Janeiro - UERJ">
				["email"] = <"sergio@lampada.uerj.br">
			>
		>
	>
description
	original_author = <
		["name"] = <"Sergio Miranda Freire & Rigoleta Dutra Mediano Dias">
		["organisation"] = <"Universidade do Estado do Rio de Janeiro - UERJ">
		["email"] = <"sergio@lampada.uerj.br">
		["date"] = <"22/05/2009">
	>
	details = <
		["pt-br"] = <
			language = <[ISO_639-1::pt-br]>
			purpose = <"Representação dos dados de uma Organização.">
			use = <"Usado em serviços de demografia para coletar dados demográficos sobre uma organização.">
			keywords = <"serviço demográfico", "organização">
			misuse = <"">
			copyright = <"© openEHR Foundation">
		>
		["en"] = <
			language = <[ISO_639-1::en]>
			purpose = <"Representation of an organisation's demographic data.">
			use = <"Used in demographic service to collect demographic data about an organisation.">
			keywords = <"demographic service", "organisation's data">
			misuse = <"">
			copyright = <"© openEHR Foundation">
		>
	>
	lifecycle_state = <"AuthorDraft">
	other_contributors = <"Sebastian Garde, Ocean Informatics, Germany (Editor)", "Omer Hotomaroglu, Turkey (Editor)", "Heather Leslie, Ocean Informatics, Australia (Editor)", "Ian McNicoll, Ocean Informatics, UK (Editor)">
	other_details = <
		["references"] = <"ISO/DTS 27527:2007(E) - Provider Identification - Draft Technnical Specification - International Organization for Standardization">
	>

definition
	ORGANISATION[at0000] matches {	 
		details matches {
			ITEM_TREE[at0001] matches { -- organisation identifiers
				items cardinality matches {1..*; ordered} matches {
					allow_archetype CLUSTER[at0010]	matches {
						include
							archetype_id/value matches {/(provider_identifier)[a-zA-Z0-9_-]*\.v1/}
					}
				}	
			}
		}		
		identities cardinality matches {1..*; ordered} matches {
			allow_archetype PARTY_IDENTITY[at0002] occurrences matches {1..*} matches {	
				include
					archetype_id/value matches {/(organisation_name)[a-zA-Z0-9_-]*\.v1/}
			}
		}
		contacts matches {
			CONTACT[at0003] matches {
				addresses matches {
					allow_archetype ADDRESS[at0030] matches {
						include 
							archetype_id/value  matches {/(address)[a-zA-Z0-9_-]*\.v1/}
							archetype_id/value  matches {/(electronic_communication)[a-zA-Z0-9_-]*\.v1/}
					}
				}
			}
		}
		relationships matches {
			PARTY_RELATIONSHIP[at0004] matches { 
				details matches {
					ITEM_TREE[at0040] matches {
						items cardinality matches {1..*; ordered} matches {
							ELEMENT[at0041] occurrences matches {0..1} matches {	-- type of relationship
								value matches {
				    					DV_TEXT matches {*}
				    					DV_CODED_TEXT matches {
										defining_code matches {[ac0000]}
				    					}
								}		
							}
						}
					}
				}
			}
		}
	}



ontology
	term_definitions = <
		["pt-br"] = <
			items = <
				["at0000"] = <
					text = <"Organização">
					description = <"Organização.">
				>
				["at0001"] = <
					text = <"Documentos">
					description = <"Documentos de Identificação da organização.">
				>
				["at0002"] = <
					text = <"Nome">
					description = <"Identificação da organização - os nomes pelos quais ela é conhecida.">
				>
				["at0003"] = <
					text = <"Contatos">
					description = <"Formas de contactar a organização.">
				>
				["at0004"] = <
					text = <"Relacionamentos">
					description = <"Relacionamentos entre uma organização com outra ou entre uma organização e uma de suas divisões/departamentos, etc.">
				>
				["at0010"] = <
					text = <"Documento">
					description = <"Um documento da organização.">
				>
				["at0030"] = <
					text = <"Endereço">
					description = <"Endereço de contato da organização.">
				>
				["at0040"] = <
					text = <"Detalhes">
					description = <"Detalhes do relacionamento.">
				>
				["at0041"] = <
					text = <"Type of relationship">
					description = <"Tipo de relacionamento entre as duas organizações.">
				>
			>
		>
		["en"] = <
			items = <
				["at0000"] = <
					text = <"Organisation">
					description = <"Organisation demographic data.">
				>
				["at0001"] = <
					text = <"Identifiers">
					description = <"Organisation identifiers.">
				>
				["at0002"] = <
					text = <"Name">
					description = <"Identification - the names the organisation is known by.">
				>
				["at0003"] = <
					text = <"Contacts">
					description = <"Organisation contacts.">
				>
				["at0004"] = <
					text = <"Relationship">
					description = <"Relationship between two organisations or between an organization and one of its division/department, etc.">
				>
				["at0010"] = <
					text = <"Identifier">
					description = <"An organisation identifier.">
				>
				["at0030"] = <
					text = <"Address">
					description = <"An organisation contact address.">
				>
				["at0040"] = <
					text = <"Details">
					description = <"Relationship details.">
				>
				["at0041"] = <
					text = <"Type of relationship">
					description = <"Type of relationship between two organisations.">
				>
			>
		>
	>
	constraint_definitions = <
		["pt-br"] = <
			items = <
				["ac0000"] = <
					text = <"Códigos do tipo de relacionamento">
					description = <"códigos válidos para o tipo de relacionamento entre duas organizações.">
				>
			>
		>
		["en"] = <
			items = <
				["ac0000"] = <
					text = <"Codes for type of relationship">
					description = <"valid codes for the type or relationship between two organisations.">
				>
			>
		>
	>

```
