# Hindcast Wave Resource Assessment
This repo was originally created to perform a wave energy assessment for the Port of Port Orford, Oregon ETIPP project. 
I combined programs authored by *Hannah Mankle* and *Andrew Simms, NLR* . *Hannah Mankle* created a Jupyter notebook that uses NREL's MHKiT toolbox to perform resource assessments using data from the MHKiT Hindcast Database.
*Andrew Simms (NLR)* provided a program that transforms Small-WEC-Tool (SWEC) WEC model power matrices from JSON files to CSVs. I removed the Small-WEC-Tool repo from the code. 

### Acronyms
- NDBC: National Data Buoy Center
- SWDEN: Omnidirectional Wave Spectrum

**Marine Energy Atlas**: https://maps.nlr.gov/marine-energy-atlas/

**Marine and Hydrokinetic Toolkit**: https://mhkit-software.github.io/MHKiT/

### Top-level structure (folders):

- `notebooks/`
	- `Load_MHkit_Test.ipynb`: Test if MHkit is installed in your active environment. 
	- `Hindcast_Assessment_v2.ipynb`: Perform Hindcast Assessment for location using 30+years of data saved in CSVs downloaded from "Marine Energ Atlas" and stored in a appropriately organized location folder. 
	- `PACWAVE_Annual_Wave_Flux.ipynb`: Example is pulled from MHKit Github (I think). Analyzes one year of data from a NDBC buoy.  
- `location/`
	- Site-specific results grouped by deployment location (specified by lat & lon):
		- `Neah_Bay_CSV` Example for WA coast lat lon
	- Each scenario folder includes:
		- `Wave/virtual_buoy/` Contains Individual CSVs for each data year (1979 - 2010) and Summary CSV (created by `PortOrford_Hindcast_Assessment_v2.ipynb`) that saves all data years. 
		- `Graphics/`Contains ouputs...
- `figures/`
	- Stores static figures and map (.html) exports.
- `requirements.txt`
	- Python dependency lock list for this workspace.

## Main Workflow

Use notebooks in `notebooks/` to run the primary wave resource analysis and plotting workflows.

Typical process:

1. Create and activate a Python environment using conda. I titled mine 'mhkit-env'. 
2. Install dependencies from `requirements.txt`. The mhkit-software github explains how download MHkit-Python  using conda: https://mhkit-software.github.io/MHKiT/installation.html 
3. Launch and run `Load_MHKit_Test`. If this works your in good shape so far. 
4. Launch and run `PACWAVE_Annual_Wave_Flux.ipynb`. This pulls data from a NDBC buoy and currently analyzes & plots 1-year of data (you choose the year?). I haven't spent much time noodling w/ this notebook, but managed to plot Virginia Beach NDBC buoy 2015 wave resource data. 
5. Launch and run `Hindcast_Assessment_v2.ipynb`. Hopefully nothing goes haywire with the Neah Bay example.
6. On marine energy atlas, choose a lat/lon and download data. Under 'Wave Hindcast: region' Select 'all years' and 'all attributes'. Provide your email and download.
7. Organize your CSVs (hopefully from 1979-2020) in a new 'location folder'
8. Reference your new location data in `Hindcast_Assessment_v2.ipynb` and run. Optionally enter your lat and lon and create a pretty folium map of your deployment location. 