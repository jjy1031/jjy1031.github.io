---
layout: default
title: run_gsm.py
parent: SE-GSM
nav_order: 2
---

# run_gsm.py

This module executes Bash script `gsm.sh` which exists in every GSM job and generates the corresponding outputs. This uses `ProcessPoolExecutor` to run the script in parallel for each gsm job directory.

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
  You can observe the process of a GSM job through the generated `.png` file.

  ![0000_string](https://github.com/user-attachments/assets/bd4aab1e-9679-4b8c-ba67-412fec56b5aa)


  
