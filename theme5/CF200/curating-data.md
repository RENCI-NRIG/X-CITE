---
title: "Curating Data, Code, Workflows, and Publishing"
author: ""
date: ""
---

::: {.callout-note}
This page is work in progress.
:::

[![XKCD 1805: Unpublished Discoveries, © Randall Munroe, Creative
Commons Attibution-NonCommercial
license](unpublished_discoveries.png)][xkcd-discoveries]

[xkcd-discoveries]: https://xkcd.com/1805/
[by-nc]: https://creativecommons.org/licenses/by-nc/2.5/


You have run your experiments, collected data, wrote code to analyze
the data, and documented your work.  One next possible step that you
should take is sharing the fruits of your labor with the world.  The
fruits of your labor includes, among other things, the data you have
collected.

However, you can't simply file your results away just about anywhere,
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

## FAIR principles and practices

FAIR is still evolving, and there is no one canonical implementation
of FAIR.  Organizations implement their individual approaches to FAIR
principles based on their needs and constraints.

Although FAIR itself does not make concrete recommendations about
implementation, some common practices have been evolving.

### Making data findable

- Data should have globally unique and persistent identifiers.  You
  will need to use [DOI]s (Digital Object Identifiers), [ARK]s
  (Archival Resource Keys), or other permanent identifier systems for
  your datasets.  People also get stable identifiers -- [ORCID] is one
  such system.

[DOI]: https://en.wikipedia.org/wiki/Digital_object_identifier
[ARK]: https://en.wikipedia.org/wiki/Archival_Resource_Key
[ORCID]:https://orcid.org/

- Data should be described with rich metadata.  Document your data
  comprehensively with standardized metadata schemas relevant to your
  field (e.g., [DataCite], [Dublin Core]).
  
[DataCite]: https://datacite.org/
[Dublin Core]: https://www.dublincore.org/
  
- Metadata should clearly include the identifier of the data it
  describes.
  
- Data should be registered or indexed in a searchable resource.  You
  will need to deposit data in appropriate domain or institutional
  repositories that are indexed by search engines.

### Making data accessible

- Data should be retrievable by their identifier using a standardized
  protocol.  Select repositories that provide web access protocols
  (HTTP/HTTPS) and web APIs (REST).  The protocol should be open,
  free, and universally implementable.

- The protocol should allow for authentication and authorization where
  necessary.  When needed, use standard authentication protocols
  rather than proprietary solutions.
  
- Even if data has restrictions, ensure the conditions for access are
  clearly specified.
  
- Metadata should remain accessible even when the data is no longer
  available.

### Making data interoperable

- Data should use formal, accessible, shared, and broadly applicable
  language for knowledge representation. Use standard formats: store
  data in non-proprietary, widely-used formats.  For example: for
  structured data, you should use CSV, JSON or XML, rather than Excel
  sheets.
    
- Data should use vocabularies that follow FAIR principles.  Use
  established ontologies and terminologies from your field.

- Data should include qualified references to other data.  When
  referencing other datasets, use their persistent identifiers.
  
- Follow semantic web standards.  Consider RDF data models and linked
  data approaches for complex datasets.
  

### Making data reusable

- Data should have accurate and relevant attributes.

- Data should be released with a clear and accessible license.  Apply
  explicit, machine-readable licenses such as Creative Commons or Open
  Data Commons.
  
- Data should include detailed information about data origin,
  collection methods, and processing steps.

- Data should adhere to domain-specific data standards and reporting
  guidelines.  Document data quality assessment methods and results.


# FOXDEN: FAIR at CHESS

<!-- TODO: expand this -->


# References

- [The FAIR Guiding Principles for scientific data management and
  stewardship](https://www.nature.com/articles/sdata201618)

- [Library Carpentry: FAIR Data and
  Software](https://librarycarpentry.org/lc-fair-research/aio/index.html)

- [FAIR (& Fair) Toolkit](https://fairisland.org/toolkit/)

- [FAIR Principles](https://www.go-fair.org/fair-principles/)

- [FAIR Data in
  Cyverse](https://cyverse-foundational-open-science-skills-2020.readthedocs-hosted.com/en/master/Data_management/FAIR.html)

