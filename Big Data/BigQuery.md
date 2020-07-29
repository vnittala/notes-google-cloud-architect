# Google Cloud Platform BigQuery

[BigQuery](https://cloud.google.com/bigquery/what-is-bigquery) is Google's fully managed, petabyte scale, low cost analytics data warehouse. BigQuery is NoOps—there is no infrastructure to manage and you don't need a database administrator—so you can focus on analyzing data to find meaningful insights, use familiar SQL, and take advantage of the pay-as-you-go model.

## Features

* Fully-managed analytics data warehouse.
* Near real-time interactive analysis of massive datasets (hundreds of TBs).
* SQL like syntax.
* Zero administration for performance and scale.
* Pay for storage and processing only.
* Discounts for long term data storage.

# Points of Interest

* Datasets:
  * Are a grouping mechanism that holds zero or more tables.
  * Are the lowest unit of access control.
  * Are owned by projects.
* Object names are relative to the project.
* Tables:
  * Are the row-column structures that contain actual data within a dataset.
  * Can not have access control.
  * Have a schema.
  * Have strongly-typed columns of values.
  * Support views.
  * Can be virtual defined by an SQL query.
  * Can be external (federated).
  * Can query Cloud Storage directly.
* Storage Optimization
  * Use the expiration settings to remove unneeded tables and partitions
    * Dataset
      * bq update --default_table_expiration 300(seconds) project_id: dataset
    * Tables
      * Table expiration timestamp can be setup with ALTER table command using "expiration_timestamp" 
        * Table expiration preceeds over Dataset table expiration setting
      * Partition expiration can be set using "partition_expiration_days" at the table level
      * If the tables are partitioned by date, the dataset's default table expiration applies to the individual partitions.
    * Take advantage of long-term storage
      * If tables/paritions are NOT accessed for 90 days, they're charged with different pricing model (close to Cloud Storage Nearline costs)
