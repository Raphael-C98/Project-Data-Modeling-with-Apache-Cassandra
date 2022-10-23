# Project-Data-Modeling-with-Apache-Cassandra

## Description

As a data engineer I am doing an assignment for the startup Sparkify. Indeed, Sparkify wants to have a precise idea about its music data in order to propose in the future a better music streaming app. To carry out this project first i had to create an Apache Cassandra database which can create queries on song play data. Then via an ETL pipeline i transfered data from a set of CSV files within a directory to create a streamlined CSV file to model and insert data into Apache Cassandra table.

## How to run 


1) Run .ipynb


## An explanation of the files in the repository

*In the "data" repository :* 
- "song_data" is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song.
- "log_data" contains activity logs from a music streaming app based on specified configurations.

*create_table.py :* contains functions which drops and creates the tables.


## Justification of my database schema

I created a star schema optimized for queries on song play analysis. In fact, primarily read optimized, star schemas will deliver good performance over large data sets.


![image](sparkifydb_erd.png)   
    

THE FACT TABLE: The Fact Table is called 'songplays' and contains the columns songplay_id, start_time, user_id, level, song_id, artist_id, session_id, and location. The songplay_id is the primary key for this table. This means each row in this column is unique. 

USERS TABLE: The "users" table is a table which contains the users of the app. The "user_id" column is the primary key column, where the rows are all unique. The columns include user_id, first_name, last_name, gender, and level. This table can be joined to the songplays table by using the 'user_id' column in each table.

SONGS TABLE: The "songs" table contains all the songs in the database. The columns includes song_id, title, artist_id, year, and duration. The "song_id" column is the primary key column for this table. This table can be joined with songplays on 'song_id'.

ARTISTS TABLE: The "artists" table contains the artist names in the database. The columns include artist_id, name, location, latitude and longitude. The "artist_id" is the primary key for this table. This table can be joined to the songplays table on artist_id, and also the songs table.

TIME TABLE: The "time" table has the timestamp data for the song plays broken down into smaller units of time. The columns include start_time, hour, day, week, month, year, and weekday. The start_time column is the primary key. The time table can be joined to the songplays table using start_time.
