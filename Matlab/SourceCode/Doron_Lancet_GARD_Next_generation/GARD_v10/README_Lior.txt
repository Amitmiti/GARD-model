The objective is to find a function that finds the start and end times of a composome.
Possible candidates:

1. cluster_traces.m
2. getcomposometime_v10.m -
3. pmc_beta_v10 - a function that checks that there are not a lot of big values
   on the diagonal of the matrix, which makes for a good beta matrix
4. tgs_acluster.m -
5. tgs_clust.m -
6. tgs_nondrift.m
7. tgs_tagtrace.m - call tgs_kmeans.m


27 June 2018 - Lior's comments
Omer's code uses K-means clustering algorithm to find the composomes and then
he can use the getcomposometime_v10 on tags variable to find the start and end
times of the most frequent composome. The tag variable associate every cluster
found to its position along the trace. This means that I have to write all
analysis code by myself.

pmc evaluates the main diagonal elements in by calculating the following:
norm = sum(diagonal(beta))*ng and summing on the entire matrix where each element is
normalized by "norm". This may prove in edquate as one relatively big element
along the diagonal may skew the results -> DISCUSS WITH DORON.

Added this line in tgs_agard_v10 to fix the rng (random number generator) state
in between lines =>
(line 44) rand('state', p.seed(1));  % added by Lior Segev 2018 June 6 to retain results

1 July 2018 - Lior's comments
in this statement p.seed = [129 21 39], the first number is the seed for Generating
beta matrix, the second number is the seed for generating the initial population of
a composition.

The above numbers give pmc = 0.43 for beta

05 July 2018 - Lior's comments
tgs_nondrift.m is the function responsible to determine composomes or non drift compisitions
as they reffered to in the text. Two techniques are used to determine these.
1. uses an avg H value between previous and next generation and uses a threshold to determine if a single compisition is a composome.
2. Calculates H between consecutive generations and takes groups of larger or equal than driftsize within a predetrimined threshold.

15 July 2018 - Sunday - Lior's comments
I found that the composomes were the same in all runs (1600) 40 beta * 40 initial compositions. This didn't make sense.
I found one error in the initialization of the correct seed for the composition. -> fixed that.
I wanted to check how important the initial condition are and I found that there was no dependence on initial compositions runs -> strange
Now, I find that the nmax is also set in the tgs_grow -> this is wrong of course.

16 July 2018 same as 15 July only I ran the run in the cluster since the local run took too long.
I found that Omer is using p.splitsize as a means to control the size of the cluster. I have set it to be 0.1 to set the nmax =100 when NG = 1000
