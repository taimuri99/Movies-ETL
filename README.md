# Movies-ETL
Module 8: Using Jupyter Notebook and SQL queries in PostGres, we extracted, transformed and loaded movie data into a database.

## Deliverable 1
An ETL function is written to read in the three data files.

### The function converts the Wikipedia JSON file to a Pandas DataFrame

<img width="1102" alt="Screenshot 2021-12-27 at 13 52 16" src="https://user-images.githubusercontent.com/87828174/147499598-c10f5121-c5ff-435d-9001-745496fb4c84.png">

### The function converts the Kaggle metadata file to a Pandas DataFrame
<img width="1097" alt="Screenshot 2021-12-27 at 13 52 31" src="https://user-images.githubusercontent.com/87828174/147499624-9372c25c-9d05-42fa-ad1f-b82240168e46.png">

### The function converts the MovieLens ratings data file to a Pandas DataFrame

<img width="333" alt="Screenshot 2021-12-27 at 13 52 40" src="https://user-images.githubusercontent.com/87828174/147499630-b1083dba-2cdb-4ba5-8555-89af1a12c961.png">

## Deliverable 2
Using Python, Pandas, the ETL process, and code refactoring, we extract and transform the Wikipedia data so we can merge it with the Kaggle metadata. While extracting the IMDb IDs using a regular expression string and dropping duplicates, we use a try-except block to catch errors. The TV shows are filtered out so a movies dataframe is created. The extraction and transformation of the Wikipedia data in the ETL function does the following:

- A list comprehension is used to keep columns with non-null values. 
- The non-null box office data is converted to string values using the lambda and join functions. 
- A regular expression is used to match the six elements of "form_one" of the box office data.
- A regular expression is used to match the three elements of "form_two" of the box office data. 
- The following columns are cleaned in the Wikipedia DataFrame:

    - The box office column
    - The budget column
    - The release date column
    - The running time column

The cleaned Wikipedia data is converted to a Pandas DataFrame.

<img width="1099" alt="Screenshot 2021-12-27 at 13 58 01" src="https://user-images.githubusercontent.com/87828174/147500041-7c58b835-c513-4c68-be61-f6df2ac015b4.png">

The columns are displayed.

<img width="263" alt="Screenshot 2021-12-27 at 13 58 15" src="https://user-images.githubusercontent.com/87828174/147500051-c462f665-a8ec-469f-b64b-c74f0e609d1d.png">

## Deliverable 3

The extraction and transformation of the Kaggle metadata using the ETL function does the following:

- The Kaggle metadata is cleaned.
- The Wikipedia and Kaggle DataFrames are merged.
- The following is performed on the merged Wikipedia and Kaggle DataFrames to create the movies_df:

    - Unnecessary columns are dropped.
    - A function is used to fill in the missing Kaggle data.
    - The movies_df DataFrame is filtered to keep specific columns.
    - The movies_df DataFrame columns are renamed.

<img width="1092" alt="Screenshot 2021-12-27 at 14 06 38" src="https://user-images.githubusercontent.com/87828174/147500276-3c0865f5-e7d2-4bcb-a6fd-20c74275b92e.png">

The extraction and transformation of the MovieLens ratings data using the ETL function does the following:

- The ratings counts are cleaned.
- The movies_df DataFrame is merged with the cleaned ratings DataFrame to create the movies_with_ratings_df DataFrame.
- The empty values in the movies_with_ratings_df DataFrame are filled with “0”.

<img width="1096" alt="Screenshot 2021-12-27 at 14 07 04" src="https://user-images.githubusercontent.com/87828174/147500301-0a8ecaa3-2a9a-435f-b2bf-284113d67836.png">

## Deliverable 4

Using Python, Pandas, the ETL process, code refactoring, and PostgreSQL to add the movies_df DataFrame and MovieLens rating CSV data to a SQL database. The code to transfer data to the PostGres SQL database is as follows: 

<img width="690" alt="Screenshot 2021-12-27 at 14 09 48" src="https://user-images.githubusercontent.com/87828174/147500447-8297d3bf-2922-4ef8-8883-e032710a1d9f.png">

The data from the movies_df DataFrame replaces the current data in the movies table in the SQL database, as determined by the following SQL query:

<img width="345" alt="movies_query" src="https://user-images.githubusercontent.com/87828174/147500637-19a73c6e-3de2-4882-a42c-4c407df99330.png">

The data from the MovieLens rating CSV file is added to the ratings table in the SQL database, as determined by the following SQL query:

<img width="337" alt="ratings_query" src="https://user-images.githubusercontent.com/87828174/147500668-5130dcbc-3951-4c6a-8ab1-b69a906d2826.png">

The elapsed time to add the data to the database is displayed in the ETL_create_database.ipynb file.

<img width="707" alt="Screenshot 2021-12-27 at 14 14 43" src="https://user-images.githubusercontent.com/87828174/147500767-af025e6b-cae0-46d2-bac4-13790cdf24dd.png">


