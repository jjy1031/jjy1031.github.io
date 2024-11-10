---
layout: default
title: filter_gsm.py
parent: SE-GSM
nav_order: 3
---

# filter_gsm.py

  Through this process, filtered structures can be obtained. This filtering algorithm excludes trivial pathways with strictly uphill energy trajectories, negligible energy variations, unfeasible structures, as well as redundant pathways.

 Certain cases need to be filtered :
If the xTB calculations fail to converge or pyGSM terminated the execution due to its criteria, no png file will be generated.

The submodule `profile_filter` filters the cases with transition states which have too high or low barrier height, or too small delta_e. 
`structure_filter` filters chemically absurd products, followed by `unique filter` which filters duplicates based on SMILES notation. If multiple identical SMILES are present, only the reaction with the lowest barrier is retained.
