
# Binding site ID pipeline:

1) Take any protein, feed through CHARMM-GUI to generate an input file. The final step (step3 for solvated, step5 for membranated) stepX_assembly.pdb is required for 3) below. 

2) Run `drug_parameterization.ipynb`: Openforcefield to generate ligand parameterization. Just input the isomeric smiles code and RDKit + openforcefield will generate correct pdbfile and AMBER forcefield-compatible parameters

3) Run `system_setup.ipynb`: System setup. This combines the drug system with the membranated protein system, and gradually releases constraints on the protein over ~25 ns. Drug molecules have a pairwise repulsive bias that drops off exponentially with distance to prevent aggregation. If using with solvated protein only, change z_range to mirror x_range and y_range i.e. minmax of protein coordinates, instead of lipid coordinates. 

4) Determine the binding site. Suggest removing the protein restraint completely, or at least replacing with an alpha-carbon only restraint. Use any combination of simulated tempering, generalised-REST, metadynamics, etc. `determine_weights.ipynb` will equilibrate weights for either simulated tempering or serial g-REST 

5) Run `analysis.ipynb` to calculate relative binding site preferences based on histograms.  




<!---
https://dont-be-afraid-to-commit.readthedocs.io/en/latest/git/commandlinegit.html
-->
