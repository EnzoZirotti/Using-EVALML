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
Initializing woodwork on a dataframe an optional name parameter can be specified to label the data.
Woodwork uses a weak reference for maintaining a reference from the accessor to the dataframe.
Instead of calling it pd.read_ect.ww.init() always pull in the data into a variable and then  init().
Once woodwork is initialized on a dataframe it is recommended to go through the ww namespace
when performing dataframe operations to avoid invalidating woodwork's typing info.


### Using Evalml from start.
Evalml allows the use of demo data that is accessable through evalml.demos.
For example, if we wanted to load the wine dataset we could do so like this:
data = evalml.demos.load_wine()
I then have commented in the evalml_usage.ipynb the way to use this.


### Evalml Diabetes Dataset
This dataset is being pulled in through https://www4.stat.ncsu.edu/~boos/var.select/diabetes.tab.txt dataset so this way I do not break any hipa compliance.From Bradley Efron, Trevor Hastie, Iain Johnstone and Robert Tibshirani (2004) "Least Angle Regression," Annals of Statistics (with discussion), 407-499, we have
"Ten baseline variables, age, sex, body mass index, average blood pressure, and six blood serum measurements were obtained for each of n = 442 diabetes patients, as well as the response of interest, a quantitative measure of disease progression one year after baseline."
s1 tc, total serum cholesterol
s2 ldl, low-density lipoproteins
s3 hdl, high-density lipoproteins
s4 tch, total cholesterol / HDL
s5 ltg, possibly log of serum triglycerides level
s6 glu, blood sugar level
Column 11 is a quantitative measure of disease progression one year after baseline

In the AutoMLSearch I added the problem type to be regression and with the objective being the R2 value to measure of the goodness of fit of the regression model. When finished I got an R2 score of 0.42 which shows that there is a 58% of unexplained variance. My suggestion to fix this for the R2 value is to add more data to the columns to see about lowering unexplained variance. I then adjusted the AutoMLSearch to look at the objective MAE (Mean Absolute Error). By doing this I can measure the average magnitude of errors between the model's predictions and the actual values. When using the MAE score on the holdout data I got a 46.818 which means that is it off by 46.818 units which leads me to see that the prediction model wouldn't be very accurate or precise. I would again suggest to add more data to find a better score for this as well as this doesn't include enough correlation to be of good use.
