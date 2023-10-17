# my_project

The project combines global datasets to analyze nitrogen indicarors.<br>
A Jupyter notebook contains the sequence of steps for the data manipulation and for the visualization of the results.<br>
The results of the notebook have been pre-calculated and are available in the repository.<br>
The `requirements.txt` can be used to set up the python environment required to execute the notebook.


## Usage

The repository contains an empty folders `data`.
Copy in the folder `data` the content of the zip file that came attached to the email.

The Jupyter notebook return the results of Tasks 1, 2, 3, 4.a and 4.b.
These results are already stored in the folder `output`. 
Execute the notebook and overwrite them if necessary.
The execution time is approximately 12 minutes.

## Requirements

```
Python implementation: CPython
Python version       : 3.8.6
IPython version      : 7.34.0

Compiler    : MSC v.1916 64 bit (AMD64)
OS          : Windows
Release     : 10
Machine     : AMD64
Processor   : Intel64 Family 6 Model 94 Stepping 3, GenuineIntel
CPU cores   : 8
Architecture: 64bit
```

It is necessary to create a python virtual environment using the package `virtualenv`.
If not already available install first `virtualenv`:
```
python -m pip install virtualenv
```

Then create a new virtual environment and install of the dependencies required to execute the notebook:
```
python -m virtualenv my_env --python=3.8
cd my_env
Scripts\activate
pip install -r requirements.txt
```

If it fails using the `requirements.txt`, the installation of single python modules has to be done separately:
```
pip install _module-name_
```

When the environment is set up and activated, navigate to the working directory and run the Jupyter notebook:
```
cd my_project
jupyter notebook
```


## Tasks 
1. Using SPAM raster data, produce a new raster at the same resolution, containing wheat production volume 
(in million tons Mt). Produce a global map and export the raster in a geotif format.
>output\SPAM2005V3r2_global_P_TA_WHEA_A.tif

2. Using the newly created raster and the GAUL shapefile of administrative borders, aggregate production 
to country level and export to a csv file.
>output\wheat_production_country.csv

3. Using the raster of wheat production generated in question 1, and assuming that 2% of harvested wheat 
yield consists of nitrogen (N) element, create, plot and export a raster of N output in harvested wheat yield.
>output\N_yield.tif

4. Using the dataset of country-level nitrogen use efficiency (NUE) of wheat from Zhang et al 2015, 
and steps from previous questions:

	a. estimate for the 10 biggest wheat producers the country-level values of N output in harvested wheat, as well as related total N inputs and N losses (i.e., surplus) and export the dataset as a csv file
	>output\top10.csv

	b. visualize the N outputs and losses for these 10 countries in 1 summary figure (plot to be exported as pdf)
	>output\top10_plot.pdf

	c. explain in 2-3 sentences the main patterns of N losses across countries, in relation to production volume and NUE (including any singular feature).

	>ANSWER<br>
	I believe that the plot can serve to group the countries according to the efficiency of their agriculture production, or at of least wheat production.<br>
	On one side China and India have a very large wheat production and high nitrogen yield, but at the same time, due to a relatively low NUE, the nitrogen loss is also very high.<br>
	On the other side USA, Russian Federation and France are among the top wheat producers, but due to a higher NUE, the nitrogen loss is lower.<br>
	Pakistan, though with a much smaller production than China and India, has a similar low nitrogen efficiency.<br>
	France is the most virtuous wheat producer (highest NUE): France produces only 37% of the wheat produced by China, but it is able to do that with only 18% of China's nitrogen loss.<br>
	The plot, especially if a temporal dimension is added, might be useful for displaying the differences in the efficiency of agricultural production in Global North and in Global South countries.<br>
	

5. Explain in 2-3 sentences how an analysis like the one performed in previous tasks could translate to 
the models within BNR's modeling suite (https://iiasa.github.io/iBIOM/en/main/), including potential limitations.

>ANSWER<br>
The Nitrogen indicators may be used as input of the EPIC model.<br>
Potential limitations: the availability of updated SPAM layers.

6. Please report any issues you encountered or assumptions that you had to make in order to complete the assignment.

>ANSWER<br>
>To answer question 4. I had to manually change two country names in order to merge the vector dataset and the NUE table. This was possible because the tasks considered only 10 countries. Otherwise it would be necessary to implement a more efficient string match.

>I made the assumption that the country's NUE can be used to calculate nitrogen indicators of one specific crop (wheat).

>I experienced some issues with the setting up of the python virtual environment. Some packages had to be installed separately (`geopandas`, `rasterio`) and a the path to the packages had to be added explicitly (see notebook).


## Contact

Giovanni Buzzo<br>
giobuzzo@gmail.com