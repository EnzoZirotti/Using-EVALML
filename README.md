# Using-EVALML
Using EVALML for machine learning

## Installing Evalml tools/libraries & Woodwork library
I would suggest creating a new virtual environment with conda.
I found it also calls for python 3.8 or 3.9 I ended up using 3.8.1
To add the environment use $ conda install -c conda-forge evalml-core
You will also need to use conda install -c conda-forge alteryx-open-src-update-checker to see if there are extra library needed to add or if any updates were made.
I found Conda to be the easiest to use instead of pip.
On MAC it is. brew install libomp
I then installed Time-Series support with Facebook's Prophet:
Prophet is a time series estimator. This will take a little longer to download.
I also added numba which is needed for shap and prediction explanations.
(conda install -c conda-forge numba)
As well as graphviz.
(conda install -c conda-forge python-graphviz)
A resourse best used also with Evalml is Woodwork which is similar to pandas.
To install Woodwork.
(conda install -c conda-forge woodwork)
Making sure you have everything for woodwork.
(conda install -c conda-forge dask pyspark alteryx-open-src-update-checker)


### Using WoodWork
Woodwork is a library that extends Pandas functionality by adding new data types and enabling efficient operations on them. This will help with data typing of 2 dimentional tabular data structures.