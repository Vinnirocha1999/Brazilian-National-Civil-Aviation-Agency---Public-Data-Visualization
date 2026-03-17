# Brazilian National Civil Aviation Agency - Data Pipeline and Visualization

This project builds an automated data pipeline using public aviation data
published by the Brazilian National Civil Aviation Agency (ANAC).

The pipeline collects raw data, performs data cleaning and transformation,
loads the processed data into a data warehouse and generates interactive
visualizations for flight analysis.

Main goals:

• Analyze domestic flight routes in Brazil

• Identify busiest airports

• Understand flight distribution across the country

## Data Pipeline Architecture

ANAC Open Data

      ↓
        
Python ETL
    
      ↓
BigQuery Data Warehouse
       
      ↓
      
Looker Studio Dashboard

## Technologies Used

• Python – Data processing and ETL

• Pandas – Data transformation

• SQL – Data aggregation

• BigQuery – Data warehouse

• Looker Studio – Data visualization

• GitHub – Version control

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

## Geral View

<img width="968" height="360" alt="image" src="https://github.com/user-attachments/assets/087a8791-c308-47d3-ae82-b99ee8e3f702" />

## Top Hubs and International Destinations from Brazil
<img width="438" height="552" alt="image" src="https://github.com/user-attachments/assets/952eca17-47da-4a55-833b-6dd7d8b30c36" />

<img width="432" height="545" alt="image" src="https://github.com/user-attachments/assets/1982c9e7-21ab-4988-ae4b-83d7bfb63dd5" />

## Flights per Month and Year

<img width="1290" height="413" alt="image" src="https://github.com/user-attachments/assets/a2529fd4-7474-40e6-a53a-9cec349c9063" />

<img width="1329" height="391" alt="image" src="https://github.com/user-attachments/assets/d73d028b-379d-414e-b971-1c54d31fa5d6" />


## Airlines Market Share

<img width="1819" height="527" alt="image" src="https://github.com/user-attachments/assets/05233762-b857-43db-a63a-c9fb5e065fe2" />

## Main routes
<img width="1842" height="748" alt="image" src="https://github.com/user-attachments/assets/c242e6e1-304e-4bc7-aa5d-f07bcb3205b4" />

## Key Insights

• São Paulo–Congonhas and São Paulo–Guarulhos are among the busiest airports.

• The highest flight volume occurs between major metropolitan regions.

• Domestic routes represent the majority of flight traffic in Brazil.

• After the Coronavirus Pandemic, flights presents a growth of 7% per year.

• LATAM Airlines is the first one in Market Share, followed by AZUL Airlines and GOL Airlines.

• The Top 3 International destinations are Argentina, Chile and EUA.

## Future Improvements

• Automate data ingestion using Google Cloud Scheduler
