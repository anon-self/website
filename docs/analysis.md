---
layout: default
title: Reasons for Unreachability
nav_order: 4
description: "Mobile Application Coverage: The 25% Curse and Ways Forward"
permalink: /docs/analysis
---

### Categorization of Reasons for Unreachability (RQ2)

The detailed breakdown of manually extracted reasons for unreachability is also provided as an [Excel sheet](../assets/data/Reasons.xlsx).

For each application under study, we grey out activities that are reached manually, and for each unreached activity, we mark the reasons leading to unreachability as described in the paper, i.e., Device (Software properties and Hardware properties), Server, Environment, External resources (Equipment and Information), Usage patterns, Error handling, Alternate entry, Disabled (For app version and For all end-users), Transitive, No caller and Inconclusive.

---

### Categorization of Properties (RQ3)

We systematically study and characterize properties of conditions guarding the execution of
unreached activities.

From a total 363 unreached activities, we exclude activities classified as <i>Inconclusive</i>, <i>No caller</i> or <i>Transitive</i>. We obtain a set of 185 activities, from which we extract a detailed breakdown in terms of <b>Exported</b>, <b>Activation Location</b>, <b>Activation Guards</b>, and <b>Data</b>.
The breakdown is provided as an [excel sheet](../assets/data/ActivationProperties.xlsx).

The distribution of activities along each property, coupled with the reasons for unreachability of the related activities is provided [here](../assets/images/full-properties.pdf).

<!--a href="../assets/images/property-intro-tbl.png">
    <img
        src="../assets/images/property-intro-tbl.png"
        alt="Activation Properties and Mapped Reasons"
    >
</a-->

<!--object data="../assets/images/full-properties.pdf" width="1000" height="1000" type='application/pdf'>
</object-->
<!--Additionally, we map the different types of properties we extract to the identified reasons for unreachability, to characterize which patterns are most common depending on the reason for unreachability.
For example, in the table below, xx% of activities unreached due to missing software properties are activated in GUI/lifecycle callbacks.
-->

From this analysis, we extract 18 types of activity with varying difficulty levels for tools to handle. We further map these types to the associated reasons for unreachability to characterize which patterns are most common depending on the reason:

<a href="../assets/images/property-tbl.png">
    <img 
        src="../assets/images/property-tbl.png"
        alt="Activation Properties and Mapped Reasons"
    >
</a>

We also characterize the data used in terms of type (<i>Parameters</i> or <i>Execution Dependencies</i>) and format (<i>Primitive only, Primitive + Strings, Primitive + Strings + Objects</i>):

<a href="../assets/images/property-data-tbl.png">
    <img 
        src="../assets/images/property-data-tbl.png"
        alt="Used Data"
    >
</a>
