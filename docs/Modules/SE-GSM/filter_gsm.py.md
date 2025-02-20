---
layout: default
title: filter_gsm.py
parent: SE-GSM
nav_order: 3
---

# filter_gsm.py

Through this process, we parse some datas to decide which data should be filtered from gsm log file. This filtering algorithm excludes trivial pathways with strictly uphill energy trajectories, negligible energy variations, unfeasible structures, as well as redundant pathways. At first, this module reads gsm job files to parse the energy of each node, transition state (TS) energy or the indexes of the reactant/product/TS nodes.

Certain cases need to be filtered :
If the xTB calculations fail to converge or pyGSM terminated the execution due to its criteria, no png file will be generated.


| Method         | Description                                                               |
|------------------------|-----------------------------------------------------------------|
|    `profile_filter`    |  Filter gsm success reactions by checking transition state index, barrier height and delta_e.  |
|     `structure_filter` |   Filter chemically absurd structures. |
|     `unique_filter`    |   If multiple identical SMILES are present, only the reaction with the lowest barrier is retained. |
