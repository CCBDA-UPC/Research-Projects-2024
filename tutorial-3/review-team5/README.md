# Validation for Team 3 - AWS Glue

**This validation was made by Ferent Ioan-Raul.**

### Table of contents
* [Following the Tutorial](#1--following-the-tutorial)
* [Feedback](#2--feedback)
* [Conclusion](#3--conclusion)

## 1 : Following the Tutorial

To follow this tutorial, I utilized AWS Management Console and AWS Glue. This environment provided the necessary tools for creating and managing ETL pipelines using AWS Glue.
I created the folder structure in an S3 bucket as described in the tutorial:

```glue-tutorial/
    |- data/
        |- idealista_db/
    |- temp-dir/
    |- scripts/
```
After that, I uploaded the `idealista` folder to `data/idealista_db/` in S3. The structure was as follows:
```
idealista
    |- ingestion_date=yyyyMMdd
        |- partition.parquet
```
### Defining a Database in AWS Glue
1. Opened AWS Glue Console
2. Navigated to the Databases tab:
  - Selected "**Add database**"
  - Entered the name: `idealista_db`
  - Location: `s3://glue-tutorial/data/idealista_db/`

### Define the Table in the Glue Data Catalog
1. Navigated to the Tables tab.

2. Added tables using a crawler:

  - Name: idealista_crawler.
  - Data source: S3.
  - S3 path: `s3://glue-tutorial/data/idealista_db/idealista/`
  - Selected: Crawl all sub-folders
  - IAM Role: LabRole
  - Target database: `idealista_db`
  - Maximum table threshold: 1
  - Advanced options: Update all new and existing partitions with metadata from the table
  - Crawler schedule: On demand
3. Ran the Crawler:

  - Verified the `idealista` table was created in the Tables tab
  - Confirmed the schema and partitions (ingestion_date) were correctly identified
### Create an ETL Job

1. Navigated to the ETL Jobs tab:

  - Selected "Visual ETL"
2. Configured the source:

  - Name: `idealista_job`
  - Source: AWS Glue Data Catalog
  - Database: `idealista_db`
  - Table: `idealista`
  - IAM Role: `LabRole`
  - Job type: Spark
  - Language: Python
  - Scripts and Temp folder paths: `s3://glue-tutorial/scripts/ and s3://glue-tutorial/temp-dir/`
3. Created a data target:

  - New folder: `s3://glue-tutorial/data/idealista_db/idealista-json/`
  - Selected this folder as the Data Target in Glue
4. Saved and ran the job:

  - Monitored the progress
  - Verified the transformed data in JSON format in S3

### Set Triggers for the Jobs
1. Navigated to the Data integration and ETL tab:

  - Selected "Triggers"
2. Added a schedule trigger:

  Name: `daily_trigger`
  Trigger type: Schedule
  Frequency: Daily
  Start time: Desired hour
  Target resource: `idealista_crawler`
  Created and activated the trigger
3. Added an event trigger:

  Name: `event_trigger`
  Trigger type: Job or crawler event
  Watched resource: `idealista_crawler`
  Status: Succeeded
4. Set the target resource:

  - Resource type: Job
  - Selected `idealista_job`
5. Created and activated the trigger

6. Tested the triggers:

  - Scheduled the trigger to a near time
  - Ensured the crawler ran, followed by the job
  - Monitored the job run status
## 2 : Feedback

The tutorial was extremely clear and well organized. Each step was presented in a logical order, which made it easy to follow without confusion. The instructions were written in a simple way, which made the process the tutorial much easier.

This tutorial was detailed and in-depth, providing all the commands and configuration files needed to complete the setup. There were no missing steps, which ensured that the process was simple and seamless from start to finish.


#### Possible Improvements:

  - Although the tutorial was detailed, it would benefit from additional information on how to set up and configure AWS IAM roles and policies, especially for users who are new to AWS. Including a brief explanation or guide on where to find specific S3 URIs, IAM roles, and other necessary details would help users who are not familiar with AWS.

  - Adding a troubleshooting section would be extremely beneficial. This section could cover common errors that users might encounter during the setup process and provide solutions or troubleshooting tips. 
  - One challenge I encountered was understanding the advanced options for the crawler configuration.

## 3 : Conclusion

Overall, the tutorial provided a clear and structured approach to implementing an ETL pipeline using AWS Glue. It was easy to follow and included all the details needed to successfully complete the setup. 
