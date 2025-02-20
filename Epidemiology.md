---
name: Epidemiology
topic: Epidemiology
maintainer: Thibaut Jombart, Matthieu Rolland, Hugo Gruson
email: thibautjombart@gmail.com
version: 2022-10-03
source: https://github.com/cran-task-views/Epidemiology/
---

Contributors (in alphabetic order): Neale Batra, Solène Cadiou, Christopher
Endres, Rich FitzJohn, Hugo Gruson, Andreas Handel, Michael Höhle, Thibaut
Jombart, Joseph Larmarange, Sebastian Lequime, Alex Spina, Tim Taylor, Sean Wu,
Achim Zeileis.

## Overview

R is increasingly becoming a standard in epidemiology, providing a wide array of
tools from study design to epidemiological data exploration, modeling,
forecasting, and simulation. This task view provides an overview of packages
specifically developed for epidemiology, including infectious disease
epidemiology (IDE) and environmental epidemiology. It does not include:

- generic tools which are used in these domains but not specifically developed
  for the epidemiological context,
- '*omics*' approaches and genome-wide association studies (GWAS), which can be
  used in epidemiology but form a largely separate domain.

Packages are grouped in the following categories:

1.  **Data visualization:** tools dedicated to handling and
    visualization of epidemiological data, *e.g.* epidemic curves ('*epicurves*'),
    exploration of contact tracing networks, etc.
2.  **Infectious disease modeling:** IDE-specific packages for the analysis of
    epidemic curves (including outbreak detection / surveillance), estimation of
    transmissibility, short-term forecasting, compartmental models (*e.g.*  SIR
    models), simulation of outbreaks, and reconstruction of transmission trees
3.  **Environmental epidemiology:** tools dedicated to the study of
    environmental factors acting as determinants of diseases
3.  **Helpers:** tools implementing miscellaneous tasks useful for practicing as
    well as teaching epidemiology, such as sample size calculation, fitting
    discretized Gamma distributions, or handling linelist data.
4.  **Data packages:** these packages provide access to both empirical and
    simulated epidemic data; includes a specific section on COVID-19.

Additional links to non specific but highly useful packages (to create tables,
manipulate dates, etc.) are provided in the task view's footnotes.

## Inclusion criteria

Packages included in this task view were identified through recommendations of
expert epidemiologists as well as an automated CRAN search using
`pkgsearch::pkg_search()` with the keywords: *epidemiology*, *epidemic*, *epi*,
*outbreak*, and *transmission*. The list was manually curated for the final
selection to satisfy the conditions described in the previous paragraph.

Packages are deemed in scope if they provide tools, or data, explicitly targeted
at reporting, modeling, or forecasting infectious diseases.

**Your input is welcome!** Please suggest packages we may have missed by 
filing an issue in the GitHub repository or by contacting the maintainer.


## Data visualization

This section includes packages providing specific tools for the visualization
and exploration of epidemiological data.

-   `r pkg("epicontacts", priority = "core")`: Implements a dedicated class for
    contact data, composed of case line lists and contacts between cases. Also
    includes procedures for data handling, interactive graphics, and
    characterizing contact patterns (*e.g.* mixing patterns, serial
    intervals). [RECON](https://www.repidemicsconsortium.org/) package.
-   `r pkg("EpiContactTrace")`: Routines for epidemiological contact tracing and
    visualization of networks of contacts.
-   `r pkg("EpiCurve")`: Creates simple or stacked epidemic curves for hourly,
    daily, weekly or monthly outcome data.
-   `r pkg("epiDisplay")`: Package for data exploration and result presentation.
-   `r pkg("epiflows")`: Provides functions and classes designed to handle and
    visualize epidemiological flows of people between locations. Also contains a
    statistical method for predicting disease spread from flow data initially
    described in [Dorigatti et al.
    (2017)](https://doi.org/10.2807%2F1560-7917.ES.2017.22.28.30572). [RECON](https://www.repidemicsconsortium.org/)
    package.
-   `r pkg("EpiReport")`: Drafting an epidemiological report in 'Microsoft Word'
    format for a given disease, similar to the Annual Epidemiological Reports
    published by the European Centre for Disease Prevention and Control.
-   `r pkg("incidence")`: Functions and classes to compute, handle and visualize
    incidence from dated events for a defined time interval, using various date
    formats. Also provides wrappers for log-linear models of incidence and
    estimation of daily growth
    rate. [RECON](https://www.repidemicsconsortium.org/) package. This package
    is scheduled for deprecation and is replaced by `r pkg("incidence2")`.
-   `r pkg("incidence2", priority = "core")`: Provides functions and classes to
    compute, handle and visualize incidence from dated events. Improves the
    original `r pkg("incidence")` package in many ways: full flexibility in time
    intervals used, allows multiple stratifications, and is fully compatible
    with `r pkg("dplyr")` and other tidyverse tools.
    [RECON](https://www.repidemicsconsortium.org/) package.
-   `r pkg("i2extras")`: Provides functions to work with 'incidence2' objects,
    including a simplified interface for trend fitting, estimation of growth
    rates, and peak estimation. [RECON](https://www.repidemicsconsortium.org/)
    package.
	
	
## Infectious disease modeling

This section includes packages for specifically dedicated to IDE modeling. Note
that R offers a wealth of options for general-purpose time series modeling,
many of which are listed in the `r view("TimeSeries")` and `r view("Survival")`
task views.

### Epidemics surveillance

Packages below implement surveillance algorithms, but these approaches can be
usefully complemented by spatial analyses. We recommend looking at the `r view("Spatial")`
task view, which has a dedicated section on
`r view("Spatial", "disease mapping and areal data analysis")`.

-   `r pkg("argo")`: Augmented Regression with General Online data (ARGO) for
    accurate estimation of influenza epidemics in United States on both national
    level and regional level. It replicates the method introduced in paper
    [Yang, S., Santillana, M. and Kou, S.C.
    (2015)](https://doi.org/10.1073/pnas.1515373112) and [Ning, S., Yang, S. and
    Kou, S.C. (2019)](https://doi.org/10.1038/s41598-019-41559-6).
-   `r pkg("Epi", priority = "core")`: Functions for demographic and
    epidemiological analysis in the Lexis diagram, i.e. register and cohort
    follow-up data, in particular representation, manipulation and simulation of
    multistate data - the Lexis suite of functions, which includes interfaces to
    `r pkg("mstate")`, `r pkg("etm")` and `r pkg("cmprsk")` packages. Also
    contains functions for Age-Period-Cohort and Lee-Carter modeling, interval
    censored data, tabulation, plotting, as well as a number of epidemiological
    data sets.
-   `r pkg("episensr")`: Basic sensitivity analysis of the observed relative
    risks adjusting for unmeasured confounding and misclassification of the
    exposure/outcome, or both. It follows the bias analysis methods and examples
    from the book by Lash T.L., Fox M.P., and Fink A.K. "Applying Quantitative
    Bias Analysis to Epidemiologic Data", ('Springer', 2009).
-   `r pkg("mem")`: The Moving Epidemic Method, created by T Vega and JE Lozano
    ([2012](https://doi.org/10.1111/j.1750-2659.2012.00422.x),
    [2015](https://doi.org/10.1111/irv.12330)), allows the weekly assessment of
    the epidemic and intensity status to help in routine respiratory infections
    surveillance in health systems. Allows the comparison of different epidemic
    indicators, timing and shape with past epidemics and across different
    regions or countries with different surveillance systems. Also, it gives a
    measure of the performance of the method in terms of sensitivity and
    specificity of the alert week.
-   `r pkg("memapp")`: The Moving Epidemic Method, created by T Vega and JE
    Lozano ([2012](https://doi.org/10.1111/j.1750-2659.2012.00422.x),
    [2015](https://doi.org/10.1111/irv.12330)), allows the weekly assessment of
    the epidemic and intensity status to help in routine respiratory infections
    surveillance in health systems. Enables the comparison of different epidemic
    indicators, timing and shape with past epidemics and across different
    regions or countries with different surveillance systems. It also gives a
    measure of the performance of the method in terms of sensitivity and
    specificity of the alert week. 'memapp' is a web application created in the
    Shiny framework for the `r pkg("mem")` R package.
-   `r pkg("nosoi")`: The aim of `r pkg("nosoi")` (pronounced no.si) is to
    provide a flexible agent-based stochastic transmission chain/epidemic
    simulator ([Lequime et al. 2020](https://doi.org/2020.03.03.973107)). The
    package can take into account the influence of multiple variables on the
    transmission process (e.g.  dual-host systems such as arboviruses,
    within-host viral dynamics, transportation, population structure), alone or
    taken together, to create complex but relatively intuitive epidemiological
    simulations.
-   `r pkg("riskCommunicator")`: Estimates flexible epidemiological effect
    measures including both differences and ratios using the parametric
    G-formula developed as an alternative to inverse probability weighting. It
    is useful for estimating the impact of interventions in the presence of
    treatment-confounder-feedback. G-computation was originally described by
    [Robbins (1986)](https://doi.org/10.1016/0270-0255(86)90088-6) and has been
    described in detail by [Ahern, Hubbard, and Galea
    (2009)](https://doi.org/10.1093/aje/kwp015); [Snowden, Rose, and Mortimer
    (2011)](https://doi.org/10.1093/aje/kwq472); and [Westreich et al.
    (2012)](https://doi.org/10.1002/sim.5316).
-   `r pkg("RSurveillance")`: Provides a diverse set of functions useful for the
    design and analysis of disease surveillance activities.
-   `r pkg("trendeval")`: Provides a coherent interface for evaluating models
    fit with the trending
    package. [RECON](https://www.repidemicsconsortium.org/) package.
-   `r pkg("SpatialEpi")`: Methods and data for cluster detection and disease
    mapping.
-   `r pkg("surveillance", priority = "core")`: Statistical methods for the
    modeling and monitoring of time series of counts, proportions and
    categorical data, as well as for the flexible covariate based regression
    modeling of spatio-temporal point processes of epidemic phenomena. The
    monitoring methods focus on aberration detection in count data time series
    from public health surveillance of communicable diseases. A recent overview
    of the available monitoring procedures is given by [Salmon et al.
    (2016)](https://doi.org/10.18637%2Fjss.v070.i10) and a recent overview of
    the implemented space-time modeling frameworks for epidemic phenomena is
    given by [Meyer et al. (2017)](https://doi.org/10.18637%2Fjss.v077.i11).
    Also contains back-projection methods to infer time series of exposure from
    disease onset and correction of observed time series for reporting delays
    (nowcasting).
-   `r github("reconhub/trendbreaker")` implements tools for detecting changes
    in temporal trends of a single response variable. It implements the
    **A**utomatic **S**election of **M**odels and **O**utlier **De**tection for
    **E**pidemmics (ASMODEE), an algorithm originally designed for detecting
    changes in COVID-19 case
    incidence. [RECON](https://www.repidemicsconsortium.org/) package.
-   `r pkg("trending")`: Provides a coherent interface to multiple modeling
    tools for fitting trends along with a standardized approach for generating
    confidence and prediction
    intervals. [RECON](https://www.repidemicsconsortium.org/) package.

### Estimation of transmissibility

-   `r pkg("earlyR")`: Implements a simple, likelihood-based estimation of the
    reproduction number (R0) using a Poisson branching process. This model
    requires knowledge of the serial interval distribution, and dates of symptom
    onsets. It is a simplified version of the model introduced by [Cori et
    al. (2013)](https://doi.org/10.1093%2Faje%2Fkwt133).
-   `r pkg("endtoend")`: Computes the expectation of the number of transmissions
    and receptions considering an End-to-End transport model with limited number
    of retransmissions per packet. It provides theoretical results and also
    estimated values based on Monte Carlo simulations. It is also possible to
    consider random data and ACK probabilities.
-   `r pkg("EpiEstim", priority = "core")`: Provides tools for estimating
    time-varying transmissibility using the instantaneous reproduction number
    (Rt) introduced in [Cori et al. (2013)](https://doi.org/10.1093/aje/kwt133).
-   `r pkg("epimdr")`: Functions, data sets and shiny apps for "Epidemics:
    Models and Data in R" by Ottar N. Bjornstad ([ISBN
    978-3-319-97487-3](https://www.springer.com/gp/book/9783319974866)). The
    package contains functions to study the S(E)IR model, spatial and
    age-structured SIR models; time-series SIR and chain-binomial stochastic
    models; catalytic disease models; coupled map lattice models of spatial
    transmission and network models for social spread of infection. The package
    is also an advanced quantitative companion to the [coursera Epidemics
    Massive Online Open Course](https://www.coursera.org/learn/epidemics).
-   `r pkg("epinet")`: A collection of epidemic/network-related tools. Simulates
    transmission of diseases through contact networks. Performs Bayesian
    inference on network and epidemic parameters, given epidemic data.
-   `r github("epiforecasts/EpiNow2")`: Provides tools for estimating the
    time-varying reproduction number, rate of spread, and doubling time of
    epidemics while accounting for various delays using the approach introducted
    in [Abbott et al. (2020)](https://doi.org/10.12688/wellcomeopenres.16006.1),
    and [Gostic et al. (2020)](https://doi.org/10.1371/journal.pcbi.1008409).
-   `r pkg("nbTransmission")`: Estimates the relative transmission probabilities
    between cases using naive Bayes as introduced in [Leavitt et
    al. (2020)](https://doi.org/10.1093%2Fije%2Fdyaa031). Includes various
    functions to estimate transmission parameters such as the generation/serial
    interval and reproductive number as well as finding the contribution of
    covariates to transmission probabilities and visualizing results.
-   `r pkg("R0", priority = "core")`: Estimation of reproduction numbers for
    disease outbreak, based on incidence data including the basic reproduction
    number (R0) and the instantaneous reproduction number (R(t)), alongside
    corresponding 95% Confidence Interval. Also includes routines for plotting
    outputs and for performing sensitivity analyses.
-   `r pkg("tsiR")`: The TSIR modeling framework allows users to fit the time
    series SIR model to cumulative case data, which uses a regression equation
    to estimate transmission parameters based on differences in cumulative cases
    between reporting periods. The package supports inference on TSIR parameters
    using GLMs and profile likelihood techniques, as well as forward simulation
    based on a fitted model, as described in [Becker and Grenfell
    (2017)](https://doi.org/10.1371/journal.pone.0185528).

### Compartmental models

-   `r pkg("EpiILM")`: Provides tools for simulating from discrete-time
    individual level models for infectious disease data analysis. This epidemic
    model class contains spatial and contact-network based models with two
    disease types: Susceptible-Infectious (SI) and
    Susceptible-Infectious-Removed (SIR).
-   `r pkg("EpiILMCT")`: Provides tools for simulating from continuous-time
    individual level models of disease transmission, and carrying out infectious
    disease data analyses with the same models. The epidemic models considered
    are distance-based and/or contact network-based models within
    Susceptible-Infectious-Removed (SIR) or
    Susceptible-Infectious-Notified-Removed (SINR) compartmental frameworks. An
    overview of the implemented continuous-time individual level models for
    epidemics is given by [Almutiry and Deardon
    (2019)](https://doi.org/10.1515/ijb-2017-0092).
-   `r pkg("EpiModel", priority = "core")`: Tools for simulating mathematical
    models of infectious disease dynamics. Epidemic model classes include
    deterministic compartmental models, stochastic individual-contact models,
    and stochastic network models.  Network models use the robust statistical
    methods of exponential-family random graph models (ERGMs) from the Statnet
    suite of software packages in R. Standard templates for epidemic modeling
    include SI, SIR, and SIS disease types. EpiModel features an API for
    extending these templates to address novel scientific research aims. Full
    methods for EpiModel are detailed in [Jenness et
    al. (2018)](https://doi.org/10.18637/jss.v084.i08).
-   `r pkg("odin")`: Provides a generic, fast and computer-efficient platform
    for implementing any deterministic or stochastic compartmental models
    (e.g. SIR, SEIR, SIRS, ...), and can include age stratification or
    spatialization. It uses a domain specific language (DSL) to specify systems
    of ordinary differential equations (ODE) and integrate them. The DSL uses
    R's syntax, but compiles to C in order to efficiently solve the system,
    using interfaces to the packages `r pkg("deSolve")` and `r pkg("dde")`.
-   `r pkg("pomp")` Provides a large set of forward simulation algorithms and
    MLE or Bayesian inference techniques to work with state-space models. Models
    may be specified as either deterministic or stochastic and typically follow
    a compartmental model structure. Time may be either discrete or continuous,
    depending on the simulation algorithm chosen. Additionally models may be
    programmed in C and compiled on-the-fly into a format suitable for use in
    the package to speed up simulation and inference. The R package and some of
    its algorithms are described in [King, Nguyen, and Ionides
    (2016)](https://doi.org/10.18637/jss.v069.i12).
-   `r pkg("popEpi")`: Enables computation of epidemiological statistics,
    including those where counts or mortality rates of the reference population
    are used. Currently supported: excess hazard models, rates, mean survival
    times, relative survival, and standardized incidence and mortality ratios
    (SIRs/SMRs), all of which can be easily adjusted for by covariates such as
    age. Fast splitting and aggregation of 'Lexis' objects (from package `r
    pkg("Epi", priority = "core")` and other computations achieved using `r
    pkg("data.table")`.
-   `r pkg("SimInf")`: Provides an efficient and very flexible framework to
    conduct data-driven epidemiological modeling in realistic large scale
    disease spread simulations. The framework integrates infection dynamics in
    subpopulations as continuous-time Markov chains using the Gillespie
    stochastic simulation algorithm and incorporates available data such as
    births, deaths and movements as scheduled events at predefined time-points.
    Using C code for the numerical solvers and 'OpenMP' (if available) to divide
    work over multiple processors ensures high performance when simulating a
    sample outcome. The package contains template models and can be extended
    with user-defined models. For more details see the paper by [Widgren, Bauer,
    Eriksson and Engblom (2019)](https://doi.org/10.18637%2Fjss.v091.i12).
-   `r pkg("socialmixr")`: Provides methods for sampling contact matrices from
    diary data for use in infectious disease modeling, as discussed in [Mossong
    et al. (2008)](https://doi.org/10.1371%2Fjournal.pmed.0050074).

### Transmission tree reconstruction

-   `r pkg("adegenet")`: primarily a population genetics package,
    `r pkg("adegenet")` implements seqtrack ([Jombart et al.
    2011](https://doi.org/10.1038%2Fhdy.2010.78)), a maximum-parsimony approach
    for reconstructing transmission trees using the Edmonds/Chu-Liu algorithm
-   `r pkg("o2geosocial")` (`r pkg("outbreaker2")` module): Bayesian
    reconstruction of who infected whom during past outbreaks using
    routinely-collected surveillance data. Inference of transmission trees using
    genotype, age specific social contacts, distance between cases and onset
    dates of the reported cases ([Robert A, Kucharski AJ, Gastanaduy PA, Paul P,
    Funk S. 2020](https://doi.org/10.1098%2Frsif.2020.0084)).
-   `r github("xavierdidelot/o2mod.transphylo")` is a module of
    `r pkg("outbreaker2")` which uses the `r pkg("TransPhylo")` model of
    within-host evolution.
-   `r pkg("outbreaker2", priority = "core")`: a modular platform for Bayesian
    reconstruction of disease outbreaks using epidemiological and genetic
    information as introduced in [Jombart T, Cori A, Didelot X, Cauchemez S,
    Fraser C and Ferguson N.
    2014](https://doi.org/10.1371/journal.pcbi.1003457), [Campbell F, Cori A,
    Ferguson N, Jombart
-   `r pkg("TransPhylo")`: Inference of transmission tree from a dated
    phylogeny. Includes methods to simulate and analyze outbreaks. The
    methodology is described in [Didelot et al.
    (2014)](https://doi.org/10.1093%2Fmolbev%2Fmsu121), [Didelot et al.
    (2017)](https://doi.org/10.1093%2Fmolbev%2Fmsw275).



## Environmental epidemiology

Environmental epidemiology is dedicated to the study of physical, chemical, and
biologic agents in the environment acting as determinants of disease. The aims
of environmental epidemiology are to infer causality, to identify environmental
causes of disease, such as from air and water pollutants, dietary contaminants,
built environments, and others.

R packages dedicated to environmental epidemiology include tools dealing with
limits of detection of pollutants (left-censoring issues), and various modeling
approaches to account for multiple correlations between exposures and infer
causality.

-   `r pkg("NADA", priority = "core")`: Nondetects and Data Analysis for
    Environmental Data, package containing all the functions derived from the
    methods in [Helsel
    (2011)](https://www.wiley.com/en-us/Statistics+for+Censored+Environmental+Data+Using+Minitab+and+R%2C+2nd+Edition-p-9780470479889).
-   `r pkg("EnvStats", priority = "core")`: Package for Environmental
    Statistics, Including US EPA Guidance, graphical and statistical analyses of
    environmental data, with focus on analyzing chemical concentrations and
    physical parameters, usually in the context of mandated environmental
    monitoring. Major environmental statistical methods found in the literature
    and regulatory guidance documents, with extensive help that explains what
    these methods do, how to use them, and where to find them in the
    literature. Numerous built-in data sets from regulatory guidance documents
    and environmental statistics literature [(Millard
    2013)](https://link.springer.com/book/10.1007/978-1-4614-8456-1).
-   `r pkg("bkmr")`: Implements Bayesian Kernel Machine Regression, a
	statistical approach for estimating the joint health effects of multiple
	concurrent exposures, as described in Bobb *et al.*
	[(2015)](https://academic.oup.com/biostatistics/article/16/3/493/269719)
-   `r pkg("mediation", priority = "core")`: Implements parametric and non
    parametric mediation analysis as discussed in Imai *et al.*
    [(2010)](http://dx.doi.org/10.1214/10-sts321).
-   `r pkg("mma")`: Implements multiple mediation analysis as described in Yu
	*et al.*  [(2017)](https://doi.org/10.1016%2Fj.sste.2017.02.001).
-   `r pkg("HIMA")`: Allows to estimate and test high-dimensional mediation
    effects based on advanced mediator screening and penalized regression
    techniques ([Zhang *et al.*
    2021])(https://doi.org/10.1093%2Fbioinformatics%2Fbtab564).





## Helpers

This section includes packages providing tools to facilitate epidemiological
analysis as well as for training (e.g. computing sample size, contingency
tables, etc).

-   `r pkg("DSAIDE")`: Exploration of simulation models (apps) of various
    infectious disease transmission dynamics scenarios. The purpose of the
    package is to help individuals learn about infectious disease epidemiology
    from a dynamical systems perspective. All apps include explanations of the
    underlying models and instructions on what to do with the models.
-   `r pkg("epibasix")`: Contains elementary tools for analyzing common
    epidemiological problems, ranging from sample size estimation, through 2x2
    contingency table analysis and basic measures of agreement (kappa,
    sensitivity/specificity). Appropriate print and summary statements are also
    written to facilitate interpretation wherever possible. The target audience
    includes advanced undergraduate and graduate students in epidemiology or
    biostatistics courses, and clinical researchers.
-   `r pkg("epiR", priority = "core")`: Tools for the analysis of
    epidemiological and surveillance data. Contains functions for directly and
    indirectly adjusting measures of disease frequency, quantifying measures of
    association on the basis of single or multiple strata of count data
    presented in a contingency table, computation of confidence intervals around
    incidence risk and incidence rate estimates and sample size calculations for
    cross-sectional, case-control and cohort studies. Surveillance tools include
    functions to calculate an appropriate sample size for 1- and 2-stage
    representative freedom surveys, functions to estimate surveillance system
    sensitivity and functions to support scenario tree modeling analyses.
-   `r pkg("epitools", priority = "core")`: Tools for training and practicing
    epidemiologists including methods for two-way and multi-way contingency
    tables.
-   `r pkg("epitrix")`: A collection of small functions useful for epidemics
    analysis and infectious disease modeling. This includes computation of
    basic reproduction numbers (R0) from daily growth rates, generation of
    hashed labels to anonymize data, and fitting discretized Gamma
    distributions.
-   `r pkg("linelist")`: Implements the `linelist` class for storing case line
    list data, which extends `data.frame` and `tibble` by adding the ability to
    tag key epidemiological variables, validate them, and providing safeguards
    against accidental deletion or alteration of these data to help make data
    pipelines more straightforward and robust.
-   `r pkg("powerSurvEpi")`: Functions to calculate power and sample size for
    testing main effect or interaction effect in the survival analysis of
    epidemiological studies (non-randomized studies), taking into account the
    correlation between the covariate of the interest and other covariates. Some
    calculations also take into account the competing risks and stratified
    analysis. This package also includes a set of functions to calculate power
    and sample size for testing main effects in the survival analysis of
    randomized clinical trials.
-   `r pkg("AMR")`: Functions to simplify and standardise antimicrobial 
    resistance (AMR) data analysis and to work with microbial and antimicrobial
    properties by using evidence-based methods and reliable reference data such 
    as LPSN ([Parte *et al.* 2020](https://doi.org/10.1099/ijsem.0.004332)).

## Data

Here are packages providing different epidemiologic datasets, either simulated
or real, useful for research purposes or field applications with a specific
COVID-19 section.

### Epidemic outbreak data

-   `r pkg("contactdata")`: Data package for the supplementary data in [Prem et
    al. (2017)](https://doi.org/10.1371%2Fjournal.pcbi.1005697). Provides easy
    access to contact data for 152 countries, for use in epidemiological,
    demographic or social sciences research.
-   `r pkg("outbreaks", priority = "core")`: Empirical or simulated disease
    outbreak data, provided either as RData or as text files.

### COVID-19

-   `r pkg("bets.covid19")`: Implements likelihood inference for early epidemic
    analysis. BETS is short for the four key epidemiological events being
    modeled: Begin of exposure, End of exposure, time of Transmission, and time
    of Symptom onset. The package contains a dataset of the trajectory of
    confirmed cases during the coronavirus disease (COVID-19) early outbreak.
    More detail of the statistical methods can be found in [Zhao et al.
    (2020)](https://arxiv.org/abs/2004.07743).
-   `r pkg("corona")`: Manipulate and view coronavirus data and other societally
    relevant data at a basic level.
-   `r pkg("coronavirus")`: Provides a daily summary of the Coronavirus
    (COVID-19) cases by state/province. Data source: [Johns Hopkins University
    Center for Systems Science and Engineering (JHU CCSE)
    Coronavirus](https://systems.jhu.edu/research/public-health/ncov/).
-   `r pkg("COVID19")`: Download COVID-19 data across governmental sources at
    national, regional, and city level, as described in [Guidotti and Ardia
    (2020)](https://doi.org/10.21105/joss.02376). Includes the time series of
    vaccines, tests, cases, deaths, recovered, hospitalizations, intensive
    therapy, and policy measures by '[Oxford COVID-19 Government Response
    Tracker](https://www.bsg.ox.ac.uk/research/research-projects/coronavirus-government-response-tracker).
    Provides a seamless integration with '[World Bank Open
    Data](https://data.worldbank.org/)', '[Google Mobility
    Reports](https://www.google.com/covid19/mobility/)', 'Apple Mobility
    Reports](<https://covid19.apple.com/mobility>)'.
-   `r pkg("covid19.analytics")`: Load and analyze updated time series worldwide
    data of reported cases for the Novel CoronaVirus Disease (CoViD-19) from the
    [Johns Hopkins University Center for Systems Science and Engineering (JHU
    CSSE) data repository](https://github.com/CSSEGISandData/COVID-19). The
    datasets are available in two main modalities, as a time series sequences
    and aggregated for the last day with greater spatial resolution. Several
    analysis, visualization and modeling functions are available in the package
    that will allow the user to compute and visualize total number of cases,
    total number of changes and growth rate globally or for an specific
    geographical location, while at the same time generating models using these
    trends; generate interactive visualizations and generate
    Susceptible-Infected-Recovered (SIR) model for the disease spread.
-   `r pkg("covid19br")`: Set of functions to import COVID-19 pandemic data
    into R. The Brazilian COVID-19 data, obtained from the official Brazilian
    repository at <https://covid.saude.gov.br/>, is available at country,
    region, state, and city-levels. The package also downloads the world-level
    COVID-19 data from the John Hopkins University's repository.
-   `r pkg("covid19dbcand")`: Provides different datasets parsed from
    '[Drugbank](https://www.drugbank.ca/covid-19)' database using
    `r pkg("dbparser")` package. It is a smaller version from
    `r github("interstellar-Consultation-Services/dbdataset")` package. It
    contains only information about COVID-19 possible treatment.
-   `r pkg("covid19italy")`: Provides a daily summary of the Coronavirus
    (COVID-19) cases in Italy by country, region and province level. Data
    source: [Presidenza del Consiglio dei Ministri - Dipartimento della
    Protezione Civile](http://www.protezionecivile.it/).
-   `r pkg("covid19france")`: Imports and cleans
    <https://github.com/opencovid19-fr/data> data on COVID-19 in France.
-   `r github("nevrome/covid19germany")`: An R package to load, visualize and
    analyze daily updated data on the COVID-19 outbreak in Germany.
-   `r github("covid19R/covid19mobility")`: Scrapes trends in mobility after the
    Covid-19 outbreak from different sources. Currently, the package scrapes
    data from Google (<https://www.google.com/covid19/mobility/>), Apple
    (<https://www.apple.com/covid19/mobility>), and will add others. The data
    returned uses the tidy [Covid19R project data
    standard](https://covid19r.github.io/documentation/) as well as the
    controlled vocabularies for measurement types.
-   `r github("covid19R/covid19nytimes")`: Accesses the NY Times Covid-19
    county-level data for the US, described in
    <https://www.nytimes.com/article/coronavirus-county-data-us.html> and
    available at <https://github.com/nytimes/covid-19-data>. It then returns the
    data in a tidy data format according to the Covid19R Project data
    specification. If you plan to use the data or publicly display the data or
    results, please make sure cite the original NY Times source. Please read and
    follow the terms laid out in the data license at
    <https://github.com/nytimes/covid-19-data/blob/master/LICENSE>.
-   `r pkg("covid19sf")`: Provides a verity of summary tables of the Covid19
    cases in San Francisco. Data source: [San Francisco, Department of Public
    Health - Population Health Division](https://datasf.org/opendata/).
-   `r pkg("covid19swiss")`: Provides a daily summary of the Coronavirus
    (COVID-19) cases in Switzerland cantons and Principality of Liechtenstein.
    Data source: Specialist Unit for Open Government Data Canton of Zurich
    <https://www.zh.ch/de/politik-staat/opendata.html>.
-   `r pkg("covid19us")`: A wrapper around the 'COVID Tracking Project API'
    <https://covidtracking.com/api/> providing data on cases of COVID-19 in the
    US.
-   `r pkg("CovidMutations")`: A feasible framework for mutation analysis and
    reverse transcription polymerase chain reaction (RT-PCR) assay evaluation of
    COVID-19, including mutation profile visualization, statistics and mutation
    ratio of each assay. The mutation ratio is conducive to evaluating the
    coverage of RT-PCR assays in large-sized samples. [Mercatelli, D. and
    Giorgi, F. M. (2020)](https://doi.org/10.20944/preprints202004.0529.v1).
-   `r pkg("CovidMutations")`: A feasible framework for mutation analysis and
    reverse transcription polymerase chain reaction (RT-PCR) assay evaluation of
    COVID-19, including mutation profile visualization, statistics and mutation
    ratio of each assay. The mutation ratio is conducive to evaluating the
    coverage of RT-PCR assays in large-sized samples. [Mercatelli, D. and
    Giorgi, F. M. (2020)](https://doi.org/10.20944/preprints202004.0529.v1).
-   `r github("epiforecasts/covidregionaldata")`: An interface to subnational and national level 
    COVID-19 data sourced from both official sources, such as Public Health
    England in the UK, and from other COVID-19 data collections, including 
    the World Health Organisation (WHO), European Centre for Disease Prevention and
    Control (ECDC), John Hopkins University (JHU), Google Open Data and others. 
    This package is designed to streamline COVID-19 data extraction, cleaning,
    and processing from a range of data sources in an open and transparent way. 
    For all countries supported, data includes a daily time-series of cases and, 
    wherever available, data on deaths, hospitalisations, and tests. 
-   `r github("como-ph/oxcovid19")`: The [OxCOVID19
    Project](https://covid19.eng.ox.ac.uk) aims to increase our understanding of
    the COVID-19 pandemic and elaborate possible strategies to reduce the impact
    on the society through the combined power of statistical, mathematical
    modeling, and machine learning techniques. The OxCOVID19 Database is a
    large, single-centre, multimodal relational database consisting of
    information (using acknowledged sources) related to COVID-19 pandemic. This
    package provides an R-specific interface to the OxCOVID19 Database based on
    widely-used data handling and manipulation approaches in R.

### Other data packages

-   `r pkg("nhanesA")`: provides ready access to the National Health and
    Nutrition Examination Survey (NHANES) data tables.


### Links

-   The R Epidemics Consortium ([RECON](https://www.repidemicsconsortium.org)),
    a non-profit organization dedicated to the development of free, open-source
    outbreak analytics resources.

-   [*Epiverse*](https://data.org/initiatives/epiverse/), an initiative created
    by [data.org](https://data.org) for the development of open-source resources
    for epidemic preparedness and
    response. [*Epiverse-TRACE*](https://github.com/epiverse-trace) is dedicated
    to creating an ecosystem of R packages for outbreak analytics.

-  The R [handbook](https://epirhandbook.com/en/) for field epidemiology.
