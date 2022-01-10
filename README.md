
# Project: Data Modeling with Postgres

This project models a Postgres database with tables designed to optimize queries on song play analysis for a startup called Sparkify.   
The objective is to create a database schema and ETL pipeline for the analysis of data Sparkify been collecting on songs and user activity on their new music streaming app.

## Project Strcuture
***
|____data			# Dataset
| |____log_data
| | |____...
| |____song_data
| | |____...
|
|____notebook			# notebook for developing and testing ETL
| |____etl.ipynb		    # developing ETL builder
| |____test.ipynb		    # testing ETL builder
| |____cheat-sheet.pdf
|
|____src			# source code
| |____etl.py			    # ETL builder
| |____sql_queries.py		    # ETL query helper functions
| |____create_tables.py		    # database/table creation script

## ETL Pipeline
***
#### etl.py

ETL pipeline builder

1. process_data
    - Iterating dataset to apply process_song_file and process_log_file functions
2. process_song_file
    - Process song dataset to insert record into songs and artists dimension table
3. process_log_file
    - Process log file to insert record into time and users dimensio table and songplays fact table

**create_tables.py**

Creating Fact and Dimension table schema

1. create_database
2. drop_tables
3. create_tables

**sql_queries.py**

Helper SQL query statements for etl.py and create_tables.py

1. *_table_drop
2. *_table_create
3. *_table_insert
4. song_select

## Database Schema
***

#### Fact table

songplays
	- songplay_id 	PRIMARY KEY
	- start_time 	REFERENCES time (start_time)
	- user_id	REFERENCES users (user_id)
	- level
	- song_id 	REFERENCES songs (song_id)
	- artist_id 	REFERENCES artists (artist_id)
	- session_id
	- location
	- user_agent

#### Dimension table

users
	- user_id 	PRIMARY KEY
	- first_name
	- last_name
	- gender
	- level

songs
	- song_id 	PRIMARY KEY
	- title
	- artist_id
	- year
	- duration

artists
	- artist_id 	PRIMARY KEY
	- name
	- location
	- latitude
	- longitude

time
	- start_time 	PRIMARY KEY
	- hour
	- day
	- week
	- month
	- year
	- weekday