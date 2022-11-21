#Purpose of the Database
The purpose of this database is to provide faster queries to the startup as well as help them better organize their data compared to storing data in a JSON file. The database will also provide the ability for more specific queries using sql clauses such as WHERE and JOINS. If the startup gets any more data stored in a JSON file, they can just put those files into the data folder and run the create_tables.py script again to insert the new data into the database so they can query that data if they need to. The startup can also use the queried data to build data models to achieve their analytical goals. 

#How to Run the python scripts
To run the python scripts, simply go to the workspace directory in the terminal and type:

1. python create_table.py
2. python etl.py

The first command will create the SQL tables and the second command will insert the JSON data into the tables.

#What each file does
Create_tables.py will connect to the Sparkify database, create the tables, and drop any existing tables to create new ones if needed. 

Etl.py will read and process the JSON data and insert the data into the respective databse table.

Sql_queries.py contains all the sql statements to create and insert the data into the tables as well as a select statement to query songs. This file is referenced by create_tables.py and etl.py to create tables, insert data into the tables, and select data from the tables.

#Database schema design and ETL pipeline
My database schema is a star schema. The songplays table is the fact table, and the users, artists, songs, and time tables are the dimensional tables. The songplays table has a common column from each of these tables to connect each of the tables to it. The ETL pipeline consists of extracting data from the json files, transforming the data by doing any necessary cast conversions, unit conversions, and extracting the neccessary columns from the files to load into each database using the pandas library to create a dataframe for each data file. The load process consists of referencing the insert statements in sql_queries.py and loading the data into each respective database table.