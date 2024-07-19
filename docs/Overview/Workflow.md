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

## 1. Initial Structures Preparation

### 1.1 opt_mothers.py

For your crude input structures, this module performs geometry optimization using GFN2-xTB. This can provide stable molecular configurations as a starting point.

## 2. Product Search

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

  This process consists of three submodules below.

  ### 2.1 create_gsm.py
  In this procedure, you can make possible GSM jobs - seeds - from mother structures. Overall algorithm calculates the number of bonds to be broken or added, decides possible rxn and generate all possible driving coordinates.
 In `your/mother/structure/path/1_gsm/.../ISOMERS.TXT`, you can get some information about caclulated reactions.

  ```
  BREAK 5 6
  ADD 4 6
  ADD 3 6
  ```

  ### 2.2 run_gsm.py
  gsm 실행하고 이결과에따라 파일여러개생긴다 설명하고
  여기서 png 안생기고 .. 등등에따라 filter하는거아닌가
  outputpath 1_gsm
  num node 30개면... 30개안넘으면 png생겨도 다 filtering하는건가???
  이게말이되? ㅜㅜㅜ
  이거여쭤봐야겠는데
  
  
  ### 2.3 filter_gsm.py

  Through this process, you can get filtered structures. This filtering algorithm excludes trivial    pathways with strictly uphill energy trajectories, negligible energy variations, unfeasible
  2 structures, or those that are repetitive.
  
  There are some cases to be filtered :
  
  - **No png file is generated**
    - xTB didn't converge: This means that the xTB calculations did not converge.
    - pyGSM suicide on its criteria: This indicates that pyGSM terminated the execution based on its predefined criteria.
    
  - **If a png file is generated:**
    - Exiting early: These cases should be filtered out.
      ![image](https://github.com/user-attachments/assets/ca9f0367-4274-4a9b-8ab5-d3e36eb5eb99)
    - Ran out of iterations: These cases may include potential reactions.      
    - Converged : Very rare case
   
![image](https://github.com/user-attachments/assets/ca9f0367-4274-4a9b-8ab5-d3e36eb5eb99)

~~The png file includes some~~ 

  Then the submodule `profile_filter` filters the cases which have wrong ts, too high or low barrier height, too small delta_e. 
`structure_filter ` can filter chemically absurd products, followed by unique filter which filters duplicates based on smiles. If there are more than one of same SMILES, pick the lowest barrier reaction.

  
## 2. Landscape Search

### 4. run_neb.py

The Nudged Elastic Band method is to find the Minimum Energy Path between a given initial and final state of a transition. It is neccessary to construct a set of images between the initial and final state by interpolation to find MEP. And to optimize this path, we have to minimize the force acting on the image.
So we can run Cl-NEB on reaction path to optimize this.

### 5. filter_neb.py
Filter out NEB jobs and sample geometries for refinement.

## 3. Database Generation

### 6. compile_neb.py
Calculate DFT forces on samples and compile as a database

