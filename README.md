
# Finding binding sites using OpenMM 

1) Take any protein, feed through CHARMM-GUI to generate an input file. The final step (step3 for solvated, step5 for membranated) stepX_assembly.pdb is required for 3) below. 

2) `drug_parameterization.ipynb`: Openforcefield to generate ligand parameterization. Just input the isomeric smiles code and RDKit + openforcefield will generate correct pdbfile and AMBER forcefield-compatible parameters

3) `system_setup.ipynb`: System setup. This combines the drug system with the membranated protein system, and gradually releases constraints on the protein over ~25 ns. Drug molecules have a pairwise repulsive bias that drops off exponentially with distance to prevent aggregation. If using with solvated protein only, change z_range to mirror x_range and y_range i.e. minmax of protein coordinates, instead of lipid coordinates. 

4) Determine the binding site by any means possible. Suggest removing the protein restraint completely, or at least replacing with a alpha-carbon only restraint. Use any combination of simulated tempering, generalised-REST, metadynamics, etc to determine binding site. 


https://dont-be-afraid-to-commit.readthedocs.io/en/latest/git/commandlinegit.html
