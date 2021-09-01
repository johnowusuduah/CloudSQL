# Data Engineering Systems Cloud SQL Project
This project showcases how AWS Athena is used to query a public dataset, in this case, housing data in King County - Seattle hosted on Kaggle. Afterwards, insight will be generated from the results of the query. The scope of the dataset is limited to homes sold between May 2014 and May 2015.

The public dataset can be found at the url below:
https://www.kaggle.com/harlfoxem/housesalesprediction/download

Also, I have uploaded a copy called "kc_house_data" into this repository.

## Demonstration Video
This [link](insertYouTubeVideo) to a video that walks through how exactly this project was carried out.

### Alternatively,

## Project Implementation Steps
As an alternative or "quasi transcript" to the demonstration video above, the following outlines the steps to execute the project.

1. Upload a dataset( into an AWS s3 bucket so that AWS Athena could access it from the cloud. In my this project I uploaded the public dataset into an s3 bucket called "kingcountydata".
[Insert Image]

2. Create a database in AWS Glue. I created "my_housing_database".
[Insert_Image]

3. Opened AWS Athena and selected the database I just created.
[Insert_Image]

4. Since SQL is a relational database, it queries data from tables, so there is the need to create table(s) in AWS Athena. So I clicked "Create table" on the menu bar. I entered the link to the data stored in the afore-mentioned AWS s3 bucket as the source of my data. If it is your first time using AWS Athena, you will be prompted to set up a query result location in your AWS s3 bucket.
[Insert Image] 

5. AWS Athena conveniently allows the creation of tables by entering the matching column names and data types in a bulk manner. AWS Athena has its peculiar data types and you can use this [link](https://docs.aws.amazon.com/athena/latest/ug/data-types.html) for easy referencing.
[Insert Image]

6. After the table is created in AWS Athena, we can preview the table to see if the column names matched the data types just as it does in the original public dataset.
[Insert Image]

7. If the table matches our dataset, we can then run queries on the table without the need for any extra SQL Database Management System. I run the following query to extract the aggregated house prices (rounded to two decimal places) for every year that a house was built:

"SELECT yr_built, ROUND(AVG(price),2) AS "average_house_price"
FROM king_county_housing_data
GROUP BY yr_built
ORDER BY 2 DESC;"
[Insert Image]

8. After the result of the query is returned, you can download the results as a csv file into your data analysis tool for analysis. 
[Insert Image]

9. I imported the dataset in R Studio and carried out the analysis and a one page analyses of the results of the query can be found in the link below:

## [LINK TO ONE PAGE ANALYSES OF QUERY RESULTS](https://github.com/johnowusuduah/CloudSQL/blob/main/visualization_markdown.html)
