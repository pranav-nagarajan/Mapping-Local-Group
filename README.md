# Introduction

This aim of this project is to produce a central repository of high-quality, self-consistent, RR Lyrae-based distance moduli to Local Group dwarf galaxies. The distances are derived by simultaneously fitting the Period-Wesenheit Magnitude-Metallicity relationship for all galaxies using MCMC sampling based on a Bayesian hierarchical model. Currently, the distances are anchored to Gaia EDR3 parallaxes to Milky Way RRab stars with known optical light curves and spectroscopic metallicities.

# Citation

This is the public code repository for Nagarajan et al. (2021).

# Documentation

The code for the Bayesian hierarchical model and MCMC sampler is provided in rr_lyrae_mcmc.py. A data table for each galaxy considered in Nagarajan et al. (2021) is provided in "Data Tables" and "Theory Tables" folders. The Wesenheit magnitudes in the "Data Tables" folder are generated with color coefficients (for the V-I sample) and (for the B-V sample) (following Neeley et al. (2019)). The Wesenheit magnitudes in the "Theory Tables" folder are generated with color coefficients (for the V-I sample) and (for the B-V sample) (following Marconi et al. (2015)). A summary of the galaxies with data in the V and I visual bands is provided in galaxies_VI.csv, while a summary of the galaxies with data in the B and V visual bands is provided in galaxies_BV.csv. Data for the Milky Way field RR Lyrae in these visual bands is provided in milky_way_VI.csv and milky_way_BV.csv respectively. Finally, rr_lyrae_VI.sh and rr_lyrae_BV.sh are job submission scripts (designed for use on Savio) for the corresponding groups of dwarf galaxies.

The script for fitting the model expects as input a number of CPUs (for parallel processing), the locations of each data table within the "Data Tables" or "Theory Tables" folder, a catalog of corresponding galaxies in the respective visual bands, the location of calibration data for the Milky Way RR Lyrae, and whether or not to use theoretical priors from Marconi et al. (2015). It is possible to derive distances to galaxies with newly discovered RR Lyrae by re-running this script to fit the parameters of the PWZ relationship. This should be done by preparing a .csv data file columns in the following order: Star, Wesenheit Magnitude, Uncertainty in Wesenheit Magnitude, and Log Period. Furthermore, add data for the new galaxy to at least the following columns in the catalog file: Galaxy and Mean Metallicity. Finally, the location of these data tables can be passed into the model in rr_lyrae_mcmc.py as command line arguments.
