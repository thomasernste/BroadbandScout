# Productionalizing Machine Learning Models for Predicting Housing Values

### Introduction

Many types of companies, their data science teams, and the general public as a whole have an interest in having fair and accurate housing valuations. However, prior to the rise of big data, the process of determining housing values was a somewhat unscientific process determined by lenders, realtors and who knows what else. Indeed, besides the basic goal of people wanting to get their fair money's worth out of their homes, problems like the housing bubble burst that occured in the United States around 2006 were arguably due in part to artificially inflated housing values that were in part the product of a poorly designed valuation process. 

As big data exploded and new forms of data science developed, one way that data science professionals and students have sought to apply data science has been to create machine learning models aimed at predicting the sale price of housing. These efforts have led to the creation of existing machine learning models with relatively high degrees of predictive accuracy. 

Many of these efforts to develop machine learning models for predicting housing prices have been applied to relatively small-scale data. So what if we put one or more of these machine learning models into a data engineering pipeline that's capable of handling massive amounts of streaming data from multiple real estate APIs? That's what this project is designed to do.

### Project:

This data engineering project proposes to build such a production-level pipeline that would enable data scientists to easily refine machine learning models that are able to scale up for massive amounts of streaming data from multiple real estate APIs. There are many challenges involved with productionalizing machine learning models that are highly scaled, however.


### Data Pipeline:

This project will be designed to ingest and proecess massive amounts of streaming data from multiple real estate APIs, then perform stream processing, clean the data as it streams in, enabling real-time training of the machine learning model on that streaming data, enable adjustments to the model by data scientists, and store historical data in a database that can become the basis of a very robust machine learning model.  Based on these needs from my pipeline, I propose the following tools for my pipeline:

- **File System** -------------> AWS S3 

      - Rationale: most obvious choice for working in AWS architecture


- **Ingestion** ---------------> Kafka

      - Rationale:
                  - Enables quick and reliable ingestion of streaming and rest API data from multiple sources/APIs
                  - High throughput for data at massive scale
                  - Works seamlessly with Kafka Streams and KSQL (which enables data wrangling on streaming and rest API  
                    data with SQL)


- **Stream Processing** -------> Kafka Streams / KSQL
                  
      - Rationale:
                  - Works seamlessly with Kafka's ingestion tool and KSQL
                  - It's light-weight
                  - Enables *real-time analytics*, allowing for data scientists to tweak MLM training model on 
                    streaming/rest API data
                  - *Widespread adoption* of Kafka means that many organizations could see potential for running their  
                    machine learning projects on this kind of pipeline
                  - KSQL allows for real-time data wrangling using SQL queries, allowing for necessary data cleaning of data                     requiring application of regular expressions, removing characters, filtering, joins of dataframes from
                    multiple APIs, and more 
                    

- **Scheduling/Monitoring** ---> Airflow

                  - Necessary for scheduling data pulls from some APIs that have limits on data requests
                  - Works well with Kafka tools
                  - Its UI enables visualization, monitoring, and troubleshooting of a production-level pipeline
                  - Allows SQL queries
               

- **DB Storage** --------------> Amazon Redshift

                  - Integrated with analytics within AWS and optimized for analytics
                  - Fully scalable for a massive database


### MVP:

      - Use a single machine learning model and data from at least two real estate APIs

### Stretch goals: 

      - Muliple machine learning models
      - Multiple versions of each machine learning model
      - Add data from additional APIs that may be available
      
