![alt text](https://media.wired.com/photos/5c9040ee4950d24718d6da99/191:100/w_2400,h_1256,c_limit/shoppingcart-1066110386.jpg)
# AWS Credit Card Transactions Stream and Batch Processing Data Pipeline

# Introduction & Goals
Cloud services have changed the way that businesses are operated. I have been working on data warehousing as a data engineer and are always exited to expand my toolbox of data engineering. With that in mind, I designed and built this data pipeline to build up knowledge in AWS and its components. The purpose of this project is to build a data pipeline to collect, transform, and store data into different data storages to meet the needs of data users. The credit card transactions dataset is sourced from Kaggle and will be fed into both stream and batch pipelines.

**Major Steps**
* Design an AWS data pipeline framework of stream and batch processing which is practical for real-world enterprises.
* Set up cloud components of stream and batch processing(API Gateway, Kinesis, Lambda Function, Dynamo DB, S3, Redshift and etc.)
* Troubleshoot and maintain the pipeline by using Cloudwatch

**Transactional Goals (Users)**
* To record customer/merchant info of each credit card transaction
* Fraud detection
* Access through: * credit card number and time 
                  * Access Merchant name

**Analytics Goals (Analysts)**
* Regional transaction analysis(e.g. customer purchase preference based on region )
* customer segmentation(e.g. Gender, age)

# Contents

- [The Data Set](#the-data-set)
- [Used Tools](#used-tools)
  - [Connect](#connect)
  - [Buffer](#buffer)
  - [Processing](#processing)
  - [Storage](#storage)
  - [Visualization](#visualization)
- [Pipelines](#pipelines)
  - [Stream Processing](#stream-processing)
    - [Storing Data Stream](#storing-data-stream)
    - [Processing Data Stream](#processing-data-stream)
  - [Batch Processing](#batch-processing)
  - [Visualizations](#visualizations)
- [Demo](#demo)
- [Conclusion](#conclusion)
- [Follow Me On](#follow-me-on)
- [Appendix](#appendix)


# The Data Set
The dataset [Credit Card Transactions Fraud Detection](https://www.kaggle.com/kartik2112/fraud-detection) is sourced from Kaggle. It is simulated with info of transactions, customers, merchants, and whether each transaction is fraud. The reason why I choose this dataset is that it provides enough details for each major section. For example, transaction info includes date, time, credit card/transaction number and etc. Customer info includes location, job, dob, gender and etc. The dataset not only meets the needs of transactional purpose but also of analytical purpose. 

There are also concerns with the dataset although the advantages outweigh the disadvantages in my use case. One of the problems is that the dataset doesn't have customer and merchant IDs which is important for database normalization if the data needs to be stored in a relational database. In this case, I'll need to generate IDs for the customers and merchants.

# Used Tools
![alt text](https://miro.com/app/board/o9J_lpMzpKg=/?moveToWidget=3458764516564478618&cot=14)

## Client
The client is simulated by local PC with the data source downloaded from Kaggle in CSV format. The CSV file is read by python script and then the data is sent to AWS API endpoint through POST method.
## Connect
API Gateway is the API management tool used in this project. It sits between the client and the backend AWS services and acts as a reverse proxy to accept all application programming interface(API) calls, aggregate the various services required to fufill them, and return the appropriate result.
## Buffer
Kinesis is used to ingest, buffer and process streaming data in real-time. The data will lineup in Kinesis every time the API endpoint triggers the Lambda function in AWS.
## Processing
Lambda functions: In this project, the use cases of Lambda function are as follow. 1. Lambda function processes the data from API Gateway and passes it to Kinesis.                   2. Lambda function processes the data from Kinesis and send it to different data stores(S3 & Dynamo DB in this project).

Kinesis Firehose: It captures and automatically load streaming data into S3 and Redshift. The way Redshift ingests the streaming data is that it uses COPY command                     to copy the streaming data loaded into S3.

AWS Glue:
## Storage
Dynamo DB:

S3:

Redshift: 
## Visualization

# Pipelines
- Explain the pipelines for processing that you are building
- Go through your development and add your source code

## Stream Processing
### Storing Data Stream
### Processing Data Stream
## Batch Processing
## Visualizations

# Demo
- You could add a demo video here
- Or link to your presentation video of the project

# Conclusion
Write a comprehensive conclusion.
- How did this project turn out
- What major things have you learned
- What were the biggest challenges

# Follow Me On
Add the link to your LinkedIn Profile

# Appendix

[Markdown Cheat Sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
