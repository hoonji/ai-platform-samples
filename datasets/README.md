# The Datasets

## Taxi Trips Dataset

The [Taxi Trips Dataset](https://data.cityofchicago.org/Transportation/Taxi-Trips/wrvz-psew) wasreleased by the City of Chicago.

Note: This site provides applications using data that has been modified
for use from its original source, www.cityofchicago.org, the official website of
the City of Chicago. The City of Chicago makes no claims as to the content,
accuracy, timeliness, or completeness of any of the data provided at this site.
The data provided at this site is subject to change at any time. It is
understood that the data provided at this site is being used at one’s own risk.

[Read more](https://cloud.google.com/bigquery/public-data/chicago-taxi) about
the dataset in [Google BigQuery](https://cloud.google.com/bigquery/). Explore
the full dataset in the
[BigQuery UI](https://bigquery.cloud.google.com/dataset/bigquery-public-data:chicago_taxi_trips).


The dataset in BigQuery is in a raw format. We have processed the dataset to prepare it for model training.

We have two different sizes of the dataset:

* Small: With 10K samples for training and 2K samples for evaluation. This dataset has a good size for local training and debugging your code.
* Big: With 1M samples for training and 200K samples for evaluation. This dataset is best used in cloud training due to its size.

You can download either dataset (or both) by running one of the two following scripts:

```bash
# To download the both datasets:
source ./download-taxi.sh /path/to/output/directory

# To download the big dataset only:

source ./download-taxi.sh /path/to/output/directory big

# To download the small dataset only:
source ./download-taxi.sh /path/to/output/directory small
```

*Note: Using `source` preserves the environment variables.*

Upon succession, the relevant datasets are downloaded and some or all of the
following environment variables properly exported:

* Local Datasets for Training:
  * `TAXI_TRAIN_BIG`: Local path to the big training dataset
  * `TAXI_EVAL_BIG`: Local path to the big evaluation dataset
  * `TAXI_TRAIN_SMALL`: Local path to the small training dataset
  * `TAXI_EVAL_SMALL`: Local path to the small evaluation dataset
* GCS Datasets for Training:
  * `GCS_TAXI_BIG`: GCS path to the [big training+evaluation dataset](https://storage.googleapis.com/cloud-samples-data/ml-engine/chicago_taxi/training/big/taxi_trips.csv)
  * `GCS_TAXI_TRAIN_BIG`: GCS path to the [big training dataset](https://storage.googleapis.com/cloud-samples-data/ml-engine/chicago_taxi/training/big/taxi_trips_train.csv)
  * `GCS_TAXI_EVAL_BIG`: GCS path to the [big evaluation dataset](https://storage.googleapis.com/cloud-samples-data/ml-engine/chicago_taxi/training/big/taxi_trips_eval.csv)
  * `GCS_TAXI_SMALL`: GCS path to the [small training+evaluation dataset](https://storage.googleapis.com/cloud-samples-data/ml-engine/chicago_taxi/training/small/taxi_trips.csv)
  * `GCS_TAXI_TRAIN_SMALL`: GCS path to the [small training dataset](https://storage.googleapis.com/cloud-samples-data/ml-engine/chicago_taxi/training/small/taxi_trips_train.csv)
  * `GCS_TAXI_EVAL_SMALL`: GCS path to the [small evaluation dataset](https://storage.googleapis.com/cloud-samples-data/ml-engine/chicago_taxi/training/small/taxi_trips_eval.csv)
* Prediction Datasets:
  * `TAXI_PREDICTION_DICT_NDJSON`: a Newline Delimited JSON file with 3 samples, represented as dictionaries
  * `TAXI_PREDICTION_LIST_NDJSON`: a Newline Delimited JSON file with 3 samples, represented as lists

Note: Each line in a Newline Delimited JSON file is a JSON object or list.