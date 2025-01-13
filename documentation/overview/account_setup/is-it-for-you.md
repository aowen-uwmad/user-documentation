---
ospool:
  path: overview/account_setup/is-it-for-you.md
---

Computation on the Open Science Pool 
====================================


The [OSG](https://osg-htc.org) is a nationally-funded consortium of computing resources 
at more than one hundred institutional partners that, together, offer a strategic 
advantage for computing work that can be run as numerous short tasks that can execute 
independent of one another. For researchers
who are not part of an organization with their own pool in the OSG, we offer the 
[Open Science Pool (OSPool)](https://opensciencegrid.org/about/open_science_pool/), with dozens 
of campuses contributing excess computing capacity in support of open science. The OSPool is available 
for US-affiliated academic, government, and non-profit research projects and groups for their High Throughput Computing (HTC) workflows.

Learn more about the services provided by the OSG that can support your HTC workload: 

<iframe width="560" height="315" src="https://www.youtube.com/embed/5FMAFxROGv0?si=brAswQEWy_VDLuIz" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Computational Fit on the OSPool

For problems that can be run as numerous independent jobs (a high-throughput approach) and have requirements
represented in the first two columns 
of the table below, the significant capacity of the OSPool can transform the types of 
questions that researchers are able to tackle. **Importantly,
many compute tasks that may appear to not be a good fit _can_ be modified in simple ways 
to take advantage, and we'd love to discuss options with you!** 

|   		| **Ideal jobs!** | **Still advantageous** | **Maybe not, but get in touch!** | 
|:--------|:--------------|:--------------|:--------------|
| Expected Throughput: | 1000s concurrent jobs | 100s concurrent jobs | let's discuss! |
| **Per-Job Requirements** |  |  |  |
| CPU	cores	|	1			|	< 8			|	> 8 (or MPI)|
| GPUs		|	0			|	1			|	> 1 |
| Walltime	| 	< 10 hrs*	|	< 20 hrs*	|	> 20 hrs (not a good fit)	|
| RAM		| 	< few GB	|	< 40 GB	|	> 40 GB	|
| Input		| 	< 500 MB	|	< 10 GB	|	> 10 GB**		|
| Output	| 	< 1GB		|	< 10 GB	|	> 10 GB**		|
| Software	| pre-compiled binaries, containers | Most other than ---> | Licensed software, non-Linux |

\* or checkpointable<br>
\** per job; you can work with a multi-TB dataset on the OSPool if it can be split into pieces!

Some examples of work that have been a good fit for the OSPool and benefited from 
using its resources include: 

- image analysis (including MRI, GIS, etc.)
- text-based analysis, including DNA read mapping and other bioinformatics
- hyper/parameter sweeps
- Monte Carlo methods and other model optimization

## Quickstart Resources

**Introduction to OSG the Distributed High Throughput Computing framework** from the annual [OSG User School](https://opensciencegrid.org/outreach/):

<iframe width="560" height="315" src="https://www.youtube.com/embed/vpJPPjoQ3QU?si=nIqhW8_mgdlKVpUZ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**[Full OSG User Documentation](https://portal.osg-htc.org/documentation/)** including our [Roadmap to HTC Workload Submission](../../../htc_workloads/workload_planning/roadmap/)

**[OSG User Training materials](../../../support_and_training/training/osgusertraining/)**. Any researcher affiliated with an academic, non-profit, or government US-based research project is welcome to attend our trainings. 


**Learn more and chat with a Research Computing Facilitator by [signing up for OSPool account](https://portal.osg-htc.org/application)**
