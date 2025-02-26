---
layout: default
title: smiles_to_isoconfs.py
parent: Preparation
nav_order: 1
---

# smiles_to_isoconfs.py

This module generates stereoisomers from SMILES string, using RDKit and reasonable 3D structures using OpenBabel.

|  Parameter / Method    |  Tool | Description |
|---------------|-------|---------|
| `StereoEnumerationOptions` | RDkit | Generate possible stereoisomers for a molecule. |
| `--gen3d ` | Open Babel | Generate 3D coordinates. |
| `--confab ` | Open Babel | Generate diverse low-energy conformers. |
| `-m ` | Open Babel | Convert and store multiple input files. |



