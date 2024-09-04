---
layout: default
title: create_gsm.py
parent: SE-GSM
nav_order: 1
---

# Create GSM jobs

In this procedure, Dandelion generates possible GSM jobs, or seeds, from each optimized mother structure. The overall algorithm calculates the number of bonds to be broken or added, determines possible reactions, and generates all viable driving coordinates.

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
You can verify that all possible GSM jobs are generated from your optimized mother structures. 

Generated `params.log` file contains used parameter and connection limits.

```
Connection limits:
  H: 1, 1
  C: 2, 4
  N: 1, 3
  O: 1, 2
  F: 1, 1
  S: 1, 2
  CL: 1, 1
  BR: 1, 1
maxbreak = 2
maxform = 2
maxchange = 3
single_change = False
equiv_Hs = False
minbreak = 0
minform = 0
minchange = 1

```




In `ISOMERS.TXT` file, you can get some information about calculated reactions.

  ```
  BREAK 5 6
  ADD 4 6
  ADD 3 6
  ```
