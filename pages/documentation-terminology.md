---
layout: default
title: Terminology
---

# Using Terminology

Terminologies are a critical aspect of supporting interoperable computable content. This implementation guide defines profiles for the CodeSystem and ValueSet resources to identify key elements that must be supported. 

Readers of this implementation guide should be familiar with the [Using Codes](http://hl7.org/fhir/R4/terminologies.html) topic in the base FHIR specification.

## Code Systems

Standard and established code systems should be used whenever possible. Only in the case that existing code systems do not provide the necessary concepts should new code systems be defined. If required, code systems defined by content conforming to this IG SHALL use the [cpg-codesystem](StructureDefinition-cpg-codesystem.html) profile.

Note that this does not mean that _any_ code system referenced by computable content must use the cpg-codesystem profile. The conformance requirement only applies to code systems _defined_ as part of computable content. For example, the SNOMED-CT code system would not be expected to conform to the cpg-codesystem profile.

Refer to the base FHIR specification for a list of established [code systems](http://hl7.org/fhir/R4/terminologies-systems.html) and the corresponding canonical URL.

## Value Sets

This implementation guide defines two value set profiles, a base cpg-valueset profile that establishes key elements that must be supported for any value set content, and a derived profile, cpg-expressionbasedvalueset, that defines key elements that must be supported for expression-based value set content. Value sets defined by content conforming to this IG SHALL use at least the [cpg-valueset](StructureDefinition-cpg-valueset.html) profile.

In addition, value sets SHOULD be defined using expression-based (or _intensional_) definitions if the value set definition (the content logical definition) cannot be represented using the standard FHIR value set compose syntax. Value sets defined in this way SHALL conform to the [cpg-expressionbasedvalueset](StructureDefinition-cpg-expressionbasedvalueset.html) profile.

Note that as with code systems, this does not mean that _any_ value set referenced by computable content must use the cpg-valueset or related profiles. The conformance requirements only apply to value sets _defined_ as part of computable content.

## Implementation Considerations

Note carefully that for _expression-based_ value sets, content is effectively distributed with the `valueset.compose` containing the enumerated set of individual concepts obtained as the result of the computed expansion of the expression or rulesText as of the time of publication. As new versions of the `cpg-expressionbasedvalueset` instance are created, and/or as new versions of the code systems used by the value set are created, the value set compose content will need to be updated to incorporate newly defined codes that meet the value set intent. Before, and periodically during production use, expression-based value set definitions SHOULD be updated.

