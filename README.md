draft.

# Finding binding sites using OpenMM 

1) Take any protein, feed through CHARMM-GUI to generate an input file. step5_assembly.pdb is required for 3) below. 

2) Openforcefield to generate ligand parameterization. Just input the isomeric smiles code and RDKit + openforcefield will generate correct pdbfile and AMBER forcefield-compatible parameters

3) System setup. This combines the drug system with the solvated/membranated protein system, and gradually releases constraints on the protein over ~25 ns. Drug molecules have a pairwise repulsive bias that drops off exponentially with distance to prevent aggregation. 

4) Determine the binding site by any means possible. Suggest removing the protein restraint completely, or at least replacing with a alpha-carbon only restraint. Use any combination of simulated tempering, generalised-REST, metadynamics, etc to determine binding site. 
