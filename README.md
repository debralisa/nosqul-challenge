# nosqul-challenge
2
​
5
​##Background
###The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

###SETUP

##Part 1: Database and Jupyter Notebook Set Up:  The supplied starter code (NoSQL_sertup_starter.ipynb was used as base code and then code added to in order to perform the following:

1. The establishments.json file data was imported from my Terminal by navigating to the proper Resource folder containing the supplied json file.  The database was named uk_food and the collection was named establishments.  The Terminal import code was: mongoimport --typ json -d uk_food -c establishments --drop --jsonArray establishments.json

2. Within my Jupyter notebook, the libraries PyMongo and PPrint (Pretty Print) were imported.  I also imported datetime, just in case it was needed at some point (which it was not).

3. I then created an instance of the Mongo Client.

4. To confirm that the database was created and loaded:

    A. I confirmed that uk_food is listed with: print(mongo.list_database_names()) 

    B. Used: print(db.list_collection_names()) to list the collection in the database.

    C. Used find_one and pprint to display one document in the collection.

5. Assigned the establishments collecton to a variable (establishments) to get ready for collection use in Part 2 and the Analysis part of challenge.

##Part 2: Update the Database - The magazine editors have some requested modifications for the database before you can perform any queries or analysis for them. 

1. Added a new, not yet rated, restaurant with supplied information by creating a dictionary and using insert_one.

2. Queried to find the BusinessTypeID for "Restaurant/Cafe/Canteen" and returned only the BusinessType and BusinessTypeID fields.

3. Updated the newly added restaurant with the BusinessTypeID found in the query.

4. Checked how many documents (count_documents) contain the Dover Local Authority. Then, removed (delete_many) any establishments within the Dover Local Authority from the database, and checked the number of documents to ensure they were deleted.

5. Some of the number values were stored as strings in the database, when they should have been stored as numbers.

    A. Used update_many to convert both latitude and longitude to decimal numbers ($toDouble) and verified successful updates.

    B. Used update_many to convert RatingValue to integer numbers from string values.  This was a several step process since variable assignment needed to be made for a list of possible "non rating" strings for the RatingValues in the database.  Then update_many for the non-rating strings to "None".  Finally, update_many from string to $toInt and verify successful updates.

###ANALYSIS. 

##Part 3: Exploratory Analysis - Eat Safe, Love has specific questions they want you to answer, which will help them find the locations they wish to visit and avoid.  Queries to be performed/answered were:

1.  Which establishments have a hygiene score equal to 20?

2.  Which establishments in London have a RatingValue greater than or equal to 4? (used $regex)

3. What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas. (used aggregate)

(count_documents and pprint were used.  Results were convert for each query to a Pandas DataFrame) 

###File Names/Folder Names

#ReadMe.md, NoSQL_setup_starter.ipynb (Jupyter notebook setup file), NoSQL_analysis_starter.ipynb (Jupyter analysis file), Resource folder with data file: 1 json file (establishments.json).​
