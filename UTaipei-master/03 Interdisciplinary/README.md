# geoviews-geopython-2018

[![Binder](https://mybinder.org/badge.svg)](https://mybinder.org/v2/gh/jackdbd/geoviews-geopython-2018/master)

Material for my talk "Approaching geovisualization and remote sensing with GeoViews" @ [GeoPython 2018](http://2018.geopython.net/).

![Basel Parks and Cafes](https://github.com/jackdbd/geoviews-geopython-2018/blob/master/screenshots/basel_parks_and_cafes.png "A Screenshot of this application, showing Basel Parks and Cafes.")

![Basel Districts, Parks and Cafes](https://github.com/jackdbd/geoviews-geopython-2018/blob/master/screenshots/basel_districts_and_cafes.png "A Screenshot of this application, showing Basel Districts, Parks and Cafes.")

![Basel cafes choropleth map](https://github.com/jackdbd/geoviews-geopython-2018/blob/master/screenshots/basel_cafes_choropleth.png "A Screenshot of this application, showing a choropleth map of Basel and its Districts, colored by the number Cafes in that district.")


## Installation

The best way to install all the dependencies for this notebook is to create a conda environment. Either [Miniconda](https://conda.io/miniconda.html) or [Anaconda](https://repo.continuum.io/) are good.

You can use the `environment.yml` file included in this repository to create a conda environment identical to the one I used:

```shell
conda env create --file environment.yml
```

Otherwise you can create and activate a new conda environment with:

```shell
conda create --name geopython-2018 python=3.6 --yes
source activate geopython-2018
```

And install all the dependencies with:

```shell
# geoviews (it depends on holoviews)
conda install -c conda-forge -c ioam holoviews geoviews --yes
# Additional packages (for the examples in the notebook)
conda install xarray  -y
conda install -c conda-forge iris -y
conda install -c conda-forge iris-sample-data
conda install -c conda-forge geopandas -y
```

You will also need to download the Bokeh sample data:

```
import bokeh.sampledata
bokeh.sampledata.download()
```

If you run into issues when importing `geopandas`, try manually downgrading `fiona`:

```
conda install -c conda forge fiona=1.7.10
```


## Data

In order to run the notebook you will also need some data files.

Here is where to find the data used in the notebook:

- Shapefiles of Basel districts @ https://wiki.openstreetmap.org/wiki/City_of_Basel_Suburb_Import (raw data, not the `.osm` file)
- Shapefiles of Basel parks and cafes @ https://extract.bbbike.org/
- netCDF file (Air quality) @ [NOAA](https://www.esrl.noaa.gov/psd/repository/entry/show?entryid=synth%3Ae570c8f9-ec09-4e89-93b4-babd5651e7a9%3AL25jZXAucmVhbmFseXNpcy5kZXJpdmVkL3N1cmZhY2UvYWlyLm1vbi5tZWFuLm5j)
- Shapefile of American Indian/Alaska Native Areas/Hawaiian Home Lands @ [United States Censun Bureau](https://www.census.gov/geo/maps-data/data/cbf/cbf_aiannh.html)

Create a `data` directory in the root of the repository and drop the files there.


## Generate the slides from the notebook

Open a terminal and type:

```
jupyter nbconvert Jupyter Notebook.ipynb --to slides --post serve
```


## Other

You could freeze your environment with:

```shell
conda env export > environment.yml
```

To remove this conda environment, run:

```shell
conda env remove -n geopython-2018
```
