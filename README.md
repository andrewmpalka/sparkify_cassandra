# Sparkify Cassandra ETL
Sparkify Cassandra ETL is a jupyter workspace for extracting JSON data, transforming it into database-ready chunks, and loading it into our Cassandra NoSQL DBMS.

# Goal
Sparkify ETL will read files from `event_data`, transform & clean data to fit our needs inside of condensed csv `event_datafile_new`, and add them to the proper places in the schema.

# Schema Design
Cassandra Tables are meant to follow a model-by-query rule

*`song_session`*: For queries against session_id for song data
- session_id -- Primary Key
- item_in_session -- Clustering Key
- artist
- song_title
- song_length

*`song_user_session`*: For queries against user_id, session_id, and item_in_session for song & user data
- user_id -- Primary Key
- session_id -- Clustering Key
- item_in_session -- Clustering Key
- artist
- last_name
- first_name

*`user_song_title`*: For queries against song_title for user last name and full name
- song_title -- Primary Key
- artist -- Clustering Key
- last_name -- Clustering Key
- first_name -- Clustering Key

### Tech

Sparkify uses a number of open source projects to work properly:

* [Conda] - Because I didn't make the original workspace!
* [cassandra] - High performance NoSQL database

### Installation

Sparkify requires:
* [Python3](https://www.python.org/downloads/release/python-363/) v3.6.3+ to run
* [Cassandra](https://github.com/datastax/python-driver) to run

1. Install the dependencies
2. Make sure cassandra is running
3. Restarn and run the kernel for `sparkify.ipynb`:

License
----

MIT