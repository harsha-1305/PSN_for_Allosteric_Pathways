# PSN_for_Allosteric_Pathways

Here, we explore protein allostery (ligand binding at a distal site influencing function at a remote active site) by modifying the algorithm for identifying probable allosteric pathways (as used in Wang et al., 2020) to work with the following schemes of edge weights assignment; (i) the original contacts-based weights assignment, (ii) Direct Coupling (Gautier et al., 2018) inspired edge assignment based on evolutionary multiple sequence alignments (MSAs) (iii) Dynamic Coupling (Yao et al., 2016) inspired edge assignment derived from Molecular Dynamics simulations, and (iv) our novel approach, using coupling free energies derived from the block Wako-Saitô-Muñoz-Eaton (bWSME) Model (Ooka et al., 2022; Gopi et al., 2019) for edge assignment. 

Refer ____ for complete information.

## Overview

The majority of this pipeline is built on a sequence of python notebooks intended to be run directly on Google Collab. Generation of couple maps using the bWSME-based methods requires running of two MATLAB scripts as well.

The broad workflow is as folllows -
1. Pick protein of interest
2. Pick mode of edge assignment
3. Generate coupling matrix for protein using edge assignment method
4. Perform visualization/community detection/allosteric pathway identification/other analysis

---

## Generation of coupling maps

Four methods of coupling map generation are explored here -

### 1. Contact-based edge weight assignment
Use the notebook `Coupling Scripts\create_contact_map.ipynb` to generate contact-based edge weight assignment via Google collab. You would be required to upload your protein structure file `pname.pdb`, and the output coupling `pname_contact_coupling.csv` will be generated.

### 2. Direct coupling-based edge weight assignement
`To be filled by Skanda`

### 3. Dynamic coupling-based edge weight assignment
Requires the MD trajectory `.xtc` and the initial topology file `.gro`, which are uploaded to `Coupling Scripts\create_dynamic_coupling.ipynb` while run on Google collab. The output coupling `pname_dynamic_coupling.csv` will be generated.

### 4. bWSME-based edge weight assignment
Required protein structure file `pname.pdb` and formatted stride output `pname_struct.txt` (obtained from http://webclu.bio.wzw.tum.de/stride/) as inputs for `Coupling Scripts\cmapCalcElecBlock.m`, which is to be run locally on MATLAB. This script creates a lot of output files in the same directory, hence, run `Coupling Scripts\FesCalc_Block_full.m` from the same directory next (again on MATLAB). The output from this, `pname_couplings.csv`, can then be passed into `Coupling Scripts\convert_mat_to_py.ipynb` when run on Google Collab, which outputs the final `pname_bWSME_coupling.csv`.

---

## Visualization of edges and community detection

Currently, visualization of top x% of edges by magnitude, along with community detection by Girvan-Newman and Greedy Modularity algorithms are supported. To perform the same, upload `pname.pdb` and `pname_method_coupling.csv` to `Analysis Scripts\vis_and_comunity.ipynb`, which then generates required visualizations.

---

## Allosteric pathways identification
`To be filled by Skanda`

---

In case of any issues, reach out to original authors at bs23b003@smail.iitm.ac.in and be23b015@smail.iitm.ac.in

Thank you.

