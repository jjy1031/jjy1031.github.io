---
layout: default
title: How-to-use
parent: User guide
nav_order: 2
---

# Example

This page provides a general overview of dandelion.

We used 5 mother structures to 

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




