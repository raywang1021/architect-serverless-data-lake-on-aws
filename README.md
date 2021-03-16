# Architect Serverless Data Lake on AWS
This sample will show you how to build a serverless data lake on AWS with minium effort to build and connect the workflow.
Includes topics as following:
1. Data Ingestion with Kinesis Firehose
2. AWS Glue for data catalog
3. Amazon Athena to query and analyze data on S3

## Data Ingestion with Kinesis Firehose
Kinesis Data Firehose delivery streams continuously collect, transform, and load streaming data into the destinations that you specify.

Kinesis -> Kinesis Firehose -> create delivery stream
<img width="1408" alt="螢幕快照 2021-03-16 下午1 13 09" src="https://user-images.githubusercontent.com/17841922/111259335-a6962080-8659-11eb-84f3-0802b2e58cc1.png">

Enter Delivery stream name
<img width="1236" alt="螢幕快照 2021-03-16 下午1 13 36" src="https://user-images.githubusercontent.com/17841922/111259333-a564f380-8659-11eb-91a3-e57ff86d00d4.png">
 
Chose S3 as your target, and provide your S3 bucket name, and prefix
<img width="921" alt="螢幕快照 2021-03-16 下午1 14 03" src="https://user-images.githubusercontent.com/17841922/111259324-a1d16c80-8659-11eb-97bc-44e0e0fa1d7b.png">

Your delivery stream created successfully
<img width="1417" alt="螢幕快照 2021-03-16 下午1 19 55" src="https://user-images.githubusercontent.com/17841922/111259745-887cf000-865a-11eb-8f78-0769220127b5.png">

Click it to detail information page
<img width="1421" alt="螢幕快照 2021-03-16 下午1 20 07" src="https://user-images.githubusercontent.com/17841922/111259742-87e45980-865a-11eb-8372-c1a97764419f.png">

Test it with demo data
<img width="1219" alt="螢幕快照 2021-03-16 下午1 20 15" src="https://user-images.githubusercontent.com/17841922/111259739-874bc300-865a-11eb-9510-e0d7a27e3928.png">

Sending demo data
<img width="1224" alt="螢幕快照 2021-03-16 下午1 20 30" src="https://user-images.githubusercontent.com/17841922/111259732-83b83c00-865a-11eb-9dc5-06f65cf7da8d.png">

Wait for 5 min and go to S3 bucket and check data is generated and load to S3
<img width="1138" alt="螢幕快照 2021-03-16 下午1 36 49" src="https://user-images.githubusercontent.com/17841922/111261007-bd8a4200-865c-11eb-850c-fd20e53d9c0b.png">

## AWS Glue for data catalog
The AWS Glue Data Catalog is an index to the location, schema, and runtime metrics of your data. You can use a crawler to populate the AWS Glue Data Catalog with tables. This is the primary method used by most AWS Glue users. 

Glue -> Crawler -> Add Crawler
<img width="1424" alt="螢幕快照 2021-03-16 下午1 32 01" src="https://user-images.githubusercontent.com/17841922/111260600-17d6d300-865c-11eb-941a-fa6f58cffd3e.png">

Provide Crawler name
<img width="1438" alt="螢幕快照 2021-03-16 下午1 35 20" src="https://user-images.githubusercontent.com/17841922/111260997-b9f6bb00-865c-11eb-8bb7-34c4cb421aab.png">

Includes S3 path you want to crawl
<img width="1438" alt="螢幕快照 2021-03-16 下午1 38 56" src="https://user-images.githubusercontent.com/17841922/111261535-95e7a980-865d-11eb-8408-59ea50a5d781.png">

Choose an IAM role
<img width="1440" alt="螢幕快照 2021-03-16 下午1 39 28" src="https://user-images.githubusercontent.com/17841922/111261547-9a13c700-865d-11eb-87dc-900be6bb4482.png">

Configure your output database
<img width="1440" alt="螢幕快照 2021-03-16 下午1 42 01" src="https://user-images.githubusercontent.com/17841922/111261552-9b44f400-865d-11eb-9c94-6a93a6f05e32.png">

Check crawler is created, and run it!
<img width="1202" alt="螢幕快照 2021-03-16 下午1 42 30" src="https://user-images.githubusercontent.com/17841922/111261553-9bdd8a80-865d-11eb-9434-090d02c44f42.png">

Crawler completed and made the following changes.
<img width="1200" alt="螢幕快照 2021-03-16 下午1 50 29" src="https://user-images.githubusercontent.com/17841922/111262127-9df41900-865e-11eb-9648-bd61f537cb06.png">

Check table is created in database
<img width="1196" alt="螢幕快照 2021-03-16 下午1 52 02" src="https://user-images.githubusercontent.com/17841922/111262236-e27fb480-865e-11eb-8866-f016fc21245c.png">

Check detail information in table
<img width="1213" alt="螢幕快照 2021-03-16 下午1 52 26" src="https://user-images.githubusercontent.com/17841922/111262247-e6133b80-865e-11eb-983b-79bdf85cc8e8.png">


## Amazon Athena to query and analyze data on S3
Amazon Athena is an interactive query service that makes it easy to analyze data in Amazon S3 using standard SQL. 

Athena -> chose database which you created table
<img width="1425" alt="螢幕快照 2021-03-16 下午1 55 01" src="https://user-images.githubusercontent.com/17841922/111262562-68036480-865f-11eb-9a44-0fe712bbd978.png">

Run SQL "SELECT * FROM "sampledb"."raw" limit 10;"
<img width="1080" alt="螢幕快照 2021-03-16 下午1 55 44" src="https://user-images.githubusercontent.com/17841922/111262572-6b96eb80-865f-11eb-912e-1d50ce0c0412.png">

See results
<img width="1079" alt="螢幕快照 2021-03-16 下午1 55 49" src="https://user-images.githubusercontent.com/17841922/111262574-6c2f8200-865f-11eb-81bf-91607a29f613.png">

