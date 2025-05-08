---
title: Computing with CI Ecosystem
author: "Karan Vahi"
date: "May 8th, 2025"
---

::: {.callout-note}
This page is work in progress.
:::


This module provides an overview of the various Cyberinfrastructure (CI) resources 
available to a CHESS researcher and more broadly to all the researchers based in the US.

Before we go into the various offerings available, it is useful to recap what we mean
by CI. A widely used and accepted definition of CI by
[Craig A. Stewart et al](https://dl.acm.org/doi/10.1145/1878335.1878347) is as follows:

*Cyberinfrastructure consists of computing systems, data storage systems, advanced
instruments and data repositories, visualization environments, and people, all linked
together by software and high performance networks to improve research productivity and
enable breakthroughs not otherwise possible.*

As a CHESS researcher, you have access to the following CI resources that can 
help you with computing

- CHESS CI Resources at Cornell
- ACCESS
- PATh / OSG

## Overview of CHESS operational workflow

Below is a high level overview of an overall chess operational workflow from the time 
a researcher puts in a proposal to use a beamline at CHESS to data collection from
the beamline; and then it's subsequent data processing and analysis before final 
data curation on the outputs is done. 


![Overview of a general CHESS Operational Workflow](./images/chess-operational-wf.png)


CHESS’ workflow complexity is the length of time spent performing a typical data
analysis. According to a CHESS survey conducted a few years back, CHESS’ workflow complexity
ranges from 1 month to 24 months among survey respondents (with the average being
7.2 months). For the most complex workflows (12 months or longer), researchers often
run into challenges regarding completing their data processing within the defined time 
constraints. 

Use of National CI resources, can especially help CHESS researchers in the following
areas

- Processing data (reduction, analysis, simulation, interpretation), handling large 
  data sets, leveraging existing software and CI.
- Metadata management, Open Science/FAIR and data curation.


## CHESS CI Resources at Cornell

The CLASSE cyberinfrastructure (CI) consists of an interconnected series of h
high-availability server clusters (HACs), data acquisition systems, control systems, 
compute farms, and workstations. Most of these systems run either Scientific Linux 
or Windows on commodity 64-bit Intel-based hardware and are centrally managed 
using Puppet. The median age of key CI components is approximately 5 years, with 
an average refresh rate of once every 10 years. The picture below provides an 
overview of the CHESS CI

![CHESS CI immediately available for processing/analysis by users on the Compute Farm](./images/chess-ci.png)

### DAQ Cluster

DAQ Cluster is the Data Acquisition System that runs on a dedicated server cluster. 
Makes available to researchers about **2PB** of storage for raw data collection, analysis, 
and simulation. Data collected at the stations written directly to the DAQ over either 
NFS or Samba and is immediately available for processing/analysis by users on the
Compute Farm.

CHESS users can also download their data remotely using the CLASSE Globus Connect Server 
or via SFTP. 
 

### Compute Farm

The HPC Cluster at CHESS/CLASSE is a central resource consisting of

- central resource of 60+ enterprise-class Linux nodes (with around 800 CPUs)
- 4.5TB of memory
- uses SGE as a front-end queueing system
- supports interactive, batch, parallel, and GPU jobs
- ensures equal access to the Compute Farm for all users.
 

### Getting access

In order to access the Cornel CI resources, you need a 
Cornell Laboratory for Accelerator-based ScienceS and Education(CLASSE) account.

You can get one by following the instructions at **XXX**.

### Job Submission

The CHESS cluster uses **SGE** as the front end scheduling system to submit jobs.

In general, there are two basic steps to submitting a job

1. Create a shell script containing the commands to be run
2. Submit this script to the Compute Farm using the qsub command.

Below is a simple shell script **myscript.sh** that you can submit to the SLURM
cluster if you are logged onto lnx201.

```{.bash}
[user@lnx201 ~]$ cat myscript.sh
#!/bin/bash
echo Running on host: `hostname`.
echo Starting on: `date`.
sleep 10
echo Ending on: `date`.
#$ -q all.q
#$ -S /bin/bash
#$ -l mem_free=8G
```

In order to submit it to the cluster you can use *qsub* command

```{.bash}
[user@lnx201 ~]$ qsub -q all.q myscript.sh
```

Detailed instructions about this can be found at
[CLASSE Wiki](https://wiki.classe.cornell.edu/Computing/GridEngine).


## ACCESS

## PATh / OSG
