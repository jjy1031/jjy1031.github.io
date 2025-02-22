---
layout: default
title : Home
nav_order: 1
---


# Dandelion Docs
Welcome to the documentation site of Dandelion.
<div align="center">
  <img src="docs/img/front.png" alt="Dandelion" width="700">
</div>

# Introduction

![overall_scheme](https://github.com/jjy1031/jjy1031.github.io/assets/160209859/e0c9ad94-fa03-42d0-95ad-f0cb31315422)



<div align="justify"> 
Dandelion is a code designed to build comprehensive chemical databases by efficiently sampling reactive chemical space. Our approach combines fast tight-binding calculations with selective high-level refinement to generate high-quality datasets for Machine Learning Interatomic Potentials (MLIPs). The workflow consists of four phases:

1. **Reactant Preparation**: Generate diverse 3D structures from GDB-13 database
2. **Product Search**: Find reaction pathways using single-ended growing string method
3. **Landscape Search**: Sample transition states using nudged elastic band method
4. **Refinement**: Perform high-level DFT calculations using ORCA

This documentation guides the installation, setup, and usage of Dandelion.
</div>


## Git repository
<https://github.com/mhyeok1/dand/>
