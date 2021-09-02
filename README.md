# Data Engineering Systems Cloud SQL Project using AWS Athena

This project showcases how AWS Athena is used to query a public dataset, in this case, housing data in King County - Seattle hosted on Kaggle. Afterwards, insight will be generated from the results of the query. The scope of the dataset is limited to homes sold between May 2014 and May 2015.

The public dataset can be found at the url below:
https://www.kaggle.com/harlfoxem/housesalesprediction/download

Also, I have uploaded a copy called ["kc_house_data"](https://github.com/johnowusuduah/CloudSQL/blob/main/kc_house_data.csv) into this repository.

## Demonstration Video
The link to the video that walks through how exactly this project was carried out can be found [here]

### Alternatively,

## Project Implementation Steps
As an alternative or "quasi transcript" to the demonstration video above, the following outlines the steps to execute the project.

1. Upload a dataset( into an AWS s3 bucket so that AWS Athena could access it from the cloud. In my this project I uploaded the public dataset into an s3 bucket called "kingcountydata".
![Step1](https://user-images.githubusercontent.com/67676957/131927377-71d7b609-1b48-4403-844b-52ac4230835a.png)

2. Create a database in AWS Glue. I created "my_housing_database".
![Step2](https://user-images.githubusercontent.com/67676957/131928056-d15916d0-5e71-423b-9be5-fbde6f9522c9.png)

3. Opened AWS Athena and selected the database I just created.
![Step3](https://user-images.githubusercontent.com/67676957/131928604-582e8e89-df24-48d2-b364-d2b334c1489b.png)

4. Since SQL is a relational database, it queries data from tables, so there is the need to create table(s) in AWS Athena. So I clicked "Create table" on the menu bar. I entered the link to the data stored in the afore-mentioned AWS s3 bucket as the source of my data. If it is your first time using AWS Athena, you will be prompted to set up a query result location in your AWS s3 bucket.
![Step3.5](https://user-images.githubusercontent.com/67676957/131929222-acf82380-00bc-4f6e-b1ba-751ce1407ab5.png) 

5. AWS Athena conveniently allows the creation of tables by entering the matching column names and data types in a bulk manner. AWS Athena has its peculiar data types and you can use this [link](https://docs.aws.amazon.com/athena/latest/ug/data-types.html) for easy referencing.
[Insert Image]

6. After the table is created in AWS Athena, we can preview the table to see if the column names matched the data types just as it does in the original public dataset.
[Insert Image]

7. If the table matches our dataset, we can then run queries on the table without the need for any extra SQL Database Management System. I run the following query to extract the aggregated house prices (rounded to two decimal places) for every year that a house was built:

>>"SELECT yr_built, ROUND(AVG(price),2) AS "average_house_price"
>>FROM king_county_housing_data
>>GROUP BY yr_built
>>ORDER BY 2 DESC;"
[Insert Image]

8. After the result of the query is returned, you can download the results as a csv file into your data analysis tool for analysis. 
[Insert Image]

9. I imported the dataset in Google Colab and carried out the analysis and a one page analyses of the results of the query can be found in the link [here.]()
