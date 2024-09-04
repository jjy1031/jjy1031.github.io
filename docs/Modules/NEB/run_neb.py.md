---
layout: default
title: run_neb.py
parent: Modules
nav_order: 5
---



# run_neb.py

The Nudged Elastic Band method is to find the Minimum Energy Path between a given initial and final state of a transition. It is neccessary to construct a set of images between the initial and final state by interpolation to find MEP. And to optimize this path, we have to minimize the force acting on the image. So, dandelion runs Cl-NEB on reaction path to optimize this.

The generated output files have some information about Minimum Energy Path(MEP).

```
ClGeom-m7138-i1-c1-opt-gsm0019
├── converged
├── fitlist.npy
├── fmaxs.json
├── mep.gif
├── mep.png
├── mep.xyz
├── neb.db
├── product.png
├── product.xyz
├── reactant.png
├── reactant.xyz
├── transition_state.png
└── transition_state.xyz
```

You can see the process of path optimization in `mep.png`

![mep](https://github.com/user-attachments/assets/ea3af721-54a0-482b-b42f-efa8d2d38512)

Also, `mep.gif` can show you how the reaction occurs.

![KakaoTalk_20240722_153538363](https://github.com/user-attachments/assets/361928e3-a4a5-412e-b5c9-12afbcc55a8a)
