# Data Engineering Systems CloudSQL Project
To showcase how AWS Athena is used to query a public dataset (ie. housing data in King County - Seattle, hosted on Kaggle) after which I will generate insight from the results of the query. The scope of the dataset is limited to homes sold between May 2014 and May 2015.

The public dataset can be found at the url below:
https://www.kaggle.com/harlfoxem/housesalesprediction/download

Also, I have uploaded a copy called "kc_house_data" into this repository.


## Project Implementation Steps
1. Upload a dataset( into an AWS s3 bucket so that AWS Athena could access it from the cloud. In my this project I uploaded the public dataset into an s3 bucket called "kingcountydata".
[Insert Image]

3. Create a database in AWS Glue. I created "my_housing_database".
[Insert_Image]

4. Opened AWS Athena and selected the database I just created.
[Insert_Image]

6. Since SQL is a relational database, it queries data from tables, so there is the need to create table(s) in AWS Athena. So I clicked "Create table" on the menu bar. I entered the link to the data stored in the afore-mentioned AWS s3 bucket as the source of my data. 
[Insert Image]

AWS Athena conveniently allows the creation of tables by entering the matching column names and data types in a bulk manner. AWS Athena has its peculiar data types and you can use this [link](https://docs.aws.amazon.com/athena/latest/ug/data-types.html) for easy referencing.
[Insert Image]
