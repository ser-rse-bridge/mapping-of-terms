---
# array of synonyms or adjacent concepts
se_fundamental:
    - a term
    - a synonym
    - a long synonym that will wrap within the cell of the table.  I wonder how long it will have to be to do that?
    - an adjacent term

# Short (1 sentence) description of the SE fundamental -- as a convenience
fundamental_description: "avoid stupid mistakes"

# SWEBOK section needs to be formatted with two digits per component, zero-filled so that they sort lexically as strings
# They also need to be quoted
swebok_section: "10.09.08.07"

# array of synonyms or adjacent concepts
# need a way of specifying that it is the same as the se_fundamental
rse_equivalent:
    - different term
    - different synonym
    - same adjacent term

# Text, a brief description of the typical realizations of the fundamental, in RSE practice
rse_practice: "doing some practical"

# General level of awareness of the fundamental in the research software community
# integers 0-3, 0=effectively no awareness, 3=widespread awareness
rse_awareness: 2
rse_awareness_source: expert judgement

# General level of usage of the fundamental in the research software community
# integers 0-3, 0=effectively no usage, 3=widespread use
rse_usage: 1
rse_usage_source: expert judgement

# Potential for SE research to improve use in research software
# integers 0-3, 0=effectively no opportunity, 3=significant SE research beneficial
ser_potential: 3
ser_potential_source: expert judgement

# Reasons/opportunities for the SE research
ser_opportunities: text

# References (external links, papers, etc., that may provide useful connections)
references:
    - ref1
    - ref2

# Date of last review by the editorial board
last_reviewed: 1970-01-01
---
Container for everything worth discussing about this fundamental, e.g., 

* Typical artifacts
* Notable exceptions/deviations (e.g., clean code can be challenging in HPC)
* Other relevant notes
