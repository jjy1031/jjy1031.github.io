---
layout: default
title: geom_opt.py
parent: preparation
nav_order: 2
---

# geom_opt.py

This module get list of all `.xyz` files in input path, optimize the input structures using GFN2-xTB method using BFGS algorithm and store the result with optimized structures with `struc.xyz` in output path.

## Parameters

| Parameter      | Short | Description |
|-----------------|-------|-----------|
| `--input_path`  | `-i`  | Path of the input directory containing `.xyz` files. |
| `--output_path` | `-o`  | Path of the output directory where optimized geometries will be stored. |
| `--max_workers` | `-n`  | Number of parallel processes to use for optimization. |
