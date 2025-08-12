uavsar_wildfire_classification
DOI

This product uses UAVSAR polarimetric data to generate fire perimeter and burn severity maps from HV polarization backscatter.

Before using this tool, apply radiometric terrain correction (RTC) to the UAVSAR data for study areas containing terrain shadow, using the radiometric_terrain_correction repository.

Ensure conda is set up prior to use. If not, mambaforge can be installed here, or conda can be installed here.

Alternatively
You can follow the steps within the README.md provided within Docker_for_UAVSAR folder to build an image that imports all of the necessary packages for the notebooks and opens a port for you to interact with through your browser.

Setup (Mac)
Open terminal.
Clone this repository:
git clone git@github.jpl.nasa.gov:UAVSAR-Fire-Research/uavsar_wildfire_classification.git
Create a virtual environment using conda:
conda create --name classification python=3.11
Confirm with y to download the listed packages.
Activate the virtual environment:
conda activate classification
Install requirements (this will take a while):
conda env update -f environment.yml
Create a new Jupyter kernel:
python -m ipykernel install --user --name classification
Ensure the kernel is classification when using Jupyter Notebook.
This has not been tested for Windows OS, but the setup steps should be similar except running them on Anaconda Prompt. More information can be found here.

Data Info
This product requires incidence angle images and the post-RTC HV images for the area of interest.

File Descriptions
Configuration Files

config.json: Configuration file for defining parameters and paths.
Jupyter Notebooks

crop_image.ipynb: Crop the raster image by a fire perimeter in GeoJSON or shapefile format.
preprocessing_segmentation.ipynb: Preprocess the images and perform superpixel segmentation. Outputs are saved for future use.
perimeter_generation.ipynb: Generate the fire perimeter map.
burn_severity_generation.ipynb: Generate the burn severity map (preprocessing happens here).
Python Scripts

process_utils.py: Utility functions for merging GeoJSON (perimeter) or images (severity).
data_prep.py: Prepare data for processing.
run_analysis.py: Run the main analysis pipeline.
Environment Setup

environment.yml: Conda environment configuration file.
Workflow
Fire Perimeter Map Generation
Use crop_image.ipynb to crop the raster image by the fire perimeter.
Run preprocessing_segmentation.ipynb to preprocess the cropped image and perform superpixel segmentation. The outputs for both are saved for the next step.
Execute perimeter_generation.ipynb to generate the fire perimeter map.
Burn Severity Map Generation
Use crop_image.ipynb to crop the raster image by a fire perimeter in GeoJSON or shapefile.
Run burn_severity_generation.ipynb to generate the burn severity map (preprocessing will occur in this notebook).
Notebooks Demonstrations

crop_image.ipynb
Crop raster image by user-defined coordinates, GeoJSON, and shapefile.
Reproject raster images to another coordinate reference system.
preprocessing_segmentation.ipynb
Preprocess the images and perform superpixel segmentation.
Save outputs for future use.
perimeter_generation.ipynb
Generate and select fire polygons with user interaction.
Merge output GeoJSON if a fire involves multiple flight lines.
burn_severity_generation.ipynb
Generate the burn severity map.
Visualize the distribution of the log ratio values for each burn severity class through boxplot.
Each flight line should be processed separately, and outputs can be merged using merge_geojson (perimeter) or merge_image (severity) functions in process_utils.py.

Copyright 2023, by the California Institute of Technology. ALL RIGHTS RESERVED. United States Government Sponsorship acknowledged. Any commercial use must be negotiated with the Office of Technology Transfer at the California Institute of Technology.

This software may be subject to U.S. export control laws. By accepting this software, the user agrees to comply with all applicable U.S. export laws and regulations. User has the responsibility to obtain export licenses or other export authority as required before exporting such information to foreign countries or providing access to foreign persons.# uavsar-wildfire-project
