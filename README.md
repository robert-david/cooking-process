cooking-process
===============

Ontology for describing processes in the domain of cooking



Cooking Process Ontology
========================

1.	Ontology:
=================


1.1.	First a Recipe class is defined. It is only used to simplify recipe instances, 
	which are defined as individuals of this class.

1.2.	Define and classify ingredient classes and object properties to assign to a recipe
	( Ingredient and hasIngredient ).

1.3.	Define and classify equipment classes and object properties to assign to a recipe
	( Equipment and usesEquipment ).

1.4.	Define the recipe step classes (subclasses of RecipeStep ).

	The system can be used to automatically infer the steps necessary to produce the dish in question.
	The process for creating a dish is composed of these steps, which are represented as defined classes.
	They can be inferred for a recipe individual by the use of ingredients and equipment.

1.5.	Define the classes, object properties and rules for ordering of the recipe steps.

	The system can be used to automatically order recipe step individuals for the dish in question.
	Define the object properties hasStep (for linking a step individual to a recipe) 
	and the object properties next and previous (for consequently linking two step individuals).
	Define SWRL rules stating an order using the next object property for two recipe steps that should 
	be executed consequently. Define RuleContext classes that can be used to limit the SWRL rules to 
	a defined context and apply only a subset of the rules to a specific recipe using the context. 

	
2.	Procedure for practical use:
====================================

2.1	Define items used:
==========================

2.1.1.	Define and classify ingredient individuals.
2.1.2.	Define and classify equipment individuals.


2.2	Define the recipe:
==========================

2.2.1.	Declarate recipe individual, classifying it as a Recipe.
2.2.2.	Add ingredients individuals to the recipe individual using the object property hasIngredient.
2.2.3.	Add equipment individuals to the recipe individual using the object property usesEquipment.


2.3.	Infer the recipe steps:
===============================

2.3.1.	If the reasoner is started, the needed recipe steps for producing the dish are inferred.


2.4	Infer the step order:
=============================

2.4.1.	For inferring the order of the recipe steps, some preparations are needed.

	Because we did use classes as representations of the recipe steps, no direct ordering can be done on these.
	Therefore we have to define individuals for the steps and assign the needed classes inferred in  2.3.1 
	to these steps. Then we have to link the steps to the recipe using the hasStep object property.
	If we do not have a SWRL rule for assigning the context to the steps based on the hasStep object property, 
	we have to define one or use generic rules.

2.4.2.	If the reasoner is started, the processing order for the recipe steps are inferred.

	The reasoner will classify the recipe step individuals with the context class based on the hasStep o
	bject property and the corresponding SWRL rule. It will apply the next object property to each two 
	recipe step individuals that should be performed consequently based on the SWRL rules and also assign 
	the previous object property as it is the inverse to next. The result is the complete step order for 
	a recipe representing the cooking process description. 

