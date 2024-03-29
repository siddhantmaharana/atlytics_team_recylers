# atlytics_team_recylers

## Temporary questions
1. JLL to Sid: Did you filter the dataset on BEV or did you keep all the entries?
	- It includes all the EV registration data 
2. JLL to Sid: Which time period did you use? It has to be a 12 month period for the same car will reregister every year (on the birthday of the owner at the latest)?
	- Filtered it to just 2018 data
3. We may work with:
- the number of new registrations wthin a time period ( that what we have been doing)
- the number of evs on the road ( ie the number of evs with a valid registration)
	To compute the second number: pick a date. https://www.atlasevhub.com/materials/state-ev-registration-data/ uses 8/10/2019. Go through the registration database and pick the rows where 8/10/2019 is between the registration date and the expiration date. Now we have the cars that have a valid registration at 8/10/2019, or what they call the cars on the road. 
The advantage of using cars on the road ( per 1000):
	- fits nicely with the ev charging station study ( cars on the road in a particular location by model) 
	- it is what ev hub is using (hence easy comparison for checking our values)
	- registration validity may not be one year in all juridictions or for all drivers. We may not be able to go from new registrations to cars on the road that easily.

What ya'll think?

4. Sid to JLL:
	- Ya, I have filtered the data to contain just the registrations in 2018
	- That would definitely sum to EVs on road. To answer your other question, if you head over to that website and change a state, the snapshot date changes. Even I thought I would just pick the latest snapshot date. So, right now I am limiting all the rows within Jan 1, 2018 till Dec 31, 2018. That should be good for the analyses. Except for Colorado and a couple of other states, a lot of them don't even allign with that provided in the website.
	- And, if you check out my other notebook(2), I have calculated EV per 1k people. That could be our target variable. 

Answer: That is a perfectly fine approach for our purpose. We are talking of two related target variables (Maybe identical but I am not convinced at this point and do not want to take the time to investigate). Let's stick to the one we started with and that you prefer.

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


* Sid Mon 12:18
	- Filtered data to include just 2018 reg data(ev_data.csv)

* Sid Mon 02:24
Notebook:  2_SID_get_metrics_by_ZIP
	- get target variables(EV per 1k)
	- get features cleaned as well
	- use these to frame this into a regression problem

* Sid Mon 00:21: 
	- Cleaned the EV data. Now it contains data for the following states
		- Colorado, Connecticut, Michigan, Minnesota, Washington, Texas, Oregon, Virginia, Vermont
	- Each row should now ideally represent each registration[Limited it to 2017-18]
	- Now the code is in 1_SID_get_data_from_evhub_V2 notebook.
	- Cleaned the blank ZIP codes
	- Get the final csv from ev_data file(in the Dropbox)
-

* JLL Sun 5:25: Just uploaded a clean version of registration data, clean_df.csv. Only rows with zipcodes that appear in  uszipcode_data are now present. Remain to check if the state matches as expected. Mon 11:00 data set superceded by Sid files.
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
3. [Vehicle Fuel Type Count by Zip Code for California](https://data.ca.gov/dataset/vehicle-fuel-type-count-by-zip-code/resource/d304108a-06c1-462f-a144-981dd0109900) 600K entries, year 2018, 17K entries for BEV,Plug In Hybrid 16K
4. [Vehicle, Snowmobile, and Boat Registrations](https://data.ny.gov/Transportation/Vehicle-Snowmobile-and-Boat-Registrations/w4pv-hbkt/data) "This dataset contains the file of vehicle, snowmobile and boat registrations in NYS." 12 million entries. Electric Vehicles per County subset, 





### Charging stations

1. [Charging location data, openchargemap](https://openchargemap.org/site/develop/api)
2. [Chargehub, load on charging stations is updated every 5 mins](https://chargehub.com/en/about-chargehub.html)
3. [Electric Charging station usage data, Canada](https://www.fleetcarma.com/evCloud/Stations)
4. [Electric Charging station usage data, NYSERDA](https://www.nyserda.ny.gov/Researchers-and-Policymakers/Electric-Vehicles/Resources)
5. [Charge time data, Boulder](https://bouldercolorado.gov/open-data/electric-vehicle-charging-stations/)

### Demographics data
1.  [US Census data](https://data.census.gov/cedsci/)
