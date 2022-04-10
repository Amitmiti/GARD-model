# GARD-model
Code repository for the scientific paper "Protobiotic network reproducers are compositional attractors: enhanced probability for life’s origin"

The repository consists of two parts - the Matlab GARD simulation folder, and the Python post-analyses folder.
To run the GARD model, you can choose one of two Matlab scripts. The script "find_beta_mat_that_generate_N_compotypes" is a script designed to quickly measure composomes for different beta matrices. The other script, "generate_compositions_within_a_generation", provides temporal compositions and fluxes of each chemical step of a simulation, based on input parameters. To run both scripts, make sure the folder "SourceCode" is added to the active path of Matlab.

The Python post-analysis folder contains the scripts used to analyze the GARD simulation runs and produce the analyses depicted in the manuscript. The input to most of these scripts are runs of the GARD Matlab simulation. A second common input is a list of pre-computed composomes, found in the Python folder and in the supplementary files of the manuscript.
