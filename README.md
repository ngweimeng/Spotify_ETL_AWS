# Spotify ETL Pipeline using Python and AWS

## Overview
Build an ETL (Extract, Transform, Load) pipeline using Python and AWS services to obtain the artist, album, and song information from the "Top Songs - France" playlist on Spotify. The pipeline first retrieves data from the Spotify API, before transforming into the desired format and loading into a S3 bucket using lambda functions. AWS Glue is then used to crawl and catalog the data which is subsequently queried via Amazon Athena.

## Architecture Diagram
<img src="Spotify ETL Architecture Diagram.png">

## AWS Services used
1. Amazon S3: Amazon S3 is scalable object storage service from AWS designed to store and retrieve any amount of data from anywhere on the web.
2. AWS Cloudwatch: AWS CloudWatch is a monitoring and observability service from Amazon Web Services that provides data and actionable insights. You can use AWS Cloudwatch to collect and track metrics, as well as set alarms.
3. AWS Glue: AWS Glue is a fully managed extract, transform, and load (ETL) service that makes it easy to prepare and load data for analytics and data processing.
4. AWS Lambda: AWS Lambda is a computing service that allows programmers to run code in response to events, without creating or managing servers.
5. Amazon Athena: Amazon Athena is an interactive query service that allows users to analyze data directly in Amazon S3 using standard SQL.

## API
Spotify's API (Spotipy) provides developers with tools to interact with the Spotify platform and access its library of music metadata, playlists, and user account details - [Spotify API Documentation](https://developer.spotify.com/documentation/web-api)

## Files
* spotify_etl_pipeline.ipynb: Jupyter notebook to develop the initial Python code for data extraction and transformation
* extract.py: This code will be loaded in the Lambda function to extract data from the Spotipy API. The file will be stored in "to_process" folder.
* transform.py: This code will be loaded in the Lambda function to perform data transformation and prepare 3 files for the album, artist, and songs to be stored in "transformed_data" folder within S3 bucket. Files in the "to_process" folder will be copied to the "processed" folder and files in "to_process" will be deleted.

## Project Execution Flow
1. Extract data from API
2. Lambda trigger (Weekly)
3. Run Extract Code _[extract.py]_
4. Store Raw Data
5. Trigger Transform Function
6. Transform Data and Load it _[transform.py]_
7. Query Using Athena



