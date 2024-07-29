---
layout: default
title: create_gsm.py
parent: Modules
nav_order: 2
---

# create_gsm.py


For detailed information, see [Journal of computational chemistry 36, 601–611 (2015)](https://onlinelibrary.wiley.com/doi/full/10.1002/jcc.23833?casa_token=7ZtVQGleOwIAAAAA%3AMCrI2MzV0_3cjRuEof_e_uoNE5egitdBSl_p9k_ZkqTeTbaVBzjS7I7AnF20ttyBuhRKS5AHzW2yeVE)

Dandelion uses the SE-GSM to explore PES and provides automated generation of viable driving coordinates from mother structures. This process consists of the following three submodules :
create_gsm.py, run_gsm.py, filter_gsm.py

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
