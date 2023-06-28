# 12-Module-noSql-Challenge
## Eat Safe, Love
noSQL, MongoDB
Python, pymongo (MongoClient), pprint, Pandas, noSQL, MongoDB<br><br>

### SETUP

Part 1: Database and Jupyter Notebook Set Up

In this project we evaluate UK Food Standards Agency food hygiene data for various establishments across the United Kingdom. The analysis will be used for future articles by journalists and food critics for a food magazine.

To start the Windows Command Prompt is opened and, using 'cd', we navigate to the project's resource folder where the json file is saved. From the terminal, we import the dataset with 'mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json'. the database is named 'uk_food and the collection is named 'establishments'. MongoDBCompass is used to confirm the dataset has been imported.

Within the python IDE we import our dipendencies, create an instance of MongoClient and re-confirm that the new database was created.
'uk_food' database is then assigned to a variable and 'list_collection_names' is used to review the collection(s) in the databse, then find_one() is executed in a prettyprint to view a document within the collection. Finally the collections is assigned to a variable.

Part 2: Update the Database

A dictionary is created for a new establishment and inserted into the collection. We then set up a query and to find the recently inserted data and confirm it has been added to the database using a for loop.

Some of the data is missing from the new establishment so a query is executed to find the matching data from similar establishments, update the latest entry and confirm the changes were made.

Data within the Dover Local Authority will not be considered for the project and therefore removed from the dataset. To accomplish this, a query and variable is established where 'LocalAuthorityName' is 'Dover'. Using this query/variable, we get the total number of documents for dover using .count_documents(), execute .delete_many() to remove all the Dover records from the dataset, re-run the .count_documents() to ensure all Dover documents have been deleted and finally check that no other documents were impacted using .find_one().

To complete the clean-up we use update_many to convert latitude and longitude values in the dataset to decimal numbers, convert RatiingValue data to Integer and check that the data values are now number (decimal/integer) types.<br><br>



### ANALYSIS

To start the analysis we import dependencies, create an instance of MongoClient, assign the database to a variable name, review the collection(s), assign that collection to a variable and pretty print a single document within the dataset to review the data.

The first part of analysis we look for any establishments that have a hygiene score equal to 20. To start we create a query where sores.Hygiene is equal to 20 and assign that to a query variable. Aditionally we use the query variable to .find all documents that match our criteria and assign the results to a variable. We use .count_documents to print the total number of establishments that match the criteria and prettyprint the results in the results variable.

Pandas is then used to convert the results into a dataframe, display the number of rows in the dataframe and display the first 10 rows.

We use similar steps to find, display results and convert to Pandas dataframe for the following queries.
- Establishments in London that have a RatingValue greater than or equal to 4
- The top 5 establishments with a RatiingValue of 5, sorted by the lowest hygiene score nearest to the Penang Flavours restaurant (which was added in the setup portion of the project).
- Establishments in each Local Authority with a hygiene score of '0'