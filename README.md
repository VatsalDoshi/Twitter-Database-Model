1. Wrote a Python script that includes API calls to Twitter to extract tweet data and
some tweet details like Twitter user, location, hashtags, tweet text, and follower count. The
script also performs some transformations on the data like data cleaning.
2. Next we created our SQL server, source blob, destination database, and batch pools.
For the pools, we used a standard A2 Windows VM instance with two nodes and two
CPUs.
3. We then incorporated the Python script in a batch job (“runpythonscript”) which is
essentially the start of our data pipeline. This batch job runs the Python script, extracts
data from Twitter into data frames, and puts the data into CSV files which are then
automatically uploaded into Azure blobs (our data source).
4. Upon successful loading of data into the source, the second step in our pipeline is
multiple jobs to copy the data from the source (blob storage) to the destination (database) using
column mapping in Azure.
5. For the document data model, we linked a Cosmos DB resource instance to the data
factory as a destination for the hashtag data.
6. For the graph data model, we created Nodes and Edges files to be pushed to our SQL
destination database.
7. As a third step in our pipeline, we also added a job to delete all CSV files from the blob
once the data is copied into the destination.

![image](https://github.com/VatsalDoshi/Twitter-Database-Model/assets/114709734/74253fce-dee8-4038-a2ce-7c166eee0772)
![image](https://github.com/VatsalDoshi/Twitter-Database-Model/assets/114709734/72bb8e80-eb4f-4d1c-b21d-bc9e7767e2cc)



