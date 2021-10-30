# Introduction

This aim of this project is to produce a central repository of high-quality, self-consistent, RR Lyrae-based distance moduli to Local Group dwarf galaxies. The distances are derived by simultaneously fitting the Period-Wesenheit Magnitude-Metallicity relationship for all galaxies using MCMC sampling based on a Bayesian hierarchical model. Currently, the distances are anchored to Gaia EDR3 parallaxes to Milky Way RRab stars with known optical light curves and spectroscopic metallicities.

# Dependencies

Running the model requires recent versions of Python 3 and pyMC3 (https://docs.pymc.io/en/stable/). 

# Citation

This is the public code repository for Nagarajan et al. (2021).

# Documentation

The code for running the MCMC sampler based on the Bayesian hierarchical model is provided in rr_lyrae_mcmc.py. Each of the 39 galaxies with distances derived in Nagarajan et al. (2021) has a data table in both the "Data Tables" and "Theory Tables" folders. The Wesenheit magnitudes in the "Data Tables" folder are generated with color coefficients 1.467 (for the V-I sample) and 3.058 (for the B-V sample) (following Neeley et al. (2019)). The Wesenheit magnitudes in the "Theory Tables" folder are generated with color coefficients 1.38 (for the V-I sample) and 3.06 (for the B-V sample) (following Marconi et al. (2015)). Photometric and spectroscopic parameters for the galaxies in either the V-I sample or B-V sample are provided in either galaxies_VI.csv or galaxies_BV.csv respectively. Also, periods, magnitudes, metallicities, and parallaxes for the Milky Way RR Lyrae are provided in milky_way_VI.csv (for the V and I visual bands) and milky_way_BV.csv (for the B and V visual bands).

The script for fitting the parameters of the Period-Wesenheit Magnitude-Metallicity relationship expects as input: a number of CPUs (for parallel processing), the location of a data table for each galaxy within either the "Data Tables" or "Theory Tables" folder, a catalog of corresponding galaxies in the respective visual bands, the location of calibration data for the Milky Way RR Lyrae, and whether or not to use theoretical priors from Marconi et al. (2015). To derive a distance to a dwarf galaxy with newly discovered RR Lyrae, prepare a .csv file with the following columns: Star, Wesenheit Magnitude, Uncertainty in Wesenheit Magnitude, and Log Period. Then, add data to the Galaxy and Mean Metallicity columns in either galaxies_VI.csv or galaxies_BV.csv, depending on which visual bands the galaxy was observed in. Finally, pass in the location of the data to rr_lyrae_mcmc.py as a command line argument (as described above).

# Sources of Data

| Galaxy | Apparent V Magnitude  | Number of RRab Stars Used | Number of RR Lyrae | Observed Filters | Transformed Filters | References|
|:---------------------------:|:----------------:|:--------------------:|:-------------------:|:------------------:|:---------------------:|:--------------------------------------------------------------:
| Andromeda I                 | 12.7 +/- 0.1   | 229                  | 296                 | F475W, F814W       | V, I                  | Martinez-Vazquez et al. (2017) |
| Andromeda II                | 11.7 +/- 0.2   | 187                  | 251                 | F475W, F814W       | V, I                  | Martinez-Vazquez et al. (2017) |
| Andromeda III               | 14.4 +/- 0.3   | 84                   | 111                 | F475W, F814W       | V, I                  | Martinez-Vazquez et al. (2017) |
| Andromeda XI                | 17.5 +/0 1.2   | 10                   | 15                  | F606W, F814W       | V, I                  | Yang & Sarajedini (2012) |
| Andromeda XIII              | 18.1 +/- 1.2   | 8                    | 9                   | F606W, F814W       | V, I                  | Yang & Sarajedini (2012) |
| Andromeda XV                | 14.6 +/- 0.3   | 80                   | 117                 | F475W, F814W       | V, I                  | Martinez-Vazquez et al. (2017) |
| Andromeda XVI               | 14.4 +/- 0.3   | 3                    | 8                   | F475W, F814W       | V, I                  | Monelli et al. (2016) |
| Andromeda XXVIII            | 15.6 +/- 0.9   | 35                   | 85                  | F475W, F814W       | V, I                  | Martinez-Vazquez et al. (2017)  |
| Bootes I                    | 12.8 +/- 0.2   | 5                    | 15                  | V, I               | V, I                  | Dall'Ora et al. (2006) |
| Canes Venatici I            | 13.1 +/- 0.2   | 18                   | 23                  | BVI                | B, V                  | Kuehn et al. (2008)  |
| Canes Venatici II           | 16.1 +/- 0.5   | 1                    | 2                   | BVI                | B, V                  | Greco et al. (2008)    |
| Carina I                    | 11.0 +/- 0.5   | 62                   | 83                  | UBVI               | V, I                  | Coppola et al. (2015) |
| Carina II                   | 13.3 +/- 0.1   | 2                    | 3                   | gri                | V, I                  | Torrealba et al. (2018) |
| Cetus                       | 13.2 +/- 0.2   | 147                  | 172                 | F475W, F814W       | V, I                  | Bernard et al. (2009)  |
| Coma Berenices              | 14.1 +/- 0.5   | 1                    | 2                   | BVI                | V, I                  | Musella et al. (2009) |
| Crater II                   | 12.15 +/- 0.02 | 28                   | 34                  | BVI                | V, I                  | Monelli et al. (2018), Vivas et al. (2019) |
| Draco                       | 10.6 +/- 0.2   | 211                  | 267                 | V, I               | V, I                  | Kinemuchi et al. (2008) |
| Eridanus II                 | 15.74 +/- 0.05 | 37                   | 67                  | gri                | V, I                  | Martinez-Vazquez et al. (2021) |
| ESO294-G010                 | 15.3 +/- 0.3   | 219                  | 232                 | F606W, F814W       | V, I                  | Yang et al. (2014) |
| ESO410-G005                 | 14.9 +/- 0.3   | 224                  | 268                 | F606W, F814W       | V, I                  | Yang et al. (2014) |
| Fornax                      | 7.4 +/- 0.3    | 1386                 | 1443                | ugriz              | V, I                  | Stringer et al. (2021)|
| Grus I                      | 17.1 +/- 0.3   | 2                    | 2                   | gri                | V, I                  | Martinez-Vazquez et al. (2019) |
| Hercules                    | 14.0 +/- 0.3   | 6                    | 12                  | B, V               | B, V                  | Musella et al. (2012) |
| IC 1613                     | 9.2 +/- 0.1    | 61                   | 90                  | F475W, F814W       | V, I                  | Bernard et al. (2010) |
| Leo A                       | 12.4 +/- 0.2   | 7                    | 10                  | F475W, F814W       | V, I                  | Bernard et al. (2013) |
| Leo I                       | 10.0 +/- 0.3   | 68                   | 164                 | UBVRI              | V, I                  | Stetson et al. (2014) |
| Leo IV                      | 15.1 +/- 0.4   | 3                    | 3                   | BVI                | B, V                  | Moretti et al. (2009) |
| Leo P                       | 16.8 +/- 0.2   | 9                    | 10                  | F475W, F814W       | V, I                  | McQuinn et al. (2015) |
| Leo T                       | 15.1 +/- 0.5   | 1                    | 1                   | F606W, F814W       | V, I                  | Clementini et al. (2012) |
| NGC 147                     | 9.5 +/- 0.1    | 113                  | 177                 | F606W, F814W       | V, I                  | Monelli et al. (2017)  |
| NGC 185                     | 9.2 +/- 0.1    | 531                  | 820                 | F606W, F814W       | V, I                  | Monelli et al. (2017)  |
| Phoenix I                   | 13.2 +/- 0.4   | 95                   | 121                 | F555W, F814W       | V, I                  | Ordonez et al. (2014)  |
| Phoenix II                  | 17.3 +/- 0.4   | 1                    | 1                   | gri                | V, I                  | Martinez-Vazquez et al. (2019) |
| Sagittarius II              | 13.83 +/- 0.1  | 1                    | 5                   | B, V               | B, V                  | Joo et al. (2019) |
| Sculptor                    | 8.6 +/- 0.5    | 271                  | 536                 | BVRI               | V, I                  | Martinez-Vazquez et al. (2016) |
| Segue II                    | 15.2 +/- 0.3   | 1                    | 1                   | B, V               | B, V                  | Boettcher et al. (2013)|
| Tucana                      | 15.2 +/- 0.2   | 216                  | 358                 | F475W, F814W       | V, I                  | Bernard et al. (2009) |
| Ursa Major I                | 14.4 +/- 0.3   | 5                    | 7                   | B, V               | B, V                  | Garofalo et al. (2013) |
| Ursa Major II               | 13.3 +/- 0.5   | 1                    | 1                   | BVI                | B, V                  | Dall'Ora et al. (2012) |
