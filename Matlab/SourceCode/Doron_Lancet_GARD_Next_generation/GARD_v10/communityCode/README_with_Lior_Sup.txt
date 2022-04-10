Lior Segev  - supplemental 22 Jan 2019

Added two matlab file
1. cluster_jl.m
2. cluster_jl_orient.m

downloaded from: 
https://github.com/jessiehl/networkmodularityscripts

Omer - original file

Accompanying code for paper "Predicting Proto-Species Emergence in Simulated
Complex Pre-Biotic Network", by Markovitch & Krasnogor.

Please also see the full manuscript and its supplementary materials.

Written in 2016 by Omer Markovitch,
School of Computer Science, Newcastle University

To the extent possible under law, the author(s) have dedicated all copyright
and related and neighbouring rights to this software to the public domain
worldwide. This software is distributed without any warranty.

See a copy of the CC0 Public Domain Dedication distributed along with this
software or visit: http://creativecommons.org/publicdomain/zero/1.0/

Please note that GARDv10 was introduced in the following publication:
Markovitch and Lancet, "Excess Mutual Catalysis Is Required for Effective Evolvability",
Artificial Life (2012); doi:10.1162/artl_a_00064


DESCRIPTION
-----------
Beta_louvain.m; receives a random-seed (integer number) and generates a
lognormal beta network using GARD10, than Louvain’s MATLAB function
cluster_jl_orient is run. Output out.indices is an array holding for each
molecule the index of the community it belongs to.

Beta_infomap.m: receives a random-seed (integer number) and generates a
lognormal beta network using GARD10, than saves the b to disk and run Infomap
as an externally program (UNIX or Windows). Output out.indices is an array
holding for each molecule the index of the community it belongs to.

Beta_oslom.m: similar to Beta_infomap.m, running program oslom_dir. Ouput
out.indices is an array of MATLAB cells, holding for each molecule a list of
indices of communities it belongs to.

getmaxrealevec.m receives a beta (or b_pseudo) and return as its first output
the eigenvector with the highest real eigenvalue.


RUN
---
It is assumed that MATLAB is already installed and running, and that GARD10 has
been extracted and that the path to GARD10 is already added to MATLAB.

Usage example: out=Beta_louvain(45); out.indices(:);

Usage example: b=tgs_newbeta_v10(45); [evec, eval]=getmaxrealevec(b); eval, plot(evec);
