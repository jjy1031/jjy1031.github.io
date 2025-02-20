---
layout: default
title: create_gsm.py
parent: SE-GSM
nav_order: 1
---

# Create GSM jobs

In this procedure, Dandelion generates possible GSM jobs or seeds, from each optimized mother structure. The overall algorithm calculates the number of bonds to be broken or added, determines possible reactions, and generates all viable driving coordinates. You can verify that all possible GSM jobs are generated from your optimized mother structures. 

  ```
  ├── ClGeom-m7138-i1-c1-opt
  │   ├── gsm0000
  │   ├── gsm0001
  │   ├── gsm0002
  ...
  ├── ClGeom-m7164-i1-c1-opt
  │   ├── gsm0000
  │   ├── gsm0001
  │   ├── gsm0002
  ...
  ```

Each GSM job is organized into a directory containing three files:

| File          | Description                                                                  |
|---------------|------------------------------------------------------------------------------|
| `gsm.sh`      | A Bash script that initiates the GSM calculation process.                   |
| `params.log`  | A log file detailing the parameters used and the connection limits applied.  |
| `ISOMERS.txt` | Contains information on bond breaking and formation in the calculated reactions. |



## params.log

```
Connection limits:
  H: 1, 1
  C: 2, 4
  N: 1, 3
  O: 1, 2
  F: 1, 1
  S: 1, 2
  CL: 1, 1
  BR: 1, 1
maxbreak = 2
maxform = 2
maxchange = 3
single_change = False
equiv_Hs = False
minbreak = 0
minform = 0
minchange = 1

```

| Parameter        | Description                                                 | Default |
|------------------|--------------------------------------------------------------|-------|
| `Connection Limits` | Minimum and maximum bonds allowed for each atom.          |       |                    
| `maxbreak`     | Maximum number of bonds that can be broken in a reaction.      |   2   |
| `maxform`      | Maximum number of bonds that can be formed in a reaction.      |   2   |
| `maxchange`     | Maximum number of total bond changes allowed in a reaction.   |   3   |
| `single_change` | Consider single bond changes (e.g., nbreak=1, nform=0) or not.| False |
| `equiv_Hs`    | Treat equivalent hydrogen atoms as unique or not.               | False |
| `minbreak`    | Minimum number of bonds that can be broken in a reaction.       |   0   |
| `minform`     | Minimum number of bonds that can be formed in a reaction.       |   0   |
| `minchange`   | Minimum number of total bond changes allowed in a reaction.     |   1   |




## ISOMERS.TXT

  ```
  BREAK 5 6
  ADD 4 6
  ADD 3 6
  ```


