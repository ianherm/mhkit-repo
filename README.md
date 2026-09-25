# Port Orford - Wave Resource Assessment
This repo was originally created to perform a wave energy assessment for the Port of Port Orford, Oregon ETIPP project. 
I combined programs authored by *Hannah Mankle* and *Andrew Simms, NLR* . *Hannah Mankle* created a Jupyter notebook that uses NREL's MHKiT toolbox to perform resource assessments using data from the MHKiT Hindcast Database.
*Andrew Simms (NLR)* provided a program that transforms Small-WEC-Tool (SWEC) WEC model power matrices from JSON files to CSVs. I combined both programs to assess annual wave energy potential (flux) at two sites near the Port of Port of Port Orford and forecast power produced by the deployment of two, hypothetical SWEC WEC models.

**Small WEC Tool**: https://apps.openei.org/swec/ 

**Marine and Hydrokinetic Toolkit**: https://mhkit-software.github.io/MHKiT/

While this version is based on the Port of Port Orford ETIPP project, different locations and WEC scales can be used for other community projects or applications. 


### Top-level structure (folders):

- `notebooks/`
	- `Load_MHkit_Test.ipynb`: Test if MHkit is installed in your active environment. 
	- `PortOrford_Hindcast_Assessment_v2.ipynb`: Perform Hindcast Assessment for location. Forecast SWEC WEC power production
	- `PortOrford_WaveFlux_v1.ipynb`: Old version. Saving for reference.
	- `PACWAVE_Annual_Wave_Flux.ipynb`: Pulled from MHKit Github (I think). Also a test. 
- `location/`
	- Site-specific results grouped by deployment location (specified by lat & lon):
		- `Inshore_CSV/`
		- `Inshore2_CSV/`
		- `Offshore_CSV/`
	- Each scenario includes:
		- `Wave/virtual_buoy/` Contains Individual CSVs for each data year (1979 - 2010) and Summary CSV (created by `PortOrford_Hindcast_Assessment_v2.ipynb`) that saves all data years. 
		- `Graphics/`Contains ouputs...
			- `run_summary.txt` defines WEC Device, annual energy production, and % of total 2024 Port Orford power consumption. 
- `figures/`
	- Stores static figures and map (.html) exports.
- `small_wec_json_reader/`
	- Standalone toolchain to process Small WEC JSON submissions into CSV matrices and heatmaps. Created by Andrew Simms (NLR) to convert SWEC power matrices into .CSV files that can be used in MHKit power production functions. 
	- For each WEC archetype/scale: Raw input JSON files, CSV performance matrices, and matrices & performance visuals (.png) 
- `SmallWEC_Data/`
	- Additional source data files and summary tables. Tbh not sure if this is used at all. 
- `requirements.txt`
	- Python dependency lock list for this workspace.

## Main Workflows

### 1) Notebook-Based Assessment

Use notebooks in `notebooks/` to run the primary wave resource analysis and plotting workflows.

Typical process:

1. Create and activate a Python environment.
2. Install dependencies from `requirements.txt`.
3. Launch Jupyter and run the notebooks as needed.

### 2) Small WEC JSON Processing Pipeline

The script `small_wec_json_reader/small_wec_to_csv.py` processes JSON files in parallel and generates:

- Columnar CSV output per run.
- Metadata JSON per run.
- Binned matrices for:
	- Peak period vs wave height.
	- Energy period vs wave height.
- Heatmap visualizations organized:
	- By run (`viz/by_run/...`)
	- By variable (`viz/by_col/...`)

Run it from the `small_wec_json_reader/` directory:

```bash
python small_wec_to_csv.py
```

Input and output locations for this pipeline:

- Inputs: `small_wec_json_reader/data/00_raw/*.json`
- Numeric outputs: `small_wec_json_reader/data/b1_vap/...`
- Figures: `small_wec_json_reader/viz/...`
