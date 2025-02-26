---
title: "Curating Data, Code, Workflows, and Publishing"
author: ""
date: ""
---

::: {.callout-note}
This page is work in progress.
:::

You have run your experiments, collected data, wrote code to analyze
the data, and documented your work.  One next possible step that you
should take is sharing the fruits of your labor with the world.

However, you can't simply keep your results just about anywhere,
promise to make them available on demand, and declare victory.  There
are some principles and processes to follow.

One such set of principles is FAIR data principles.

# FAIR Data

FAIR stands for Findability, Accessibility, Interoperability, and
Reusability.

FAIR is a set of guiding principles designed to make data more
findable, accessible, interoperable, and reusable. Officially
introduced in the article titled _[The FAIR Guiding Principles for
scientific data management and stewardship][fair-paper]_ in 2016,
these principles have become a fundamental framework for scientific
data management and stewardship.

[fair-paper]: https://www.nature.com/articles/sdata201618

FAIR data principles are increasingly being adopted by research
institutions, funding agencies, and publishers to enhance the value
and impact of scientific data. FAIR is particularly important in the
context of open science initiatives and research data management.

## FAIR principles

FAIR principles break down as follows.

### Findable

- Data should have globally unique and persistent identifiers.
- Data should be described with rich metadata.
- Metadata should clearly include the identifier of the data it
  describes.
- Data should be registered or indexed in a searchable resource.

### Accessible

- Data should be retrievable by their identifier using a standardized
  protocol.
- The protocol should be open, free, and universally implementable.
- The protocol should allow for authentication and authorization where
  necessary.
- Metadata should remain accessible even when the data is no longer
  available.

### Interoperable

- Data should use formal, accessible, shared, and broadly applicable
  language for knowledge representation.
- Data should use vocabularies that follow FAIR principles.
- Data should include qualified references to other data.

### Reusable

- Data should have accurate and relevant attributes.
- Data should be released with a clear and accessible data usage
  license.
- Data should have detailed provenance.
- Data should meet domain-relevant community standards.


## FAIR principles in practice

FAIR is still evolving, and there is no one implementation of FAIR.
Organizations have been implementing their individual approaches to
FAIR principles.

In practice, implementing FAIR data principles requires a strategic
approach across multiple dimensions of data management. Here are some
things to keep in mind.

### Making data findable

- **Assign persistent identifiers**: Use DOIs (Digital Object
  Identifiers), ARKs, or other permanent identifier systems for your
  datasets.
- **Create rich metadata**: Document your data comprehensively with
  standardized metadata schemas relevant to your field (e.g.,
  DataCite, Dublin Core).
- **Register in repositories**: Deposit data in appropriate domain or
  institutional repositories that are indexed by search engines.
  

### Making data accessible

- **Choose appropriate repositories**: Select repositories that
  provide HTTP/HTTPS access protocols.
- **Clarify access conditions**: Even if data has restrictions, ensure
  the conditions for access are clearly specified.
- **Preserve metadata**: Ensure metadata remains accessible even if
  the dataset itself becomes unavailable.
- **Implement authentication**: When needed, use standard
  authentication protocols rather than proprietary solutions.

### Making data interoperable

- **Use standard formats**: Store data in non-proprietary, widely-used
  formats (CSV rather than Excel, JSON or XML for structured data).
- **Apply controlled vocabularies**: Use established ontologies and
  terminologies from your field.
- **Include qualified references**: When referencing other datasets,
  use their persistent identifiers.
- **Follow semantic web standards**: Consider RDF data models and
  linked data approaches for complex datasets.

### Making data reusable

- **License clearly**: Apply explicit, machine-readable licenses
  (Creative Commons, Open Data Commons).
- **Document provenance**: Include detailed information about data
  origin, collection methods, and processing steps.
- **Follow community standards**: Adhere to domain-specific data
  standards and reporting guidelines.
- **Include quality indicators**: Document data quality assessment
  methods and results.


# References

- [The FAIR Guiding Principles for scientific data management and
  stewardship](https://www.nature.com/articles/sdata201618)

- [Library Carpentry: FAIR Data and
  Software](https://librarycarpentry.org/lc-fair-research/aio/index.html)

- [FAIR (& Fair) Toolkit](https://fairisland.org/toolkit/)

- [FAIR Principles](https://www.go-fair.org/fair-principles/)

- [FAIR Data in
  Cyverse](https://cyverse-foundational-open-science-skills-2020.readthedocs-hosted.com/en/master/Data_management/FAIR.html)

