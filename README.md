# atlytics_team_recylers

## News

* JLL, Sat11:34:  US census is a bit bewildering for me. So many variables. Anybody having some luck handling US Census API? I am now using the Python module [uszipcode](https://uszipcode.readthedocs.io/index.html#)  to get demographic and economic data per zipcode. Only problem so far: it needs to be installed via pip. See snippet for installation within a Jupyter notebook environment.
```python
import sys
!{sys.executable} -m pip install uszipcode
```
The added complexity is to ensure that only the local Jupyter environment is affected, see [Installing Python Packages from a Jupyter Notebook](https://jakevdp.github.io/blog/2017/12/05/installing-python-packages-from-jupyter/)


## Resources:

### EV data
#### [ev hub, Registration and sales by zipcode](https://www.atlasevhub.com/materials/state-ev-registration-data/)
### Charging stations
#### [Charging location data, openchargemap](https://openchargemap.org/site/develop/api)
#### [Chargehub, load on charging stations is updated every 5 mins](https://chargehub.com/en/about-chargehub.html)
#### [Electric Charging station usage data, Canada](https://www.fleetcarma.com/evCloud/Stations)
#### [Electric Charging station usage data, NYSERDA](https://www.nyserda.ny.gov/Researchers-and-Policymakers/Electric-Vehicles/Resources)

### Demographics data
#### [US Census data](https://data.census.gov/cedsci/)
#### [Zip code Census data](https://data.census.gov/cedsci/table?q=&g=0400000US13,23_8600000US80003&table=S0101&tid=ACSST1Y2018.S0101&layer=zcta5&hidePreview=false&cid=S0101_C01_001E&vintage=2018&lastDisplayedRow=16)
