# Brazilian National Civil Aviation Agency - Public Data Visualization / ETL
## Executive Summary:
Using Python, I extract the data from ANAC website, treated the nulls fields and merged two differents dataframes to complete some fields and with SQL on Big Query merge the datasets for having the airports cordinates for a map visualization. After all this treatment I load the treated dataframe to a Big Query Table and refresh the data visualization that I build on Looker Studio. On Dashboard we can have a better visualization of Data besides of fast insights with the main KPI's:

  ### 1. Flights per Month and Year
  ### 2. Occupation per Flight
  ### 3. Airports Demand / Hubs
  ### 4. Airlines Market Share
  ### 5. Main Routes

## Dataset Problems:
The dataset had in "Destination Airport UF" field 15% of null values and the same for "Origin Airport UF". Besides I need a coordinate reference to build a map visualization on Looker, and the main dataset didn't have these info. Besides the "Airline Name" field had different names for the same company, this could damage your KPI's based on this field.

## Main questions:

  ### 1. How much flights have per month and year?
  ### 2. How much active airports are involved in these operation?
  ### 3. Whic are the main Hubs in Brazil?
  ### 4. Witch are the main International Destinations from Brazil?
  ### 5. What's the occupation tax per flight?
  ### 6. How is it the Domestic, International and Total Market Share?
  ### 7. Can we visualize the routes on the map?

## Extracting, Transforming and Loading Dataset
Using Python I extract the dataset from ANAC website reading whithout downloading saving space. Analysing the null fields, I saw that Origin and Destination UF fields had a high number of null fields. 
So I list all airports with these null field and extract and another dataframe from ANAC website witch contains all airports info to merge and complete the null values, and I used dictionary tool for it.
Still in Python I used the dictionary to group the Airline Name field where were many differents names for the same company.

After, I loaded this treated dataframe in a Google Big Query table which refresh the BI on Looker Studio.
The notebook used for this treatment is on repository.

## Business Intelligence - Looker Studio
The data visualization answer all the questions and bring some context like Coronavirus Pandemic and Brazilian regional info.
Link to BI: https://lookerstudio.google.com/s/sLkPb25YhMM

