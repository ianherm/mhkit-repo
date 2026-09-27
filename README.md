# Port Orford - Wave Resource Assessment
This repo was originally created to perform a wave energy assessment for the Port of Port Orford, Oregon ETIPP project. 
I combined programs authored by *Hannah Mankle* and *Andrew Simms, NLR* . *Hannah Mankle* created a Jupyter notebook that uses NREL's MHKiT toolbox to perform resource assessments using data from the MHKiT Hindcast Database.
*Andrew Simms (NLR)* provided a program that transforms Small-WEC-Tool (SWEC) WEC model power matrices from JSON files to CSVs. I combined both programs to assess annual wave energy potential (flux) at two sites near the Port of Port of Port Orford and forecast power produced by the deployment of two, hypothetical SWEC WEC models.

### Acronyms
- NDBC: National Data Buoy Center
- SWDEN: Omnidirectional Wave Spectrum

**Small WEC Tool**: https://apps.openei.org/swec/ 

**Marine and Hydrokinetic Toolkit**: https://mhkit-software.github.io/MHKiT/

While this version is based on the Port of Port Orford ETIPP project, different locations and WEC scales can be used for other community projects or applications. 


### Top-level structure (folders):

- `notebooks/`
	- `Load_MHkit_Test.ipynb`: Test if MHkit is installed in your active environment. 
	- `Hindcast_Assessment_v2.ipynb`: Perform Hindcast Assessment for location
	- `PACWAVE_Annual_Wave_Flux.ipynb`: Pulled from MHKit Github (I think). Also a test. 
- `location/`
	- Site-specific results grouped by deployment location (specified by lat & lon):
		- `Inshore_CSV/`
		- `Inshore2_CSV/`
		- `Offshore_CSV/`
	- Each scenario includes:
		- `Wave/virtual_buoy/` Contains Individual CSVs for each data year (1979 - 2010) and Summary CSV (created by `PortOrford_Hindcast_Assessment_v2.ipynb`) that saves all data years. 
		- `Graphics/`Contains ouputs...
- `figures/`
	- Stores static figures and map (.html) exports.
- `requirements.txt`
	- Python dependency lock list for this workspace.

## Main Workflow

Use notebooks in `notebooks/` to run the primary wave resource analysis and plotting workflows.

Typical process:

1. Create and activate a Python environment.
2. Install dependencies from `requirements.txt`.
3. Launch Jupyter and run the notebooks as needed.