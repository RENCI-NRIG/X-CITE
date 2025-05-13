---
title: Scientific Workflow Management
author: "Karan Vahi"
date: "May 12, 2025"
---

::: {.callout-note}
This page is work in progress.
:::

This module provides an overview on how a CHESS can use notion of workflows to automate
their data processing tasks and in the process shortening the turn around time for the
data processing that needs to be done on data collected at a beamline. 

The content in this module is gathered from author's various presentations over 
the years and their work on workflows.

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

In the above example figure, the nodes/vertices in indicate the job that
needs to be run, while the edges indicate the dependencies between the jobs.

The dependencies can be both *control flow* or *data driven* i.e.
- a job can be run only after the parent has finished successfully OR
- a job requires data sets to run that are generated as outputs by a parent node/job.
- the rectangles in the figure indicate datasets that a node/job require and generate.

Using scientific workflows for your data processing in general provides you the 
following benefits

1. **Reproducibility** - Scientific workflows allow you to document and 
   reproduce your analyses, ensuring their validity.

2. **Automation** - Workflows automate repetitive and time-consuming tasks, 
   thereby reducing the workload of researchers.

4. **Scalability** - Workflows allow you to scale up your data processing to handle
   large data sets and complex analyses, enabling you to solve large research 
   problems in your field. It helps you run your analysis in parallel over distributed
   resources.

5. **Reusability** - Once your data processing pipeline is modelled as a workflow, 
   typically it is possible to reuse the workflow in different ways. For example, 
   you could use the workflow as part of a bigger science analysis (that maybe faclity 
  wide), or even share the workflow with another CHESS researcher.
   
### High Level Steps on Identifying a Workflow

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

### Workflow Constructs

There are some core different types of workflow patterns that underpin most
of the complex workflows. The jobs in the examples, below map to simple
commonly available *linux executables* and is for illustration purposes
only. For your actual workflows, you use your actual scientific code. 

**Process**

![Process Workflow](./images/process-workflow.png)

In the above example, workflow consists of a single job that runs
the `ls` command and generates a listing of the files in the `/` directory.

**Pipeline**

![Pipeline Workflow](./images/pipeline-workflow.png)

In the above example, workflow consists of two jobs linked together in a pipeline. 
The first job runs the `curl` command to fetch the Pegasus home page and 
store it as an HTML file. The result is passed to the `wc` command, which 
counts the number of lines in the HTML file.

**Split**

![Split Workflow](./images/split-workflow.png)

In the above example, workflow consists of a job that downloads the Pegasus home 
page using the `curl` command,  then uses the `split` command to divide it into 4 pieces. 
The result is passed to the `wc` command to count the number of lines in each piece.

**Merge**

![Merge Workflow](./images/merge-workflow.png)

In the above example, workflow consists of 3 jobns that execute the `ls` command 
on several */bin directories and passes the results to the `cat` command, 
which merges the files into a single listing.

### Workflow Challenges 

When running workflows independent of what workflow system you are using, there
are some common challenges that you may encounter.

- **How to describe your complex workflows in a simple way?** This is important in relation
  to sharing your workflows with your colleagues. Can the workflow that you just ran
  locally on your resource, can be run by another researcher on the 
  - same resource
  - different resource / cluster
  - what changes if any are required?
- **How do you get your workflows to  access distributed, heterogeneous data and
  resources (heterogeneous interfaces)**. For example, you may want to distribute
  your analysis across different clusters.
- **How to deal with resources/software that change over time?** The 
  resource on which you are currently running may go away (no longer operational),
  software dependencies on which your code requires change.
- **How to have ease of use?** Ability to debug and monitor large workflows.


### Workflow Creation

There are a variety of workflow systems available that you can use in general.
Some of them allow you to create workflows using

* A graphical interface
* Programmatically using an API in a main stream programming language such as Python

CHESS researchers have access to the following systems for running workflows

* CHESS Workflow Runner
* Galaxy (to be covered in DC102)
* Pegasus  Workflows

### CHESS Workflow Runner

To be added

### Pegasus Workflows

Pegasus WMS allows users to model their computational pipelines as workflows, that
can execute in a number of different environments including 

- desktops, 
- campus clusters, 
- distributed computing environments such as PATh and OSG OSPool, 
- supercomputing CI such as ACCESS and clouds.
 
Pegasus bridges the scientific domain and the execution environment by automatically 
mapping high-level workflow descriptions onto distributed resources. It automatically 
locates the necessary input data and computational resources necessary for workflow 
execution. Pegasus enables scientists to construct workflows in abstract terms 
without worrying about the details of the underlying execution environment or 
the particulars of the low-level specifications required by the middleware 
(HTCondor, SLURM,  or Amazon EC2). 

The clean separation of how the user defines a Pegasus workflow (in a resource
agnostic way) called the *Abstract* workflow and the *Executable* workflow that 
actually runs on your target resource is illustrated below. 

![Pegasus Translation of User Defined Abstract Workflow to Executable Workflow](./images/pegasus-abstract-to-executable)

As a user when you define a Pegasus workflow, you 

- identify both input and data sets that a job requires by their logical identifiers called *LFN*.
- identify the executable that needs to be invoked for a job by it's logical identifier called *transformation*.

The *Abstract* workflow when given to Pegasus gets transformed to an *Executable* 
workflow that can execute on your target resource. As part of this transformation
of the workflow Pegasus will figure out

- how to get/stage the input data required for your workflow. add data stage-in jobs
- maps your jobs to a compute resource
- how to stage-out data that your workflow generates

Additionally, as part of this transformation Pegasus can do a lot of optimizations
on your workflow such as

- add data cleanup nodes, that clean up data from cluster when it is not required
- cluster short running jobs together
- data reuse (delete jobs whose datasets already exist)

