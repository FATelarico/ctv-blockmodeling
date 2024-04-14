---
name: Blockmodeling
topic: Blockmodeling
maintainer: Fabio Ashtar Telarico, Saint-Clair Chabert-Liddell, Carl Nordlund
email: Fabio-Ashtar.Telarico@fdv.uni-lj.si
version: 2023-04-14
source: https://github.com/FATelarico/ctv-blockmodeling
---

This CRAN Task View contains a list of packages that can be used for finding groups in networks (also known as _relational data_ and _graphs_) based on a selected definition of equivalence. 

*Blockmodeling* (BM) is a set of statistical models used to cluster relational data. The various available BMs cluster units adopt different definitions of equivalence based on which the units are grouped: _structural_, _regular_, _generalised_, and _stochastic_ equivalence.

Furthermore, each of these equivalences can be implemented in conjunciton with different conceptualisations of the networks: static, temporal, linked, multi-level, and so on.

Moreover, the literature offers various computational methods to determine the final partition: hierarchical clustering, local optimisation, k-means, expectation-maximisation, and so on.

This task view includes models all R packages that cluster units in relational data regardless of the definition of network and the conceptualisaton of groups. This includes packages that assume the cluster membership is a latent variable or simple an aggregation of units contingent on a starting point. As well as packages that deal with static networks, dynamic (or temporal) ones, multi-level, linked, or multipartite.

### Generalised blockmodeling (structural and/or regular equivalence)

The label 'generalised blockmodeling' describes a very flexible approach for binary and valued networks with one or more modes that can leverage  any definition of equivalence that can be expressed by specifying a set of allowed block types (either for the whole network or for each set of ties from a certain row cluster to a specific column cluster). The block types and their specification for each type of network (e.g. binary, valued, etc.) and are described in great detail in the literature (Doreian, Batagelj, and Ferligoj [1994](https://doi.org/10.1016/0378-8733(94)90013-2); [2005](https://doi.org/10.1016/j.socnet.2004.01.002)).

There are several packages and functions for generalised blockmodeling based on generalised and/or regular equivalence:

- `r pkg("concoR", priority = "core")` implements the classical CONCOR (CONvergence of iterated CORrelation) algorithm (Breiger, Boorman, and Arabie [1975](https://doi.org/10.1016%2F0022-2496%2875%2990028-0)) for one- and multi-mode un/directed networks.

- `r pkg("blockmodeling", priority = "core")`: this package offers and implementation of generalised blockmodeling (`blockmodeling::optRandomParC`) as well as functions for computation of (dis)similarities in terms of structural or regular equivalence and plotting. Furthermore, it include implementations of the REGE (also implemented in Ucinet) algorithm (`blockmodeling::REGE`) for regular equivalence ()

- `r pkg("BlockmodelingGUI")` a Shiny app providing a graphical interface for generalised blockmodeling of single-relation, one-mode networks. It includes several ways to visualise networks and partitions.

- `r pkg("kmBlock")` implements a k-means like approach to the blockmodeling of one-mode and linked networks as presented in Žiberna ([2020](https://doi.org/10.1016/j.socnet.2019.10.006)) based on structural equivalence.

- `r pkg("signnet")` offers to functions implementing the generalised blockmodeling with structural equivalence (`signnet::signed_blockmodel`) and generalised equivalence (`signnet::signed_blockmodel_general`) of signed networks based on `graph` objects from the R package [`igraph`](https://cran.r-project.org/package=igraph) 

### Stochastic blockmodeling (SBM)

Unlike generalised BM, SBM looks for stochastic equivalence in the pattern of ties between units: 

- `r pkg("blockmodels")` allows to run the SBM or the Latent Block Model (LBM) of static networks using  a Variational Expectation Maximisation algorithm. Various `S4` functions implement three probability distributions: `BM_bernoulli` for binary data, `BM_poisson` for discrete/count weights, `BM_gaussian` for continuous weights. It allows for SBMs and LBM with or without node covariates and supports multiplex binary networks via `BM_bernoulli_multiplex`.
- `r pkg("sbm")` is an extension of `blockmodels` bi- and multi-partite as well as multiplex networks as proposed by Barbillon et al ([2017](https://www.doi.org/10.1111/rssa.12193)) through dedicated `R6` clasess. It includes functions to plot the resulting partition.
- `r pkg("dynsbm", priority = "core")` implements the model for temporal networks presented in Matias and Miele ([2020](https://doi.org/10.1111/rssb.12200)) which combines a static SBM with independent Markov chains for the dynamic part. It supports binary and weighted networks with both discrete or continuous edges. Includes also functions for plotting (`adjacency.plot`, `alluvial.plot`, `connectivity.plot`) the partition and automatically constructs matrices as an array of the right format.
- `r pkg("MLVSBM")` Implements the SBM of multilevel networks where the different matrices each represent an interaction layer either weighter or binary. It generalises the approach proposed by Chabert-Liddell et al. ([2021](https://doi.org/10.1016/j.csda.2021.107179)) to more than two layers.
- `r pkg("StochBlock", priority = "core")` implements the stochastic blockmodeling of one-mode and linked networks as implemented in Škulj and Žiberna ([2022](https://doi.org/10.1016/j.socnet.2022.12.003)). It include utilities to plot the results, but cannot choose automatically the 'right' number of clusters and tends to be very slow according to subsequent reviews (see Cugmas and Žiberna [2023](https://doi.org/10.1016/j.socnet.2022.12.003));
-  `r pkg("GREMLINS", priority = "core")` implements the SBM of generalised multipartite networks where the different matrices each involve nodes that can be partitioned into  a-priori defined _functional groups_ as
proposed by Bar-Hen, Barbillon, and  Donnet ([2018](https://doi.org/10.1177/1471082X20963254)) to more than two layers.

### Links

* Barbillon, Pierre, Sophie Donnet, Emmanuel Lazega, and Avner Bar-Hen. 2017. ‘Stochastic Block Models for Multiplex Networks: An Application to a Multilevel Network of Researchers’. Journal of the Royal Statistical Society Series A: Statistics in Society 180 (1): 295–314. https://doi.org/10.1111/rssa.12193.

* Bar-Hen, Avner, Pierre Barbillon, and Sophie Donnet. 2022. ‘Block Models for Generalized Multipartite Networks: Applications in Ecology and Ethnobiology’. Statistical Modelling 22 (4): 273–96. https://doi.org/10.1177/1471082X20963254.

* Breiger, Ronald L, Scott A Boorman, and Phipps Arabie. 1975. ‘An Algorithm for Clustering Relational Data with Applications to Social Network Analysis and Comparison with Multidimensional Scaling’. Journal of Mathematical Psychology 12 (3): 328–83. https://doi.org/10.1016/0022-2496(75)90028-0.

* Chabert-Liddell, Saint-Clair, Pierre Barbillon, Sophie Donnet, and Emmanuel Lazega. 2021. ‘A Stochastic Block Model Approach for the Analysis of Multilevel Networks: An Application to the Sociology of Organizations’. Computational Statistics & Data Analysis 158 (June): 107179. https://doi.org/10.1016/j.csda.2021.107179.

* Cugmas, Marjan, and Aleš Žiberna. 2023. ‘Approaches to Blockmodeling Dynamic Networks: A Monte Carlo Simulation Study’. Social Networks 73 (May): 7–19. https://doi.org/10.1016/j.socnet.2022.12.003.

* Doreian, Patrick, Vladimir Batagelj, and Anuška Ferligoj. 1994. ‘Partitioning Networks Based on Generalized Concepts of Equivalence’. The Journal of Mathematical Sociology 19 (1): 1–27. https://doi.org/10.1080/0022250X.1994.9990133.

* ———. 2005. Generalized Blockmodeling. Cambridge University Press.

* Matias, Catherine, and Vincent Miele. 2017. ‘Statistical Clustering of Temporal Networks through a Dynamic Stochastic Block Model’. Journal of the Royal Statistical Society. Series B (Statistical Methodology) 79 (4): 1119–41. https://www.jstor.org/stable/26773154.

* Škulj, Damjan, and Aleš Žiberna. 2022. ‘Stochastic Blockmodeling of Linked Networks’. Social Networks 70 (July): 240–52. https://doi.org/10.1016/j.socnet.2022.02.001.

* Žiberna, Aleš. 2020. ‘K-Means-Based Algorithm for Blockmodeling Linked Networks’. Social Networks 61 (May): 153–69. https://doi.org/10.1016/j.socnet.2019.10.006.
