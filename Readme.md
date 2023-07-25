# Explaining Gender Differences in Career Trajectories Across 30 Academic Fields
This repository contains the code and data needed to replicate the analyses presented in the paper *Who supports Bernie? analyzing identity and ideological variation on Twitter during the 2020 Democratic primaries* by shuster, Madani, Campos-Castillo, and Joseph.  If you use this code base or ideas from the paper, please consider citing us!

```
CITATION FORTHCOMING
```

Due to limitations on what can be shared from the Twitter API, we do not share the raw tweets. However, 1) these data are available upon request from the last author, and 2) we provide replication materials for the processes of data collection and manipulating data into the format required for out analysis.  This repository therefore, we believe, contains sufficient data needed to replicate and extend the results presented in the paper. Please open an issue if you have questions!

The replication materials consist of five code files and several data files used in them. Each of the files containing code are described below:

- `01_collect_data.py` - This `python` script uses `tweepy` to listen to the Twitter v1.1 Streaming API for a list of keywords and/or mentions of specific handles. Keywords and handles we listened for are described in the article text, the final list of keywords used is contained in the `api_query.json` file here. To connect to the (now depreciated) streaming API, we called this script at the command line using the statement `python 01_collect_data.py [PATH_TO_API_CREDENTIALS] api_query.json [OUTPUT_DIRECTORY_LOCATION]`.

- `02_preprocess_data.ipynb` - This `python` notebook takes the raw output from `01_collect_data.py` and transforms it into a series of `parquet` files used for downstream analysis. Of particular note is the creation of the `trimmed_rtnet` directory, which contains the data that we run VSP on to generate the clusters we use to identify Bernie-supporting accounts. A tarred and gzipped version of this dataset is [UPDATE]

- `03_run_vsp.ipynb` - This `R` notebook provides the code needed to replicate our use of VSP in the paper for both identifying Bernie-supporting accounts and identifying different sets of framed values.

- `04_post_vsp_dataprocessing.ipynb` - This `python` notebook generates 

- `05_plot_results.ipynb` - This `R` notebook... 

