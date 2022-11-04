# Data Modeling w/ Postgres


## Context

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.

## Schema

After becoming familiar with the files and data needed for analysis, I created the schema below. This schema will provide the framework for efficient queries as needed by the analytics team. 

<img src="schema.png" alt="database schema" width="800"/>


## ETL Pipeline

After defining the schema to be used for the Sparkify database, my next step was to develop the ETL pipeline. I used Jupyter notebooks to test my extractions, transformations, and loading of the data to the appropriate tables within Postgres. I then took the code written in Jupyter and created the etl.py file, which effecitvely iterates through all song and log files and loads the transformed data into the Sparkify database. 

## Running the Scripts

To get started, run 'create_tables.py' at the command line or terminal. This first script initializes the Sparkify database, drops any residual tables (if they exist), and then re-establishes each of the tables needed within the database. The 'create_tables.py' script runs several user-defined functions ('create_database()', 'drop_tables()', and 'create_tables()'). Each of these functions call on variables stored in the 'sql_queries.py' file. You should NOT run the 'sql_queries.py' file, as each of the variables it holds is called upon and utilized by the functions in the 'create_tables.py' script. 

After the connection to the Sparkify database and all tables have been established, the next step is to run the 'etl.py' script. This is the last step to completing the ETL process. It is responsible for iterating through each of the song and log files, and extracts only the necessary data from each file where it will then call upon several queries stored in variables within the 'sql_queries.py' file to effectively populate each of the tables with the data extracted from each file.

## GLOSSARY OF FILES
    
- 'create_tables.py': establishes connection to Sparkify database, drops residual tables, and re-establishes needed tables. 
- 'sql_queries.py': consists of variables storing the queries used to create and drop tables, insert into tables, and select        songs.
- 'etl.py': iterates through each of the song and log files to extract data needed for the database. It calls upon variables in      'sql_queries.py' to populate the extracted data into the appropriate tables.
- 'test.ipynb': used to test the ETL process as it was being built.
- 'etl.ipynb': used to build and test the ETL process as it was being built.
- 'schema.png': image of the database schema to be created with the ETL process.
- 'data': holds many sub-directories for the song and log data used for populating the database. 


