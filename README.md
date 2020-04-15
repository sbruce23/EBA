# EBA
Empirical Frequency Band Analysis (EBA) Algorithm described in "Empirical Frequency Band Analysis of Nonstationary Time Series" by Bruce, Tang, Hall, and Krafty (2019)
Author: Scott A. Bruce

## Description: 
Instructions for implementing empirical band analysis
using the FRESH statistic and procedure from "Empirical Frequency 
Band Analysis of Nonstationary Time Series"
by Bruce, Tang, Hall, and Krafty (2019)

## Dependencies: 
Code was developed using R version 3.5.2 ("Eggshell Igloo"), so code
may not function properly on older versions of R.  The packages listed
in the demo file must also be installed prior to use: momentchi2, fields,
viridis, signal, and fossil.

Code has been tested and developed for data of the following dimensions:
<= 100000 time points (T), <= 20 tapers (K), <= 1000 observations per block (N).
Larger datasets may require more RAM for processing. 

## Quick start guide:
Follow the steps below to simulate data, run the search algorithm
using the FRESH statisic, and create summary tables and plots of the results.
Simulated data is according to the three settings in the paper: white noise (1 band),
linear time-varying dynamics (3 bands), and sinusoidal time-varying dynamics (3 bands).

1) Download the two R files (EBA_demo.R and EBA_functions.R) into a folder of your 
choosing. In what follows, we will assume the folder is saved with the
following path 'C:\EBAdemo'.

2) Open R (version 3.5.2 or newer is recommended) and open the file 
'C:\EBAdemo\EBA_demo.R'. This script contains
all necessary code to simulate data pertaining to the processes
described in the paper and run the search algorithm using the FRESH
statistic.

3) Follow the instructions in the comments of the demo file to simulate
data and apply the EBA search algorithm using the FRESH procedure. 

## Using EBA with the FRESH statistic and procedure on other data:
The following inputs are necessary to run the EBA with the FRESH statisic:

'**X**' is a vector containing a realization of the time series process you wish
to analyze. 

'**N**' is a number representing how many observations should be contained in
each approximately stationary block for the estimation procedure of the local
approximately stationary power spectrum.  For example, N=1000 means that the
time series is broken up into approximately stationary segments each containing
1000 observations.  Note that N must be significantly smaller than the total
length of the time series.

'**K**' is a number representing how many tapers to use in estimating the approximately
stationary local power spectrum using multitaper spectral estimation.  Note here that
K must be significantly smaller than N in order to achieve reasonable frequency
resolution.  For example, if you wish to distinguish behavior for frequencies separated
by 0.01 or larger (this is the bandwidth) and you had N=1000 observations in each 
approximately stationary block, then you could have at most K=9 tapers.  More generally,
using the sine tapers, bw=(K+1)/(N+1). 

'**std**' is a binary indicator to determine if the variance in each stationary block
should be standardized to unit variance (std=TRUE) or not (std=FALSE).

'**alpha**' is the significance level for testing each frequency partition.  For example,
alpha=0.05 corresponds to the 5% significance level or 95% confidence level. 

Once you have created these inputs, you can pass them into the 'eba.search' function 
just as in the demo file for estimation.
