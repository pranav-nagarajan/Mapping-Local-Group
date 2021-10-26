# Introduction

This aim of this project is to produce a central repository of high-quality, self-consistent, RR Lyrae-based distance moduli to Local Group dwarf galaxies. The distances are derived by simultaneously fitting the Period-Wesenheit Magnitude-Metallicity relationship for all galaxies using MCMC sampling based on a Bayesian hierarchical model. Currently, the distances are anchored to Gaia EDR3 parallaxes to Milky Way RRab stars with known optical light curves and spectroscopic metallicities.

# Citation

This is the public code repository for Nagarajan et al. (2021).

# Documentation

The code for the Bayesian hierarchical model and MCMC sampler is provided in rr_lyrae_mcmc.py. A data table for each galaxy considered in Nagarajan et al. (2021) is provided in "Data Tables" and "Theory Tables" folders. The Wesenheit magnitudes in the "Data Tables" folder are generated with color coefficients (for the V-I sample) and (for the B-V sample) (following Neeley et al. (2019)). The Wesenheit magnitudes in the "Theory Tables" folder are generated with color coefficients (for the V-I sample) and (for the B-V sample) (following Marconi et al. (2015)). A summary of the galaxies with data in the V and I visual bands is provided in galaxies_VI.csv, while a summary of the galaxies with data in the B and V visual bands is provided in galaxies_BV.csv. Data for the Milky Way field RR Lyrae in these visual bands is provided in milky_way_VI.csv and milky_way_BV.csv respectively. Finally, rr_lyrae_VI.sh and rr_lyrae_BV.sh are job submission scripts (designed for use on Savio) for the corresponding groups of dwarf galaxies.

The script for fitting the model expects as input a number of CPUs (for parallel processing), the locations of each data table within the "Data Tables" or "Theory Tables" folder, a catalog of corresponding galaxies in the respective visual bands, the location of calibration data for the Milky Way RR Lyrae, and whether or not to use theoretical priors from Marconi et al. (2015). It is possible to derive distances to galaxies with newly discovered RR Lyrae by re-running this script to fit the parameters of the PWZ relationship. This should be done by preparing a .csv data file columns in the following order: Star, Wesenheit Magnitude, Uncertainty in Wesenheit Magnitude, and Log Period. Furthermore, add data for the new galaxy to at least the following columns in the catalog file: Galaxy and Mean Metallicity. Finally, the location of these data tables can be passed into the model in rr_lyrae_mcmc.py as command line arguments.

# Sources of Data

| \tablehead{\colhead{Galaxy} | \colhead{$m_V$}  | \colhead{$N_{RRab}$} | \colhead{$N_{RRL}$} | \colhead{Observed} | \colhead{Transformed} | \colhead{References}                                           |
|:---------------------------:|:----------------:|:--------------------:|:-------------------:|:------------------:|:---------------------:|:--------------------------------------------------------------:|
| \colhead{(1)}               | \colhead{(2)}    | \colhead{(3)}        | \colhead{(4)}       | \colhead{(5)}      | \colhead{(6)}         | \colhead{(7)}}                                                 |
| Andromeda I                 | 12.7 $\pm$ 0.1   | 229                  | 296                 | F475W, F814W       | V, I                  | \citet{martinez-vazquez_islands_2017}                          |
| Andromeda II                | 11.7 $\pm$ 0.2   | 187                  | 251                 | F475W, F814W       | V, I                  | \citet{martinez-vazquez_islands_2017}                          |
| Andromeda III               | 14.4 $\pm$ 0.3   | 84                   | 111                 | F475W, F814W       | V, I                  | \citet{martinez-vazquez_islands_2017}                          |
| Andromeda XI                | 17.5 $\pm$ 1.2   | 10                   | 15                  | F606W, F814W       | V, I                  | \citet{yang_hst/wfpc2_2012}                                    |
| Andromeda XIII              | 18.1 $\pm$ 1.2   | 8                    | 9                   | F606W, F814W       | V, I                  | \citet{yang_hst/wfpc2_2012}                                    |
| Andromeda XV                | 14.6 $\pm$ 0.3   | 80                   | 117                 | F475W, F814W       | V, I                  | \citet{martinez-vazquez_islands_2017}                          |
| Andromeda XVI               | 14.4 $\pm$ 0.3   | 3                    | 8                   | F475W, F814W       | V, I                  | \citet{monelli_islands_2016}                                   |
| Andromeda XXVIII            | 15.6 $\pm$ 0.9   | 35                   | 85                  | F475W, F814W       | V, I                  | \citet{martinez-vazquez_islands_2017}                          |
| Bootes I                    | 12.8 $\pm$ 0.2   | 5                    | 15                  | V, I               | V, I                  | \citet{dallora_variable_2006}                                  |
| Canes Venatici I            | 13.1 $\pm$ 0.2   | 18                   | 23                  | BVI                | B, V                  | \citet{kuehn_variable_2008}                                    |
| Canes Venatici II           | 16.1 $\pm$ 0.5   | 1                    | 2                   | BVI                | B, V                  | \citet{greco_newly_2008}                                       |
| Carina I                    | 11.0 $\pm$ 0.5   | 62                   | 83                  | UBVI               | V, I                  | \citet{coppola_carina_2015}                                    |
| Carina II                   | 13.3 $\pm$ 0.1   | 2                    | 3                   | gri                | V, I                  | \citet{torrealba_discovery_2018}                               |
| Cetus                       | 13.2 $\pm$ 0.2   | 147                  | 172                 | F475W, F814W       | V, I                  | \citet{bernard_acs_2009}                                       |
| Coma Berenices              | 14.1 $\pm$ 0.5   | 1                    | 2                   | BVI                | V, I                  | \citet{musella_pulsating_2009}                                 |
| Crater II                   | 12.15 $\pm$ 0.02 | 28                   | 34                  | BVI                | V, I                  | \citet{monelli_variable_2018}, \citet{vivas_walker_et_al_2019} |
| Draco                       | 10.6 $\pm$ 0.2   | 211                  | 267                 | V, I               | V, I                  | \citet{kinemuchi_variable_2008}                                |
| Eridanus II                 | 15.74 $\pm$ 0.05 | 37                   | 67                  | gri                | V, I                  | \citet{martinez-vazquez_monelli_cassisi_et_al_2021}            |
| ESO294-G010                 | 15.3 $\pm$ 0.3   | 219                  | 232                 | F606W, F814W       | V, I                  | \citet{yang_early_2014}                                        |
| ESO410-G005                 | 14.9 $\pm$ 0.3   | 224                  | 268                 | F606W, F814W       | V, I                  | \citet{yang_early_2014}                                        |
| Fornax                      | 7.4 $\pm$ 0.3    | 1386                 | 1443                | ugriz              | V, I                  | \citet{stringer_identifying_2021}                              |
| Grus I                      | 17.1 $\pm$ 0.3   | 2                    | 2                   | gri                | V, I                  | \citet{martinez-vazquez_search_2019}                           |
| Hercules                    | 14.0 $\pm$ 0.3   | 6                    | 12                  | B, V               | B, V                  | \citet{musella_stellar_2012}                                   |
| IC 1613                     | 9.2 $\pm$ 0.1    | 61                   | 90                  | F475W, F814W       | V, I                  | \citet{bernard_acs_2010}                                       |
| Leo A                       | 12.4 $\pm$ 0.2   | 7                    | 10                  | F475W, F814W       | V, I                  | \citet{bernard_acs_2013}                                       |
| Leo I                       | 10.0 $\pm$ 0.3   | 68                   | 164                 | UBVRI              | V, I                  | \citet{stetson_homogeneous_2014}                               |
| Leo IV                      | 15.1 $\pm$ 0.4   | 3                    | 3                   | BVI                | B, V                  | \citet{moretti_leo_2009}                                       |
| Leo P                       | 16.8 $\pm$ 0.2   | 9                    | 10                  | F475W, F814W       | V, I                  | \citet{mcquinn_leo_2015}                                       |
| Leo T                       | 15.1 $\pm$ 0.5   | 1                    | 1                   | F606W, F814W       | V, I                  | \citet{clementini_variability_2012}                            |
| NGC 147                     | 9.5 $\pm$ 0.1    | 113                  | 177                 | F606W, F814W       | V, I                  | \citet{monelli_variable_2017}                                  |
| NGC 185                     | 9.2 $\pm$ 0.1    | 531                  | 820                 | F606W, F814W       | V, I                  | \citet{monelli_variable_2017}                                  |
| Phoenix I                   | 13.2 $\pm$ 0.4   | 95                   | 121                 | F555W, F814W       | V, I                  | \citet{ordonez_rr_2014}                                        |
| Phoenix II                  | 17.3 $\pm$ 0.4   | 1                    | 1                   | gri                | V, I                  | \citet{martinez-vazquez_search_2019}                           |
| Sagittarius II              | 13.83 $\pm$ 0.1  | 1                    | 5                   | B, V               | B, V                  | \citet{joo_rr_2019}                                            |
| Sculptor                    | 8.6 $\pm$ 0.5    | 271                  | 536                 | BVRI               | V, I                  | \citet{martinez-vazquez_variable_2016}                         |
| Segue II                    | 15.2 $\pm$ 0.3   | 1                    | 1                   | B, V               | B, V                  | \citet{boettcher_search_2013}                                  |
| Tucana                      | 15.2 $\pm$ 0.2   | 216                  | 358                 | F475W, F814W       | V, I                  | \citet{bernard_acs_2009}                                       |
| Ursa Major I                | 14.4 $\pm$ 0.3   | 5                    | 7                   | B, V               | B, V                  | \citet{garofalo_variable_2013}                                 |
| Ursa Major II               | 13.3 $\pm$ 0.5   | 1                    | 1                   | BVI                | B, V                  | \citet{dallora_stellar_2012}                                   |
