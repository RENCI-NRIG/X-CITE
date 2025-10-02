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
developed. These are grouped by general topic into "Themes". The first
theme is named "Essential Elements" and is, as the name suggests,
absolutely critical. Make certain you understand the material in that
theme before you move on to the others, but once you cross this hurdle
you can move through the other themes in any order. Some of the
Essentials topics may be old hat to you (Python programming, for
instance) while other are highly CHESS-specific (Data Collection).

## Theme 0: Essential Elements

- XS 100: [Data collection, preparing input parameters, SPEC and
  CLI][xs100]
- SF 100: [Intro to Linux, the command line, and programming in Python][sf100]
- XS 101: [Basic / on-the-fly data analysis, viewing detector
  images][xs101]
- PE 100: [Python Programming and Jupyter notebooks][pe100]




## Theme 1: Programming Fundamentals

- PE 101: [Using Python packages & libraries, Conda][pe101]
- PE 102: [Numerical data analysis with Python][pe102]
- PE 103: [Software version control][pe103-vcs],
  [testing][pe103-testing], and [debugging][pe103-debugging]
  
## Theme 2: Systems Fundamentals

- SF 101: [Containers and virtualization][sf101] 
- SF 200: [Parallel computing concepts][sf200]  
- SF 201: [Batch systems and compute farms with CHESS example][sf201] 

## Theme 3: Distributed Computing and the CI Ecosystem

- DC 100: [Distributed computing concepts][dc100] 
- DC 101: [Scientific workflow management][dc101] 
- DC 102: [Using science gateways with Open OnDemand example][dc102] 
- DC 200: [Computing with CI ecosystem - ACCESS, PATh, Campus][dc200] 

## Theme 4: X-Ray Science S&E Software

- XS 102: [Large-scale data analysis: from images to science
  parameters to interpretation][xs102] 
- XS 200: [Metadata for data fidelity and systematic checks][xs200]  

## Theme 5: Data Curation and FAIR

- CF 100: [Intro to domain metadata standards, formats and repositories][cf100] 
- CF 101: [Best practices for developing DMP][cf101] 
- CF 102: [Metadata annotation and DOI][cf102] 
- CF 200: [Curating data, code, workflows, and publishing][cf200] 



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

[sf200]: ./theme2/SF200/parallel-computing.md
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
[cf101]: ./theme5/CF101/dmp-best-practices.md
[cf102]: ./theme5/CF102/metadata-annotation-and-doi.md
[cf200]: ./theme5/CF200/curating-data.md

