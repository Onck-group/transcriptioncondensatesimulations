# Transcription Condensate simulations

Simulation details for the manuscript 'Selective phase separation of transcription factors is driven by orthogonal molecular grammar'. Preprint available on Biorxiv: DOI: [10.1101/2024.04.12.589262](https://doi.org/10.1101/2024.04.12.589262
).

## General simulation files

In the `general` directory, the bonded (angle and dihedral) potential files for gromacs are present as `xvg` files, alongisde the MDP settings for the simulations.

## Simulation details

The simulations are collected into a directory based on the ion concentration of the simulation (in mM):

- 150
- 200
- 250
- 300
- 500

Within these directories is a directory for composition, labelled with the pattern `{species (protein) name}-{frequency}` for each species present separated by `__` (double underscore) between species.

Each Directory contains the following files:

- *multimolsystem.pdb* : System PDB file for the initial configuration.
- *system.ndx* : System ndx file
- *polymer.top* : System topolgy file
- *forcefield.itp* : ITP topogolgy file for particle definitions (global settings for the 1BPA v2.1 forcefield.
- *{species name}.itp* files : ITP topology files- one per species present in the system.
- *nonbondedtable.xvg* : Tabulated GROMACS non-bonded interactions used for all interactions except cation-pi interactions
- *nonbondedtable_RK_FYW.xvg* : Tabulated GROMACS non-bonded interactions used for cation-pi interactions
- *simulation_commands.json* : JSON file containing the GROMACS simulation commands.

  ### GROMACS command calls

  The commands within the `simulation_commands.json` file are called in the following order:
  - small_editconf
  - small_EM_grompp
  - small_EM_mdrun
  - small_EQ_grompp
  - small_EQ_mdrun
  - small_EQ_NPT_grompp
  - small_EQ_NPT_mdrun
  - trjconv
  - trjconv_cluster
  - large_editconf
  - large_EM_grompp
  - large_EM_mdrun
  - large_EQ_grompp
  - large_EQ_mdrun


