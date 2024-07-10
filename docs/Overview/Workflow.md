---
layout: default
title: Workflow
parent: Overview
nav_order: 2
---

# Workflow

Dandelion is -.


![overall_scheme](https://github.com/jjy1031/jjy1031.github.io/assets/160209859/e0c9ad94-fa03-42d0-95ad-f0cb31315422)


## 1. dandelion_sample.py

We automated the generation of mother structures and the corresponding driving coordinates in this process. 

  ``` python

  usage: dandelion_sample.py [-h] -i INPUT_PATH -o OUTPUT_PATH -n MAX_WORKERS

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

  This process consists of six steps below.

  ### 1. Creating GSM
  In this procedure, you can make GSM jobs from mother structures.
  This algorithm considers number of connections to break, to change, to form and decides possible rxn.
  Result is stored in your/mother/structure/path/1_gsm/.../ISOMERS.TXT

  ```
  BREAK 5 6
  ADD 4 6
  ADD 3 6
  ```
  ### 2. Running GSM
  ### 3. Filtering GSM
  ### 4. Running NEB
  ### 5. Filtering NEB
  ### 6. Compiling samples
  

- **dandelion_refine.py**

```python
$ python 2_run_gsm_jobs.py --input_path INPUT_PATH --max_workers MAX_WORKERS
```
  `input_path` should contain XYZ files of mother structures.
  
  You can run SE-GSM in this process.
  
  
 You should modify the `input_path` and `output_path` of the config file. 

 `input_path` should contain XYZ files of generated coordinates(seeds).

 `output_path` will be the directory where filtered coordinates(seeds) will be stored.
 
  If you run this cell, you can get filtered structures. This filtering algorithm excludes trivial    pathways with strictly uphill energy trajectories, negligible energy variations, unfeasible
  2 structures, or those that are repetitive.

## 2. Nudged Elastic Band 
- 1_neb_xtb.py
- 
```python
$ python 2_run_gsm_jobs.py --input_path INPUT_PATH --max_workers MAX_WORKERS
```
- 2_make_rxns_json.ipynb
- 3_compile_xtb_h5.py

## 3. wB97X/6-31g(d) refinement
- 1_wb97x_on_xtb_h5.py
- 2_compile_wb97x_h5.ipynb

