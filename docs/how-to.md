---
layout: default
title: How-to-use
nav_order: 3
---


# Getting Started

## Prerequisites
- Activate the conda environment:
```shell
conda activate ts
```

## Sample Data

<div align="center">
  <img width="1600" alt="all" src="https://github.com/user-attachments/assets/6ff5bf37-7ce5-4980-a268-ee0f1d2c185d">
</div>

Download the example structures [Here](https://github.com/mhyeok1/dand_docs/raw/refs/heads/docs/assets/mother_structures_for_tut.Zip)

We are interested in expanding the dataset from 5 given mother structures. 
First, each mother structure needs to be optimized to serve as a good starting point for GSM. This can be achieved by performing geometry optimization using GFN2-xTB. 
Ensure that all the prepared mother structures are in specific `input_path` and saved in `.xyz` file format. 

Your input structures should be organized as follows:

```
mother_strucs/
├── Cl7138/
│   └── ClGeom-m7138-i1-c1-opt/
│       └── struc.xyz
├── Cl7164/
│   └── ClGeom-m7164-i1-c1-opt/
│       └── struc.xyz
├── ...
```


# Command Reference

## 1. Sampling the reaction pathways

Basic command structure:
```shell
$ dand sample [-h] -i INPUT_PATH -o OUTPUT_PATH -n MAX_WORKERS
```


Parameters:


| Parameter                                      | Description                                                               |
|------------------------------------------------|---------------------------------------------------------------------------|
| `-h`, `--help`           | Displays the help message and exits the program.  |
| `-i`, `--input_path`     | Specifies the directory where the mother structures are stored.                 |
| `-o`, `--output_path`    | Specifies the directory where Dandelion output will be saved.              |
| `-n`, `--max_workers`    | Specifies the number of worker processes for parallel execution.          |



                      
Assuming your mother structures are saved as 'struc.xyz' in `/home/pekora/example/mother_strucs`, you can initiate sampling process with the following command:


```shell
$ dand sample -i /home/pekora/example/mother_strucs -o /home/pekora/example/outputs -n 30
```



Output files will be stored in `/home/pekora/example/outputs`.

The following six steps will be executed automatically:

----


Dandelion first generates possible driving coordinates(seeds) from each mother structure.

```
╔════════════════════════════════════════════════════════════════════╗
║                          1. Creating GSM                           ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/mother_strucs
  output_path: /home/pekora/example/outputs/1_gsm
  maxbreak: 2
  maxform: 2
  maxchange: 3
  minbreak: 0
  minform: 0
  minchange: 1
  ignore_single_change: True
  equiv_Hs: False

280 Seeds were generated from ClGeom-m7138-i1-c1-opt
276 Seeds were generated from ClGeom-m7164-i1-c1-opt
...

Creating GSM finished!
```

Based on generated GSM jobs, GSM can be executed. Some jobs can fail to converge or reach the product within the predefined maximum number of nodes and should be filtered out.

```
╔════════════════════════════════════════════════════════════════════╗
║                           2. Running GSM                           ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/output/1_gsm
  max_workers: 30

GSM on seeds: 100%|████████████████████████| 1406/1406 [4:57:13<00:00]
GSM finished!

```

Dandelion excludes some trivial pathways with strictly uphill energy trajectories, negligible energy variations, unfeasible structures, or those that are repetitive.

```
╔════════════════════════════════════════════════════════════════════╗
║                          3. Filtering GSM                          ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/outputs/1_gsm
  output_path: /home/pekora/example/outputs/2_gsm_filtered
  barrier_min: 5
  barrier_max: 200
  delta_e_min: 5

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7138-i1-c1-opt
Initial seeds:                   280
GSM success reactions:           115
Profile filtered reactions:       41
Structure filtered reactions:     38
Unique reactions:                 28
...

Filtering GSM finished!

```

Using the outputs of gsm, Dandelion runs climbing-image NEB. NEB optimizes the reaction pathways, relaxing the force of the bands of structures.

```
╔════════════════════════════════════════════════════════════════════╗
║                           4. Running NEB                           ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/output/2_gsm_filtered
  output_path: /home/pekora/example/output/3_neb
  max_workers: 30
  n_images: 10
  neb_fmax: 0.5
  cineb_fmax: 0.05
  steps: 500

Seeds: 100%|███████████████████████████████████| 144/144 [04:34<00:00]
xTB-NEB completed!

```

In the fifth step, data is filtered based on specific criteria. For example, non-convergent reactions and those without a single negative eigenvalue in their Hessian matrices are excluded. This ensures focus on structures near valid paths. NEB results are further refined to avoid redundant structural data. A new band iteration is chosen only when the cumulative Fmax exceeds 0.1 eV/Å, saving DFT calculations and preventing overfitting to narrow PES regions.

```

╔════════════════════════════════════════════════════════════════════╗
║                          5. Filtering NEB                          ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/output/3_neb
  output_path: /home/pekora/example/output/4_neb_filtered

Mothers: 100%|█████████████████████████████████████| 5/5 [00:20<00:00]

40/53 rxns were saved to /home/pekora/example/output/4_neb_filtered/reactions.json
Filtering NEB finished!

```

The sixth step is to compile samples in Hierarchical Data Format:
```

╔════════════════════════════════════════════════════════════════════╗
║                        6. Compiling samples                        ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/output/4_neb_filtered/reactions.json
  output_path: /home/pekora/example/output/xtb.h5
  fmax_threshold: 0.1

Compiling reactions: 100%|███████████████████████| 40/40 [00:03<00:00]
Compiling finished!

```
And there will be a newly generated file in your output path, the `xtb.h5` file.





## 2. Refining Energy and Force Labels

Structure sampling is now finished. The next step is to refine the energy and force labels at the DFT level.

```shell
$ dand refine [-h] -i INPUT_PATH -n MAX_WORKERS --orca ORCA
```

| Parameter                                      | Description                                                               |
|------------------------------------------------|---------------------------------------------------------------------------|
| `-h`, `--help`           | Displays the help message and exits the program. 
| `-i`, `--input_path`     | Specifies the path of working directory containing `xtb.h5`.             |
| `-n`, `--max_workers`    | Specifies the number of worker processes for parallel execution.          |
| `--orca`                 | Specifies the path of the orca executable file             |


{: .important }
The ORCA path must point to the **executable file**.

If you enter like this:
```shell
$ dand refine -i /home/pekora/example/outputs -n 15 --orca /home/pekora/package/orca/orca_5_0_4/orca
```
The refinement process includes two steps:

In this phase, we use DFT calculations with Orca 5.0.4. The default setting uses wB97X functional and 6-31(d) basis set, but these settings can be adjusted as needed.

```
╔════════════════════════════════════════════════════════════════════╗
║                         7. Refining forces                         ║
╚════════════════════════════════════════════════════════════════════╝
Arguments provided:
  input_path: /home/pekora/example/output/xtb.h5
  output_path: /home/pekora/example/output/wb97x.db
  max_workers: 15
  orca: /home/pekora/package/orca/orca_5_0_4/orca

Restarting calculation from /home/pekora/example/output/wb97x.db
640 points are skipped.

Formulas: 100%|██████████████████████| 2/2 [85:50:01<00:00, ? hour/it]
wB97X calculation finished!

```

You can check your compiled database wb97x.db using ASE:
```shell
$ ase db wb97x.db
id|age|user   |formula |calculator|    energy|natoms| fmax|pbc|charge|   mass
 1| 5d|pekora|C4ClH4NO|orca      |-20266.198|    11|5.874|FFF| 0.000|117.532
 2| 5d|pekora|C4ClH4NO|orca      |-20269.074|    11|0.470|FFF| 0.000|117.532
 3| 5d|pekora|C4ClH4NO|orca      |-20268.333|    11|5.994|FFF| 0.000|117.532
 4| 5d|pekora|C4ClH4NO|orca      |-20268.047|    11|1.195|FFF| 0.000|117.532
...
Rows: 53842 (showing first 20)
```


Finally, it compiles our wb97x.db sample in Hierarchical Data Format :
```
╔════════════════════════════════════════════════════════════════════╗
║                     8. Compiling final samples                     ║
╚════════════════════════════════════════════════════════════════════╝
Arguments provided:
  input_path: /home/pekora/example/output/wb97x.db
  output_path: /home/pekora/example/output/wb97x.h5

Compiled successfully!
```


# Checking Results

## ase db file

You can check how to access the ase db file in the [ase manual](https://wiki.fysik.dtu.dk/ase/ase/db/db.html).


{: .highlight }
> Launch visualization interface:
> ```shell
> ase db wb97x.db -w
> ```
> <img src="https://github.com/user-attachments/assets/5ea3be3b-a7e1-409a-a878-73d842e922e2" width="400">



## h5 file

You can check how to access the h5 file in the [hdfgroup webpage](https://www.hdfgroup.org/download-hdfview/)

{: .highlight }
The data structure of h5 files can be easily visualized using VS Code with [H5Web](https://github.com/silx-kit/h5web) extension.
<img src="https://github.com/user-attachments/assets/d95f1f5b-7bcd-43bf-9442-78836e87b2ad" width="400">



[Continue: Modules](https://mhyeok1.github.io/dand_docs/docs/Modules.html){: .btn .btn-purple }





