---
title: "X-CITE training materials"
toc: false
---

X-CITE (CyberInfrastructure Training and Education for Synchrotron
X-Ray Science) develops training materials for the community of
scientists and researchers using the [CHESS] synchrotron X-ray
facility and similar light sources.

Our training modules will get you up to speed in working with the
CyberInfrastructure ("CI") at CHESS - the High Performance Computing
(HPC)
and Networking resources. Understanding the CI and how to use it is
practically essential for making the most of your beamline time and
the analysis that follows after the fact.

Below you'll find links to the training modules we have
developed. These are grouped by general topic into themes; the first
is named "Essential Elements" and is absolutely critical. Make certain
you understand the material in that section before you move on to the
others, but once you cross this hurdle you can move through the other
collections in any order. Some of the Essentials topics may be old hat
to you (Python programming, for instance) while others are 
CHESS-specific - Data Collection, for instance.

## Essential Elements

- (B) XS 100: [Data collection, preparing input parameters, SPEC and
  CLI][xs100]
- (B) SF 100: [Intro to Linux, the command line, and programming in Python][sf100]
- (B) XS 101: [Basic / on-the-fly data analysis, viewing detector
  images][xs101]
- (B) PE 100: [Python Programming and Jupyter notebooks][pe100]


## Additional Topics - Programming and Software Development

- (I) PE 101: [Using Python packages & libraries, Conda][pe101]
- (I) PE 102: [Numerical data analysis with Python][pe102]
- (E) PE 103: [Software version control using git][pe103-vcs],
  deliberate [testing][pe103-testing], and [debugging][pe103-debugging] techniques
  
## Additional Topics - Cyberinfrastructure (CI) Systems

- (B) DC 100: [Parallel and distributed computing concepts][dc100]
- (E) DC 200: [Computing with CI ecosystem - ACCESS, PATh, Campus][dc200]
- (E) SF 201: [Batch Systems and Compute Farms][sf201]
- (E) DC 101: [Scientific workflow management][dc101] 
- (I) SF 101: [Containers and virtualization][sf101]
- (I) DC 102: [Using science gateways with OpenOnDemand][dc102]
- (B) SF 102: [Moving data with Globus][sf102]



## Data Curation and FAIR

- (I) CF 100: [Intro to domain metadata standards, formats and repositories][cf100] 
- (I) CF 101: [Best practices for developing DMP][cf101] 
- (I) CF 102: [Metadata annotation and DOI][cf102] 
- (I) CF 200: [Curating data, code, and workflows; publishing][cf200]
- (E) CF 201: [End-to-end research data workflow with FOXDEN example][cf201]
<!-- References -->

[CHESS]: https://www.chess.cornell.edu/

[pe100]: ./theme1/PE100/index.qmd
[pe101]: ./theme1/PE101/index.qmd
[pe102]: ./theme1/PE102/index.qmd
[pe103]: ./theme1/PE103/vcs-testing-debugging.md

[pe103-vcs]: ./theme1/PE103/vcs.qmd
[pe103-testing]: ./theme1/PE103/testing.md
[pe103-debugging]: ./theme1/PE103/debugging.md

[sf100]: ./theme2/SF100/linux-commandline-scripting.md
[sf101]: ./theme2/SF101/containers-and-virtualization.md
[sf103]: ./theme2/SF102/moving-data-with-globus.md
[sf201]: ./theme2/SF201/batch-systems-and-compute-farms.md

[dc100]: ./theme3/DC100/distributed-computing.md
[dc101]: ./theme3/DC101/scientific-workflow-management.md
[dc102]: ./theme3/DC102/using-science-gateways.md
[dc200]: ./theme3/DC200/computing-with-ci-ecosystem.md

[xs100]: ./theme4/XS100/data-collection.md
[xs101]: ./theme4/XS101/data-analysis.md
[xs102]: ./theme4/XS102/large-scale-data-analysis.md
[xs200]: ./theme4/XS200/metadata.md

[cf100]: ./theme5/CF100/domain-metadata-standards.md
[cf102]: ./theme5/CF102/metadata-annotation-and-doi.md
[cf200]: ./theme5/CF200/curating-data.md
[cf201]: ./theme5/CF201/end-to-end-dataflow.md
