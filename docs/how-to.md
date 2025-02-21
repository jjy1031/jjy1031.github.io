---
layout: default
title: How-to-use
nav_order: 3
---

# Example


This page provides a guide for using Dandelion, which efficiently generates an extensive database by sampling both equilibrium and reactive regions of chemical compound space.
<div align="center">
  <img width="1600" alt="all" src="https://github.com/user-attachments/assets/6ff5bf37-7ce5-4980-a268-ee0f1d2c185d">
</div>

You can download the structures from [Here](https://github.com/mhyeok1/dand_docs/raw/refs/heads/docs/assets/mother_structures_for_tut.Zip)

Let's assume we are interested in expanding the dataset from 5 given mother structures. First,  each mother structure needs to be optimized to serve as a good starting point for GSM. This can be achieved by performing geometry optimization using GFN2-xTB. Ensure that all the prepared mother structures are in specific `input_path` and saved in `.xyz` file format. 

```
mother_strucs
├── Cl7138
│   └── ClGeom-m7138-i1-c1-opt
│       └── struc.xyz
├── Cl7164
│   └── ClGeom-m7164-i1-c1-opt
│       └── struc.xyz
├── Cl7166
│   └── ClGeom-m7166-i1-c1-opt
│       └── struc.xyz
├── Cl7168
│   └── ClGeom-m7168-i1-c1-opt
│       └── struc.xyz
└── Cl7188
    └── ClGeom-m7188-i1-c1-opt
        └── struc.xyz
```

To run dandelion, your current conda environment should be **ts**.
```shell
$ conda activate ts
```

# dand sample

The grammar is like this:


```shell
$ dand sample [-h] -i INPUT_PATH -o OUTPUT_PATH -n MAX_WORKERS
```



| Parameter                                      | Description                                                               |
|------------------------------------------------|---------------------------------------------------------------------------|
| `-h`, `--help`           | Displays the help message and exits the program.                           |
| `-i`, `--input_path`     | Specifies the path where the mother structures are stored.                 |
| `-o`, `--output_path`    | Specifies the directory where Dandelion output will be saved.              |
| `-n`, `--max_workers`    | Specifies the number of worker processes for parallel execution.          |



                      
Assuming your mother structures are saved as 'struc.xyz' in `/home/pekora/example/mother_strucs`, you can initiate sampling process with the following command:



```shell
$ dand sample -i /home/pekora/example/mother_strucs -o /home/pekora/example/outputs -n 30
```



Output files will be stored in `/home/pekora/example/outputs`.

The following six steps will be executed automatically:



```


                                                     `;:`  BREAK 1 2
                                         .;:;         /    BREAK 3 4
        _____                   _      _;::;         `     ADD 1 3
        |  __ \                | |    | |';:;'
        | |  | | __ _ _ __   __| | ___| |  _  ___  _ __
        | |  | |/ _` | '_ \ / _` |/ _ \ | | |/ _ \| '_ \
        | |__| | (_| | | | | (_| |  __/ | | | (_) | | | |
        |_____/ \__,_|_| |_|\__,_|\___|_| |_|\___/|_| |_|

                   Chemical compound space sampling
           near transition state using xTB, SE-GSM and NEB
                          Ver. 0.6.2 by mlee



```

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
275 Seeds were generated from ClGeom-m7166-i1-c1-opt
276 Seeds were generated from ClGeom-m7168-i1-c1-opt
299 Seeds were generated from ClGeom-m7188-i1-c1-opt

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

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7164-i1-c1-opt
Initial seeds:                   276
GSM success reactions:           111
Profile filtered reactions:       42
Structure filtered reactions:     38
Unique reactions:                 32

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7166-i1-c1-opt
Initial seeds:                   275
GSM success reactions:            96
Profile filtered reactions:       31
Structure filtered reactions:     28
Unique reactions:                 25

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7168-i1-c1-opt
Initial seeds:                   276
GSM success reactions:            87
Profile filtered reactions:       37
Structure filtered reactions:     35
Unique reactions:                 29

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7188-i1-c1-opt
Initial seeds:                   299
GSM success reactions:           102
Profile filtered reactions:       40
Structure filtered reactions:     33
Unique reactions:                 30

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

Sixth step is to compile samples in Hierarchical Data Format:
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





# dand sample

Structure sampling is now finished. The next step is to refine the energy and force labels at the DFT level.
You can enter this command:

```shell
$ dand refine [-h] -i INPUT_PATH -n MAX_WORKERS --orca ORCA
```

| Parameter                                      | Description                                                               |
|------------------------------------------------|---------------------------------------------------------------------------|
| `-h`, `--help`           | Displays the help message and exits the program.                           |
| `-i`, `--input_path`     | Specifies the path of working directory containing `xtb.h5`.             |
| `-n`, `--max_workers`    | Specifies the number of worker processes for parallel execution.          |
| `--orca`                 | Specifies the path of the orca binary file             |


{: .important }
Ensure that the path of the orca should point to an orca **executable file**.

If you enter like this:
```shell
$ dand refine -i /home/pekora/example/outputs -n 15 --orca /home/pekora/package/orca/orca_5_0_4/orca
```
The two steps below will be executed automatically!

```
         ⢀⣀⣀⣀⣀⣀⡀       ⢀⢀⣀⢀⠞⠖⠁⠡⡂⡆ ⡠⢀⡀
         ⠺⢿⣿⣿⣿⣿⣿⣿⣷⣦⣠⣤⣤⣤⣄⣀⣀ ⡏⢸  ⢀ ⠣⠈ ⡠⡋⡨⡋⡂
           ⠙⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣷⣦⣄⡀⡎⢀⡰⢀⢎⠌⢀⠔⣐⠠⣄⣀
       ⢀ ⡔⢀⣴⣾⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⠿⠿⠿⣿⣿⣷⣄⠂ ⢊⠎ ⠠⠂⡀⠕⠌⠌ ⡄⡠⢄
    ⢀⡆⠄⠁⢈⢠⣾⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣀   ⣀⣿⣿⣿⣆⠐    ⡨⠒⠁⡀⢠⣦⠍⠇⡀⢲⠂⡄⠄
   ⠨⡀⠑⡈ ⢠⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡄   ⠈  ⣬⠠⣰⣿ ⢳⢹⡄⡆⠄⢀⢼
 ⡄⠱⠈⠁⠑⢄⠐⣾⣿⣿⡿⠋⠁⣀⣠⣬⣽⣿⣿⣿⣿⣿⣿⠿⠿⠿⠿⠿⠿⠿⠿⠟⠁⡟⣅⡢⠁⠠⠜⡄⡑⢌⢧⡀ ⡀⣰⢁⡐⢁⢄⣡⣧⡤⠄
⠠⡐⠓⠂⠌  ⢀⣿⣿⡏⢀⣴⣿⠿⠛⠉⠉⠶⢸⣿⣿⠿⠁⠢⠨⢀⣻⣿⣿⣿⣿⢟⣿⣝⠂  ⠠⡠⢆⠈⡂⠱⡇ ⣅⠫⠂⡠⢂⡪⠋  ⠁⡆
⡶⠉ ⢀⡀⠁⡁⢸⣿⣿⢠⣾⡟⠁⣿⣿⡇ ⢀⠈⠉⠁    ⣀⠷⣹⣏⣷⢏⠹⠁    ⠈⢈ ⢇ ⢸⠱⢸⡏⡀⡶⡸⠎  ⠰⠁⡸
⢈⡕⡈⠁⠐⠂⢀⢸⣿⣿⣾⠏⣿⣿⡿⣻⣿⢞⡢⠄ ⠈ ⡀⡤⠂⠁⠉⠌       ⢀⢀⠠⠐⢄ ⡀⢆⠎⢹⣶⣷⣧⡈⠈⠉⠤⠂⠉⢀⠱⡀
⢠⡊    ⠁⣸⣿⣿⣿⣀⠉⡻⡏⠋⠁ ⠁⠒⠒⡀⣍⠍⠁ ⡀ ⢠⠂     ⢀⠈⠄⢀⠄⡒⠅⠈⢄⢡ ⢿⣿⣷⣿⡄ ⠐⠄⠤ ⠜⢀
⠐⠁ ⠤⠒⢠⣾⣿⣿⣿⣿⣿⣷⣄⢄  ⢀ ⡏ ⢰⣃⠊⡐⠐⠁⢀⠈  ⣀ ⠰⠢⢀⠂⡰⠈⠂  ⡱⠂⢂⡇⡈⠻⢿⣿⠇   ⡤⠄⣀⡰⠁
    ⠁⣾⣿⣿⣿⣿⣿⣿⣿⣿⣦ ⠄ ⠉   ⠸⠫⢞⠈⣰⠈ ⡐⢲⣿⡏       ⢠⡾ ⣀⠊⢱ ⠠⡀    ⢈⢀⡐⠤⣕⡄
    ⢰⣿⡿⠛⠉   ⠈⠙⠛         ⠈⠈ ⠻⠔⠁⢸⡍⡇      ⢀⣏ ⢀⠠⠆ ⠣⡀⠈⡠⡀⠉⠢⡤⠢⣈⡡⣢⠦
⠈⠁           ⢻⣇               ⢸⡇⡇      ⣼⡿⠉  ⢀⡇ ⠑⡄⠑⣌⢄ ⠙⢄⠠⡪⣅
             ⠈⣾⡆              ⢸⣏⡇     ⢠⣿⠇   ⠸⢌⢢⢄⡠⠣⠈⠢⡁⡈⣎⢢⡬⠃

               Energy refinement on samples using orca
                          Ver. 0.6.2 by mlee
```

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
 5| 5d|pekora|C4ClH4NO|orca      |-20266.059|    11|3.630|FFF| 0.000|117.532
 6| 5d|pekora|C4ClH4NO|orca      |-20266.920|    11|4.553|FFF| 0.000|117.532
 7| 5d|pekora|C4ClH4NO|orca      |-20266.081|    11|1.022|FFF| 0.000|117.532
 8| 5d|pekora|C4ClH4NO|orca      |-20265.240|    11|4.314|FFF| 0.000|117.532
 9| 5d|pekora|C4ClH4NO|orca      |-20265.014|    11|7.924|FFF| 0.000|117.532
10| 5d|pekora|C4ClH4NO|orca      |-20268.711|    11|3.512|FFF| 0.000|117.532
11| 5d|pekora|C4ClH4NO|orca      |-20266.886|    11|5.938|FFF| 0.000|117.532
12| 5d|pekora|C4ClH4NO|orca      |-20266.322|    11|3.704|FFF| 0.000|117.532
13| 5d|pekora|C4ClH4NO|orca      |-20266.081|    11|1.021|FFF| 0.000|117.532
14| 5d|pekora|C4ClH4NO|orca      |-20265.532|    11|3.059|FFF| 0.000|117.532
15| 5d|pekora|C4ClH4NO|orca      |-20267.115|    11|3.885|FFF| 0.000|117.532
16| 5d|pekora|C4ClH4NO|orca      |-20262.912|    11|6.171|FFF| 0.000|117.532
17| 5d|pekora|C4ClH4NO|orca      |-20268.863|    11|1.657|FFF| 0.000|117.532
18| 5d|pekora|C4ClH4NO|orca      |-20265.663|    11|4.222|FFF| 0.000|117.532
19| 5d|pekora|C4ClH4NO|orca      |-20263.405|    11|5.723|FFF| 0.000|117.532
20| 5d|pekora|C4ClH4NO|orca      |-20267.567|    11|5.143|FFF| 0.000|117.532
Rows: 53842 (showing first 20)
```


{: .note }
> You can check how to use the ase db file in the ase manual.
>
> <https://wiki.fysik.dtu.dk/ase/ase/db/db.html>


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

{: .note }
> The data structure of h5 files can be easily visualized using VS Code extension [H5Web](https://github.com/silx-kit/h5web)
> ![image](https://github.com/user-attachments/assets/d95f1f5b-7bcd-43bf-9442-78836e87b2ad)



[Continue: Modules](https://mhyeok1.github.io/dand_docs/docs/Modules.html){: .btn .btn-purple }





