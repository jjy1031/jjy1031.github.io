---
layout: default
title: How-to-use
parent: User guide
nav_order: 2
---

# Example

This page provides a general overview of dandelion.

We used 5 mother structures to 

![struc_cl7138](https://github.com/user-attachments/assets/3adec694-1ce6-4296-adfe-a96e95b3f621)
![struc_cl7164](https://github.com/user-attachments/assets/289683e0-1571-494f-bf1e-ca909cd7cd33)
![struc_cl7166](https://github.com/user-attachments/assets/dec9375a-694a-4b0a-8e1a-31008cc683a5)
![struc_cl7168](https://github.com/user-attachments/assets/404fd715-895d-4ef6-8120-8089f262cf6e)
![struc_cl7188](https://github.com/user-attachments/assets/c53230a7-b93a-403b-81b6-6e9cdc0a1ae0)

Download mother structures in path `/home/jjy1031/example/mother_strucs`

Make sure your current conda environment is **ts**

Move your current directory ( working directory ) to path which dandelion_sample.py is located.

You can enter this for more information:
``` python
python dandelion_sample.py -h
```

```python

usage: dandelion_sample.py [-h] -i INPUT_PATH -o OUTPUT_PATH -n MAX_WORKERS

Do SEGSM and NEB from mother structures, Other parameters can be set in each
modules

options:
  -h, --help            show this help message and exit
  -i INPUT_PATH, --input_path INPUT_PATH
                        Input path of mother structures
  -o OUTPUT_PATH, --output_path OUTPUT_PATH
                        Output path of dandelion
  -n MAX_WORKERS, --max_workers MAX_WORKERS
                        Number of worker processes
```

If you enter this:
```python
python dandelion_sample.py -i /home/jjy1031/example/mother_strucs -o /home/jjy1031/example/outputs -n 10
```

Total 6 steps below will be executed automatically.

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
                          Ver. 0.6.0 by mlee

```

First step is to 

```
╔════════════════════════════════════════════════════════════════════╗
║                          1. Creating GSM                           ║
╚════════════════════════════════════════════════════════════════════╝



Arguments provided:
  input_path: /home/jjy1031/example/mother_strucs
  output_path: /home/jjy1031/example/outputs/1_gsm
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

Second step is to

```

╔════════════════════════════════════════════════════════════════════╗
║                           2. Running GSM                           ║
╚════════════════════════════════════════════════════════════════════╝



Arguments provided:
  input_path: /home/jjy1031/example/outputs/1_gsm
  max_workers: 10

GSM on seeds: 100%|██████████████████████████| 1406/1406 [00:00<00:00]
GSM finished!

```

Third step is to:

```
╔════════════════════════════════════════════════════════════════════╗
║                          3. Filtering GSM                          ║
╚════════════════════════════════════════════════════════════════════╝



Arguments provided:
  input_path: /home/jjy1031/example/outputs/1_gsm
  output_path: /home/jjy1031/example/outputs/2_gsm_filtered
  barrier_min: 5
  barrier_max: 200
  delta_e_min: 5


◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7138-i1-c1-opt
Initial seeds:                   280
GSM success reactions:             0
Profile filtered reactions:        0
Structure filtered reactions:      0
Unique reactions:                  0

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7164-i1-c1-opt
Initial seeds:                   276
GSM success reactions:             0
Profile filtered reactions:        0
Structure filtered reactions:      0
Unique reactions:                  0

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7166-i1-c1-opt
Initial seeds:                   275
GSM success reactions:             0
Profile filtered reactions:        0
Structure filtered reactions:      0
Unique reactions:                  0

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7168-i1-c1-opt
Initial seeds:                   276
GSM success reactions:             0
Profile filtered reactions:        0
Structure filtered reactions:      0
Unique reactions:                  0

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7188-i1-c1-opt
Initial seeds:                   299
GSM success reactions:             0
Profile filtered reactions:        0
Structure filtered reactions:      0
Unique reactions:                  0

Filtering GSM finished!
```

Fourth step is to:

```
╔════════════════════════════════════════════════════════════════════╗
║                           4. Running NEB                           ║
╚════════════════════════════════════════════════════════════════════╝



Arguments provided:
  input_path: /home/jjy1031/example/outputs/2_gsm_filtered
  output_path: /home/jjy1031/example/outputs/3_neb
  max_workers: 10
  n_images: 10
  neb_fmax: 0.5
  cineb_fmax: 0.05
  steps: 500

Seeds: |                                               | 0/0 [00:00<?]
xTB-NEB completed!
```

Fifth step is to :

```
╔════════════════════════════════════════════════════════════════════╗
║                          5. Filtering NEB                          ║
╚════════════════════════════════════════════════════════════════════╝



Arguments provided:
  input_path: /home/jjy1031/example/outputs/3_neb
  output_path: /home/jjy1031/example/outputs/4_neb_filtered

Mothers: |                                             | 0/0 [00:00<?]

0/0 rxns were saved to /home/jjy1031/example/outputs/4_neb_filtered/reactions.js
Filtering NEB finished!
```

Sixth step is to :
```
╔════════════════════════════════════════════════════════════════════╗
║                        6. Compiling samples                        ║
╚════════════════════════════════════════════════════════════════════╝



Arguments provided:
  input_path: /home/jjy1031/example/outputs/4_neb_filtered/reactions.json
  output_path: /home/jjy1031/example/outputs/xtb.h5
  fmax_threshold: 0.1

Compiling reactions: |                                 | 0/0 [00:00<?]
Compiling finished!
```

And there will be generated files in your output path.
We can easily see using tree :

```
(ts) [jjy1031@ne00 example]$ tree -L 2
.
├── 0_mothers.zip
├── mother_strucs
│   ├── Cl7138
│   ├── Cl7164
│   ├── Cl7166
│   ├── Cl7168
│   └── Cl7188
└── outputs
    ├── 1_gsm
    ├── 4_neb_filtered
    ├── xtb.h5
    └── xtb.h5.index.json
```

In outputs/1_gsm, there are many seeds generated by segsm from each mother structures

```
(ts) [jjy1031@ne00 outputs]$ tree -L 3
├── 1_gsm
│   ├── ClGeom-m7138-i1-c1-opt
│   │   ├── gsm0000
│   │   ├── gsm0001
│   │   ├── gsm0002
│   │   ├── gsm0003
│   │   ├── gsm0004
│   │   ├── gsm0005
│   │   ├── gsm0006
...
├── ClGeom-m7168-i1-c1-opt
│   │   ├── gsm0000
│   │   ├── gsm0001
│   │   ├── gsm0002
│   │   ├── gsm0003
│   │   ├── gsm0004
│   │   ├── gsm0005
│   │   ├── gsm0006
│   │   ├── gsm0007
...

```
In outputs/4_neb_filtered :
```
├── 4_neb_filtered
  └── reactions.json
```

Next step is to execute dandelion_refine.py

You can enter -h or --help if u want more information:
```
(ts) [jjy1031@ne00 dandelion]$ python dandelion_refine.py -h
usage: dandelion_refine.py [-h] -i INPUT_PATH -n MAX_WORKERS --orca ORCA

Refine force on obtained samples, Other parameters can be set in each modules

options:
  -h, --help            show this help message and exit
  -i INPUT_PATH, --input_path INPUT_PATH
                        Input path of working directory containing xtb.h5
  -n MAX_WORKERS, --max_workers MAX_WORKERS
                        Number of worker processes
  --orca ORCA           Path of the orca binary file
```

If you enter like this:
```
(ts) [jjy1031@ne00 dandelion]$ python dandelion_refine.py -i /home/jjy1031/example/outputs -n 10 --orca ORCA
```

2 steps below will be executed automatically !
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
                          Ver. 0.6.0 by mlee
```

```
╔════════════════════════════════════════════════════════════════════╗
║                         7. Refining forces                         ║
╚════════════════════════════════════════════════════════════════════╝



Arguments provided:
  input_path: /home/jjy1031/example/outputs/xtb.h5
  output_path: /home/jjy1031/example/outputs/wb97x.db
  max_workers: 10
  orca: ORCA

Created db file at /home/jjy1031/example/outputs/wb97x.db

Formulas: |                                 | 0/0 [00:00<?, ? hour/it]
wB97X calculation finished!
```

```
╔════════════════════════════════════════════════════════════════════╗
║                     8. Compiling final samples                     ║
╚════════════════════════════════════════════════════════════════════╝



Arguments provided:
  input_path: /home/jjy1031/example/outputs/wb97x.db
  output_path: /home/jjy1031/example/outputs/wb97x.h5

Compiled successfully!
```






