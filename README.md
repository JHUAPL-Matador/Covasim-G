# Covasim-G

**To cite:**

>_Hamilton A, Clapp G, Colton R, Tulchinsky A, Klein E, and Lin G. Covasim-G: A method for projecting COVID-19 health burden by demographic and geographic groups. In: Proceedings of the 2024 Winter Simulation Conference. Florida: Lam H, Azar E, Batur D, Gao S, Xie W, Hunter S R, and Rossetti M D, eds.; 2024._

This repo contains a series of Jupyter notebooks for formatting GREASYPOP files for Covasim. Covasim (COVID-19 agent-based simulator) is an open-source agent-based model by the Institute for Disease Modeling for simulating COVID-19 tranmission. GREASYPOP-CO is an open-source software built by One Health Trust for generating geographically realistic synthetic populations. By using Covasim with a GREASYPOP population (Covasim-G), you can explore COVID-19 outcomes both spatially (down to the Census Block Group) and across demographic groups (age, race, gender, occupation). See the following references to learn more:

- [Covasim manuscript](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1009149)
- [Covasim user tutorials](https://docs.idmod.org/projects/covasim/en/latest/tutorials.html)
- [GREASYPOP manuscript](https://arxiv.org/abs/2406.14698)
- [GREASYPOP GitHub](https://github.com/CDDEP-DC/GREASYPOP-CO/tree/main)

#### 1. Set up environments
Before going through the Covasim-G notebooks, set up the environments below and make the GREASYPOP population.

Python 3.9-3.11 (64-bit)
- pandas 1.5.3
- numpy 1.24.3
- geopandas 0.12.2
- shapely 2.0.1
- openpyxl 3.0.10

R 4.4.1
- rjson
- here
- tidyverse
- data.table
- censusapi
- tidycensus
- devtools
- lehdr
- usmap
- geojsonio

Julia 1.9.0 (https://julialang.org/downloads/oldreleases/)
- CSV v0.10.10
- DataFrames v1.5.0
- Graphs v1.8.0
- InlineStrings v1.4.0
- JSON v0.21.4
- MatrixMarket v0.4.0
- StatsBase v0.33.21
- ProportionalFitting v0.3.0

#### 2. Make the GREASYPOP population
Download the GREASYPOP-CO repo and follow the instructions to generate a synthetic population for a US location of your choice. This tutorial will use the area of Maryland, DC, and northern Virginia as an example. Running the julia files takes a long time so you may want to connect to a cluster or run overnight.

#### 3. Go through the Covasim-G tutorials
Save the GREASYPOP files in a folder called 'data' in this repo then go through these notebooks to format GREASYPOP agents and contact layers for Covasim and run your simulations.
- `1_make_contact_matrices.ipynb`: Processes GREASYPOP data so the contact matrices are in format readable to Covasim
- `2_make_people_object.ipynb`: Creates a Covasim People object with the GREASYPOP agents and contact matrices
- `3_compare_sims.ipynb`: Compares observed and simulated outcomes for three population types (random, hybrid, and GREASYPOP)
- `4_calibration.ipynb`: Manually adjusts model parameters to better match observed data for deaths
- `5_sim_by_subgroup.ipynb`: Custom analyzer for storing simulated deaths by age, gender, and race
- `6_sim_by_county.ipynb`: Custom analyzer for storing simulated deaths by county

The following supplementary notebooks process observed data for the example of Maryland, DC, and northern virginia. You'll want to do this yourself for your location of interest, but these files are here for reference.
- `i_process_observed.ipynb`: Processes observed cases and deaths for Maryland, DC, and northern Virginia.
- `ii_process_observed_by_subgroup.ipynb`: Processes observed deaths for Maryland by age, gender, and race.
