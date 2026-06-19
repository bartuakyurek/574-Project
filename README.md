# CENG574 Project | Analysis of NYC Yellow Taxi Trip Data

Below, a description to setup and run this project is provided.

## Dataset Setup

Download the following:
-   Original data set from [Kaggle NYC Yellow Taxi Trip Data](https://www.kaggle.com/datasets/elemento/nyc-yellow-taxi-trip-data) specifically `yellow_tripdata_2015-01.csv`
-   Newer version from [NYC TLC website](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
specifically 2015 January - Yellow Taxi Trip Data (`yellow_tripdata_2015-01.parquet` [direct download link](https://d37ci6vzurychx.cloudfront.net/trip-data/yellow_tripdata_2015-01.parquet))
-   Taxi Zone Lookup CSV file from [NYC TLC website](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
    (`taxi_zone_lookup.csv` [direct download link](https://d37ci6vzurychx.cloudfront.net/misc/taxi_zone_lookup.csv))

place all files under ``./data/`` directory.

Note that you can conduct the same procedure for other months available in the Kaggle dataset (e.g. 2016 January, February, March).



## Running Code

The source code is provided under separate jupyter notebook modules for convenience.
They produce required sampled and normalized data sets and then run clustering analysis.
The order of running them is as follows:

    1 - merge_by_dask.ipynb | This module merges Kaggle data with NYC/TLC version to obtain ground truth

    2 - preprocess.ipynb | Conducts feature selection and extraction, and outlier removal

    3 - Sampling modules (can be run independent from each other, order does not matter)

        3.1 - proportional_sampling.ipynb | Takes 500 samples from each Borough except Staten Island, and takes Staten Island fully (as it has too few samples)

        3.2 - grid_sampling.ipynb | Uniformly samples by splitting geographical coordinates into 50x50 grid

    4 -  normalize.ipynb | Normalizes given dataset and saves it to be utilized in the next stage

    5 - projection_and_clustering.ipynb | Conducts main analysis we have covered during assignments and saves relevant figures

NOTE: Sampled subsets as well as their normalized versions are provided. These can be directly run in final notebook projection_and_clustering.ipynb (except for random sampling, in that case stages 1,2, and 4 needs to be run).

Authors: Bartu Akyürek, Seral Buse Atak
