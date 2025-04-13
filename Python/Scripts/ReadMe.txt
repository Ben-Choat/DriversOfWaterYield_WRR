2022/07/26 Ben Choat
Text file describing the files located in the Python/Scripts directory related to
GAGESii_ANNstuff (GAGESii work from my PhD dissertation).

GAGESii_Class.py: Defines the Clusterer and Regressor objects which contain nearly all
	methods and objects used in this analysis.

GAGESii_Class_Apply.py: This is the testground/playground for the GAGESii_Class.py script.
	It is also the best script to view for examples of applying the GAGESii_Class.py classes.

GAGESii_AddAntecedent_All.py: Script to define antecedent variables for all 
	DAYMET variables. Opposed to summing or average, this script simply provides
	the actual reported values for each day, month, or year or a spefied lead time.

GAGESii_Mapping.py: Script to produce maps for GAGESii chapter of dissertation.

GAGESii_Plotting.py: Script used for plotting results from GAGESii work. E.g.,
	heatmap of shap values, barplots of shap values.

GAGESii_SHAP_CalcAll.py: Script to calculate all shapley values for each model specified. It also
	performs linear regression on standardized explanatory variables and shape values to get
	a general directional relationship.

GAGESii_ExploreTree.py: Explore information available in the XGB trees produced during 
	training.

GAGESii_ProcessWWTP.py: Code to read in WWTP effluent data, sum the total effluent
	within a catchment, and write out to explanatory variable csv.


GAGESii_timeseries_plots.py: Create timeseries plots of results

Gather_Outputs.py: Script to gather outputs from individual models (e.g., ecoregions)
	and combine them into one of two pickle files. One pickle file holds the results
	for individual catchments and the other holds summary results. 

DownloadDAYMET_Annual.py: Script to download annual daymet data using the shape files that came 
	with the GAGESii data.

DownloadDAYMET_Monthly.py: Script to download monthly daymet data using the shape files that came 
	with the GAGESii data.

Plotting_Scratch.py: A plotting playground. Currently (2022/07/26) primarily used to investigate
	regression results from mean annual water yield data including all data and ecoregions

Regression_PerformanceMetrics_Functs.py: Script that defines several functions, such as 
	adjR2, MAE, VIF, etc. to be applied when analyzing the performance of predictive models.

ExplDataReduction_VIF.py: Short script to remove variables that have a VIF greater than
	a defined threshold (.e.g., 10). Removes variables with largest VIF first. If 
	variables tie, then variables that tie are removed in alphabetical order.

Train_Val_Test_RePartitioning_AdvVal.py: After investigating original partitioning, decided to repartition
	data using adversarial paritioning up front. 

	This script also removes catchments for which daily DAYMET data failed to download.
	The relevant lines of code will be commented out if we decide to remove daily 
	data from analysis.

	NOTE: This is now (10/1/2022) the main script partitioning data into training, validation, and testing 
	partitions.

Train_Val_Test_RePartitioning.py: Similar to Train_Val_Test_RePartitioning_AdvPart.py, except
	does not consider multiple random states, but rather, uses one and then applies 
	adversarial validation after the fact to investigate if data was split in a way where
	the partitions are from the same distribution (i.e., xgboost is unable to identify
	which data is in training vs testing/validation partitions based on explantory vars.


CSVtoPickle.py: Script to read in multiple csv files and combine them into a single
	pickle file. Was used to combine DAYMET and USGS csv files into training
	testin, and valnit pickle files.

CSVtoParquet.py: Script to read in multiple csv files and combine them into a single
	parquet file. Was used to combine DAYMET and USGS csv files into training
	testin, and valnit pickle files. This was motivated by consideration of using
	DASK for parallel processing. It allows readinga and writing Parquet files
	but not pickle files.

HPC_$TIMESCALE_Callable.py: Script that defines function that applies specified models
	 at specified $TIMESCALE when called

HPC_$TIMESCALE_CallPred.py: Script that calls HPC_$TIMESCALE_Callable.py. This script
	is where data is developed for use in Callable script.

HydrologicLandscapes.py: Script to assign each study catchment to a hydrologic
	landscape region (Winter 2001)..

Load_Data.py: Defines a function that loads explanatory variables, response variables,
	and ID variables for specified time-scale

NGE_KGE_timeseries.py: Function to calculate NSE and KGE.

