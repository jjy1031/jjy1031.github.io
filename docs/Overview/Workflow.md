---
layout: default
title: Workflow
parent: Overview
nav_order: 2
---

# Workflow

Dandelion provides integrated streamlined process to create extensive database using sampled chemical spaces along the reaction pathways with efficient computational cost.
This method consists of four stages: the preparation of mother structures, product search, landscape exploration and database generation.

![overall_scheme](https://github.com/jjy1031/jjy1031.github.io/assets/160209859/e0c9ad94-fa03-42d0-95ad-f0cb31315422)


## 1. Product Search

Dandelion can provide automated generation of possible driving coordinates from mother structures in this process. The available commands of sampling chemical spaces can be queried with `-h` or `--help` arguments : 

  ``` python

  usage: dandelion_sample [-h] -i INPUT_PATH -o OUTPUT_PATH -n MAX_WORKERS

  Do SEGSM and NEB from mother structures, Other parameters can be set in each modules

  options:
    -h, --help            show this help message and exit
    -i INPUT_PATH, --input_path INPUT_PATH
                          Input path of mother structures
    -o OUTPUT_PATH, --output_path OUTPUT_PATH
                          Output path of dandelion
    -n MAX_WORKERS, --max_workers MAX_WORKERS
                          Number of worker processes

  ```

  This process consists of three steps below.

  ### 1.1 Creating GSM
  In this procedure, you can make possible GSM jobs from mother structures. Overall algorithm calculates the 
  number of bonds to be broken or added, decides possible rxn and generate possible driving coordinates.
  In `your/mother/structure/path/1_gsm/.../ISOMERS.TXT`, you can get some information about caclulated 
  reactions.

  ```
  BREAK 5 6
  ADD 4 6
  ADD 3 6
  ```

  ### 1.2 Running GSM
  
  
  ### 3. Filtering GSM

  Through this process, you can get filtered structures. This filtering algorithm excludes trivial    
  pathways with strictly uphill energy trajectories, negligible energy variations, unfeasible
  2 structures, or those that are repetitive.

  '''
Faith of pyGSM run

1) png is not made
- xTB not converge
- pyGSM suicide on his criteria

2) png is made
- Exiting early -> should filter out
- Ran out of iterations -> also includes potential rxn
- Converged -> very rare
'''

Example of filtered structures :
  
## 2. Landscape Search

### 4. Running NEB

The Nudged Elastic Band method is to find the Minimum Energy Path between a given initial and final state of a transition. It is neccessary to construct a set of images between the initial and final state by interpolation to find MEP. And to optimize this path, we have to minimize the force acting on the image.
So we can run Cl-NEB on reaction path to optimize this.

### 5. Filtering NEB
Filter out NEB jobs and sample geometries for refinement.

## 3. Database Generation

### 6. Compiling samples
Calculate DFT forces on samples and compile as a database

