---
title: Scientific Workflow Management
author: ""
date: ""
---

::: {.callout-note}
This page is work in progress.
:::

This module provides an overview on how a CHESS can use notion of workflows to automate
their data processing tasks and in the process shortening the turn around time for the
data processing that needs to be done on data collected at a beamline. 


## What are Scientific Workflows

Scientific workflows allow users to easily express multi-step computational tasks, 
for example retrieve data from an instrument or a database, reformat the data, and 
run an analysis. A scientific workflow describes the dependencies between the tasks
and in most cases the workflow is described as a directed acyclic graph (DAG), 
where the nodes are tasks and the edges denote the task dependencies.

A defining property for a scientific workflow is that it manages data flow. 
The tasks in a scientific workflow can be everything  from short serial tasks to 
very large parallel tasks (MPI for example) surrounded by a large number of small, 
serial tasks used for pre- and post-processing.

![Example Workflow](./images/diamond-workflow.png)


Using scientific workflows for your data processing in general provides you the 
following benefits

1. **Reproducibility** - Scientific workflows allow you to document and 
   reproduce your analyses, ensuring their validity.

2. **Automation** - Workflows automate repetitive and time-consuming tasks, 
   thereby reducing the workload of researchers.

4. **Scalability** - Workflows allow you to scale up your data processing to handle
   large data sets and complex analyses, enabling you to solve large research 
   problems in your field.

5. **Reusability** - Once your data processing pipeline is modelled as a workflow, 
   typically it is possible to reuse the workflow in different ways. For example, 
   you could use the workflow as part of a bigger science analysis (that maybe faclity 
  wide)
   
### High level steps on identifying a Workflow

Here are some tips on how you can identify a workflow for your data processing

- Start on a whiteboard and think about the various steps that your data processing
  entails. Especially when you already have existing monolithic code for data processing,
  it is important to think about your processing at a high level in a logical manner.
- Think about the various steps that make sense logically, and would also make sense 
  another CHESS researcher when discussing the problem. 
- Think about the granularity in context of input data. If a particular step in 
  your identified workflow, can benefit on working on smaller chunks of data; then 
  consider breaking down that step in smaller parallel sub steps. For example if you 
  are working on time series dataset, and you have a dataset collected for a month, 
  you can break down processing in chunks of 
  - per day
  - per hour
  - per minute
  - and so forth.
   
  What granularity makes sense is subjective. A good rule of thumb is that the step
  can easily run on a wide variety of compute nodes with reasonable memory. You don't
  want to model a workflow that can only run on a few extremely powerful nodes with
  lots of memory. In some cases this maybe **unavoidable**. However, it is always 
  good to think along these lines. 
- Often, each step (type of step) in your workflow would map to a different 
  executable.  


Find the inherent DAG structure in your application to convert into a workflow
