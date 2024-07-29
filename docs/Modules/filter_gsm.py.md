---
layout: default
title: filter_gsm.py
parent: Modules
nav_order: 4
---

# filter_gsm.py

  Through this process, you can get filtered structures. This filtering algorithm excludes trivial pathways with strictly uphill energy trajectories, negligible energy variations, unfeasible 2 structures, or those that are repetitive.
  
There are some cases to be filtered :
  If xTB didn't converged or pyGSM terminated the execution based on its criteria, there will be no png file is generated.

Then the submodule `profile_filter` filters the cases which have wrong ts, too high or low barrier height, too small delta_e. 
`structure_filter ` can filter chemically absurd products, followed by unique filter which filters duplicates based on smiles. If there are more than one of same SMILES, pick the lowest barrier reaction.
