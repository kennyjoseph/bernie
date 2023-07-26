# Who supports Bernie?

This repository contains the code and data needed to replicate the analyses presented in the paper *Who supports Bernie? analyzing identity and ideological variation on Twitter during the 2020 Democratic primaries* by shuster, Madani, Campos-Castillo, and Joseph.  If you use this code base or ideas from the paper, please consider citing us!

```
CITATION FORTHCOMING
```
# Data Sharing Information

Due to limitations on what can be shared from the Twitter API, we do not share the raw tweets. However:
1. These data are available upon request from the last author
2. We provide data that is sufficient to replicate all analyses in the present work aside from data collection and the data used to construct of the trimmed retweet network
3. We provide code that shows how raw data was collected and how this trimmed retweet network was constructed.
  
This repository therefore, we believe, contains sufficient data needed to replicate and extend the results presented in the paper. Please open an issue if you have questions!

# Replication Code 

The replication codebase consist of five code files and several data files used in them. Each of the files containing code are described below:

- `01_collect_data.py` - This `python` script uses `tweepy` to listen to the Twitter v1.1 Streaming API for a list of keywords and/or mentions of specific handles. Keywords and handles we listened for are described in the article text, the final list of keywords used is contained in the `api_query.json` file here. To connect to the (now depreciated) streaming API, we called this script at the command line using the statement `python 01_collect_data.py [PATH_TO_API_CREDENTIALS] api_query.json [OUTPUT_DIRECTORY_LOCATION]`.

- `02_preprocess_data.ipynb` - This `python` notebook takes the raw output from `01_collect_data.py` and transforms it into a series of `parquet` files used for downstream analysis. Of particular note is the creation of the `trimmed_rtnet` directory, which contains the data that we run VSP on to generate the clusters we use to identify Bernie-supporting accounts (i.e. our "who retweets whom" analysis). A tarred and gzipped version of this dataset is available in the `data` directory, please make sure to untar before attempting replication. **Additionally, please note that due to the size of the file, we have used [git-lfs](https://github.com/git-lfs/git-lfs) to upload it to this repository. You will need to enable git-lfs to download it.**

- `03_run_vsp.ipynb` - This `R` notebook provides the code needed to replicate our use of VSP in the paper for both identifying Bernie-supporting accounts and identifying different sets of framed values. Results for the who retweets whom clustering (and the experiments using different values of `k`) are available [here](https://www.dropbox.com/scl/fi/qdrv1ivkpqovmcta5agxh/rtnet_clustering.rdata?rlkey=m942oqzflbgr644hakjgribk4&dl=0) as a (16GB!) `.rdata` file.  Our results for the "who retweets what" clustering are available at `data/rt_tweet_clustering.rdata` in this repository, but note that we have used [git-lfs](https://github.com/git-lfs/git-lfs) again with this file.

- `04_post_vsp_dataprocessing.ipynb` - This `python` notebook generates various intermediary datasets used in our results. All of these datasets are included in this repository in the `data` directory as `.tgz` files, please make sure to untar them before replicating our work.

- `05_plot_results.ipynb` - This `R` notebook provides code to generate all of the main figures in the paper, using data provided in this repository.

# Wrapping up

Please let us know if you have any issues!

