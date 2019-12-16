# atlytics_team_recylers


## Proj Plan

### EDA
- DT and ANP would focus on generating some interesting insights in the form of graphs, maps(Ref- EVdata hub has interesting ones)
- Can we answer some interesting claims/myths using the data? [Descriptive analysis]

### Predictive

- Calculate BEVs per million for all zip codes. Can we predict this for a new Zip Code? 
Porsche can then determine which Zip code would be most profitable based on this number.[SID]
-  Can test couple of interesting hypothesis
	- Does policy impact BEVs in a region?
		- Two paired test to compare means of 2 groups(One group with all zip codes with incentivized states. Other group being the one which is not incentivized.)

### Probabilistic Modeling
- JLL would come up with some fancy probabilities which would likely increase our probability to win the competition.

## Data
Dropbox link: https://www.dropbox.com/sh/l7t43kaain31w4r/AAD1cxKOc3owapsbtQpoJYYua?dl=0


## News
* Sid Mon 00:21: 
- Cleaned the EV data. Now it contains data for the following states
	- Colorado, Connecticut, Michigan, Minnesota, Washington, Texas, Oregon, Virginia, Vermont
- Each row should now ideally represent each registration[Limited it to 2017-18]
- Now the code is in 1_SID_get_data_from_evhub_V2 notebook.
- Cleaned the blank ZIP codes
- Get the final csv from ev_data file(in the Dropbox)
- 


* JLL Sun 5:25: Just uploaded a clean version of registration data, clean_df.csv. Only rows with zipcodes that appear in  uszipcode_data are now present. Remain to check if the state matches as expected.
* JLL ,Sun 12:12: Moving forward again :). We now have a dataframe that gives us a plethora of demographic and economic indicators per zipcode. See uszipcode_data.csv, roughly 100MB.
* Sid, Sat14:31: 
  - I tried to aggregate all the data from the EV hub and have downloaded in the data folder(compressed as a zip file). 
  - Also aggregated by Zip codes now. We can get features for the zip codes we have.

* JLL, Sat11:34:  US census is a bit bewildering for me. So many variables. Anybody having some luck handling US Census API? I am now using the Python module [uszipcode](https://uszipcode.readthedocs.io/index.html#)  to get demographic and economic data per zipcode. Only problem so far: it needs to be installed via pip. See snippet for installation within a Jupyter notebook environment.
```python
import sys
!{sys.executable} -m pip install uszipcode
```
The added complexity is to ensure that only the local Jupyter environment is affected, see [Installing Python Packages from a Jupyter Notebook](https://jakevdp.github.io/blog/2017/12/05/installing-python-packages-from-jupyter/)


## Resources:

### EV data
1.  [ev hub, Registration and sales by zipcode](https://www.atlasevhub.com/materials/state-ev-registration-data/)
2. [WA Reg_data](https://catalog.data.gov/dataset/electric-vehicle-population-data)

### Charging stations

1. [Charging location data, openchargemap](https://openchargemap.org/site/develop/api)
2. [Chargehub, load on charging stations is updated every 5 mins](https://chargehub.com/en/about-chargehub.html)
3. [Electric Charging station usage data, Canada](https://www.fleetcarma.com/evCloud/Stations)
4. [Electric Charging station usage data, NYSERDA](https://www.nyserda.ny.gov/Researchers-and-Policymakers/Electric-Vehicles/Resources)

### Demographics data
1.  [US Census data](https://data.census.gov/cedsci/)