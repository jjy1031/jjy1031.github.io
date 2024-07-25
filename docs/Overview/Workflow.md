---
layout: default
title: Workflow
parent: Overview
nav_order: 2
---

# Workflow

Dandelion provides an integrated and streamlined process to create an extensive database by sampling chemical spaces along the reaction pathways. This method consists of four stages: the preparation of mother structures, product search, landscape exploration and database generation.

![overall_scheme](https://github.com/jjy1031/jjy1031.github.io/assets/160209859/e0c9ad94-fa03-42d0-95ad-f0cb31315422)

## 1. Initial Structures Preparation

### 1.1. opt_mothers.py

For your crude input structures, this module performs geometry optimization using GFN2-xTB. This can provide stable molecular configurations as a starting point.

## 2. Product Search

For detailed information, see [Journal of computational chemistry 36, 601–611 (2015)](https://onlinelibrary.wiley.com/doi/full/10.1002/jcc.23833?casa_token=7ZtVQGleOwIAAAAA%3AMCrI2MzV0_3cjRuEof_e_uoNE5egitdBSl_p9k_ZkqTeTbaVBzjS7I7AnF20ttyBuhRKS5AHzW2yeVE)

Dandelion uses the SE-GSM to explore PES and provides automated generation of viable driving coordinates from mother structures. This process consists of the following three submodules :

### 2.1. create_gsm.py

In this procedure, dandelion generates possible GSM jobs, or seeds, from each optimized mother structure. The overall algorithm calculates the number of bonds to be broken or added, determines possible reactions, and generates all viable driving coordinates.

  ```
  ├── ClGeom-m7138-i1-c1-opt
  │   ├── gsm0000
  │   ├── gsm0001
  │   ├── gsm0002
  ...
  ├── ClGeom-m7164-i1-c1-opt
  │   ├── gsm0000
  │   ├── gsm0001
  │   ├── gsm0002
  ...
  ```
You can verify that all possible GSM jobs are generated from your optimized mother structures. In `ISOMERS.TXT` file, you can get some information about calculated reactions.

  ```
  BREAK 5 6
  ADD 4 6
  ADD 3 6
  ```

### 2.2. run_gsm.py

Dandelion runs SEGSM using this module, and output files will be generated. Based on these results, the coordinates to be filtered in the next stage are determined.

  ```
  ├── 0000_string.png
  ├── grown_string_000.xyz
  ├── grown_string1_000.xyz
  ├── gsm_log
  ├── gsm.sh
  ├── IC_data_0000.txt
  ├── initial.xyz
  ├── ISOMERS.txt
  ├── lot_jobs_0.txt
  ├── lot_jobs_1.txt
  ├── lot_jobs_2.txt
  ├── lot_jobs_3.txt
  ├── lot_jobs_4.txt
  ├── lot_jobs_5.txt
  ├── lot_jobs_6.txt
  ├── lot_jobs_7.txt
  ├── lot_jobs_8.txt
  ├── opt_converged_000.xyz
  ├── scratch
  │   └── 000
  └── TSnode_0.xyz
  ```
  By generated `.png` file, you can check whether a GSM job has converged.

  ![0000_string](https://github.com/user-attachments/assets/bd4aab1e-9679-4b8c-ba67-412fec56b5aa)

  Because this job has successfully converged before `max_node = 30`, it will be survived in filtering process.
  
### 2.3. filter_gsm.py
  Through this process, you can get filtered structures. This filtering algorithm excludes trivial pathways with strictly uphill energy trajectories, negligible energy variations, unfeasible 2 structures, or those that are repetitive.
  
There are some cases to be filtered :
  If xTB didn't converged or pyGSM terminated the execution based on its criteria, there will be no png file is generated.

Then the submodule `profile_filter` filters the cases which have wrong ts, too high or low barrier height, too small delta_e. 
`structure_filter ` can filter chemically absurd products, followed by unique filter which filters duplicates based on smiles. If there are more than one of same SMILES, pick the lowest barrier reaction.

## 3. Landscape Search

### 3.1 run_neb.py

The Nudged Elastic Band method is to find the Minimum Energy Path between a given initial and final state of a transition. It is neccessary to construct a set of images between the initial and final state by interpolation to find MEP. And to optimize this path, we have to minimize the force acting on the image. So, dandelion runs Cl-NEB on reaction path to optimize this.

The generated output files have some information about Minimum Energy Path(MEP).

```
ClGeom-m7138-i1-c1-opt-gsm0019
├── converged
├── fitlist.npy
├── fmaxs.json
├── mep.gif
├── mep.png
├── mep.xyz
├── neb.db
├── product.png
├── product.xyz
├── reactant.png
├── reactant.xyz
├── transition_state.png
└── transition_state.xyz
```

You can see the process of path optimization in `mep.png`

![mep](https://github.com/user-attachments/assets/ea3af721-54a0-482b-b42f-efa8d2d38512)

Also, `mep.gif` can show you how the reaction occurs.

![KakaoTalk_20240722_153538363](https://github.com/user-attachments/assets/361928e3-a4a5-412e-b5c9-12afbcc55a8a)

### 3.2. filter_neb.py
Filter out NEB jobs and sample geometries for refinement. This algorithm extracts caculated energy, and checks if the reaction is valid. Also, it counts the number of significant imaginary frequencies below the threshold and determines whether a given structure is a proper transition state or not. 

### 3.3. compile_neb.py
Calculate DFT forces on samples and compile as a database using Atomic Simulation Environment.
If you want to effectively use the database, please refer to [this page](https://wiki.fysik.dtu.dk/ase/).

## 4. Database Generation

### 4.1. refine_forces.py


### 4.2. compile_refined.py
This module extracts data from ASE database generated before, and save these to an h5 file. Using h5 visualization program, you can easily check the calculated result of sampled chemical points including energy, force, positions and atomic numbers.


