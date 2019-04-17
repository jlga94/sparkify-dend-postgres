# Data Modeling with Postgres: Song Play Analysis
> José Luis Gil Aguilar

This ETL Pipeline was designed for a startup **Sparkify**, who wants to analyze the data comming from their songs and user activity on their new music streaming app. This project creates a star-schema database from a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

### Files in Project
Tha main files for running the project are:
**create_tables.py** - Script to create and drop tables.
**sql_queries.py** - Script with the queries and scripts to use in create_tables.py and etl.py.
**etl.py** - Script with the detail for transforming the original data from json tables to Postgres tables.
**etl.ipynb** - Notebook with the step by step of the process.
**test.ipynb** - Notebook that test that the tables are created and fill with the data from the etl process.

### Schema for Song Play Analysis
Fact and dimension tables were defined for a star schema for analytics purposes.

#### Fact Table
**songplays** - records in log data associated with song plays i.e. records with page NextSong
*songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent*

#### Dimension Tables
**users** - users in the app
*user_id, first_name, last_name, gender, level*

**songs** - songs in music database
*song_id, title, artist_id, year, duration*

**artists** - artists in music database
*artist_id, name, location, lattitude, longitude*

**time** - timestamps of records in songplays broken down into specific units
*start_time, hour, day, week, month, year, weekday*

### Database and tables creation script
A script for drop and create the database **SparkifyDB**, and drop and create every table mentioned before. Run ´python create_tables.py´ in a terminal.

### ETL Script
An ETL script automatically loops through the logs and songs directories, reads every file, transforms the data using Pandas, and insert them on the star-schema acording with the tables previously defined. It asumes that the main tables are already created and uses ´sql_queries.py´. Run ´python etl.py´ in a terminal.
