# Information Reterivel 

## ABSTRACT
The use of the Internet has fully-fledged intensely over the past few years. Information resources are available all over, both in internal networks and on the Internet. This progress represents an implausible means of information. The increasing amount of information requires information retrieval (IR) systems for users to access information efficiently. The main goal of Information Retrieval is to develop systems that would let users access all information resources available in the network. For this purpose we use (ETL) tools to extract data from multiple, assorted data sources, transform data, and finally load data into the database and data mining. Data quality is so important for accurate, complete, and efficient data to be provided to the user.
## ABOUT RECIPES INFORMATION RETRIEVAL
Information retrieval is dependent on a user's queries. To make the document more convenient, the query and content in the document are consistent. To eliminate extraneous data and arrive at more exact results, information retrieval techniques are used. Finding relevant information quickly within large amounts of data and ranking the findings according to relevancy. As a result, IR systems provide users with online access to information they may not be aware of, and they are not required to know or care where the information is stored. Users can inquire with a single search.
## GETTING STARTED
To evolve various recipes over the internet we need some way to collect all the recipe data. The technique we imply to gather all the recipe relevant data is data extraction and the tool we use for this purpose is Visual Web Ripper.
## 1-	INSTALLING VISUAL WEB RIPPER
Visual Web Ripper is a powerful web page scraper used to easily extract website data, such as product catalogs, classifieds, financial web sites or any other web site that contains information you may Excel, MySQL db file, SQL Lite db file.
*	Data Extraction Using Visual Web Ripper and Recipes Script
Recipes Script generates out .rip file. In the script, we define the recipe model if present for the website. For script generation and execution of it according to requirements, we follow a specified schema that assists us in every step of data extraction and how we structure it during extraction for late use.First, we give it a template Page Area and save it,next we give it a Link that would help us continue to the next page and name them as “recipeCategoryList” and “recipeCategory” respectively. 

![image](https://user-images.githubusercontent.com/96038471/156801914-810e6114-98a8-4473-8c59-4e480db3592b.png)

For the next step, we take in a list of recipes in the template of Page Area and select all our recipes and will name it as “recipeList”. 

![image](https://user-images.githubusercontent.com/96038471/156802372-10aa788f-064b-4104-8011-a29afb958097.png)

After saving the same area as “recipes” we make a link of those selected items and give them the template of Link. 

![image](https://user-images.githubusercontent.com/96038471/156802496-38c87a00-c8c6-4b7c-8e14-5cdd8108a9df.png)

This list will help us open each recipe and is named as “recipe”. Once we have provided all the present content of the recipe constituents and gave them names according to the provided schema, we save the script and the file as a Visual Web Ripper Project (.rip). 

![image](https://user-images.githubusercontent.com/96038471/156802650-b932d834-ff9c-49ef-9f42-7fd6bc2cb15a.png)

Next comes the extraction. We will extract the website by running our project. It will take some time to get done. The time for extraction varies depending upon the size of the website.

![image](https://user-images.githubusercontent.com/96038471/156802705-cf5de3bf-8606-4c06-a723-d335d4d0221e.png)

![image](https://user-images.githubusercontent.com/96038471/156802734-16d6b533-0bd8-4fdd-999e-90204c7ee487.png)

![image](https://user-images.githubusercontent.com/96038471/156802799-046b6c72-4954-4431-b8b3-60b0a6f45ef0.png)

Extracting the website successfully isn’t the end of our work. After the extraction is done wgar we will do is that using its database file titled “internal.db”.

![image](https://user-images.githubusercontent.com/96038471/156802836-a43357ef-26f5-43d9-a43a-4b6d6aa4dce0.png)

We will use the extracted database file in SQLite studio to export a .sql file of our extracted data.  After some syntax changes which are five to be precise, to this .sql file, we upload it to our PHP server. 
After the file has been successfully uploaded, we move towards the next phase which will be Data Consolidation.

## b-	Recipe Schema and Naming Conventions
Throughout our journey of exploring recipes, we have come across various constituents of recipes, each of them enhancing their outlook and essence. The elements a recipe comprises, bestow a sense of soul to it. The core recipe constituents we have gathered so far and also mentioned in the provided schema are mentioned as follows:

## RECIPE MODELS
While exploring recipes, the models of recipes we see never remain consistent. Studying a wide range of models and inspecting those models side by side, I would like to mention the commonly occurring models below:
*	Recipes by Category
*	Recipes by Ingredients
*	Recipes by Regions
*	Recipes by Ethnicity
*	Recipes by Diet
*	Recipe by Cuisines
*	Recipes by Courses
*	Recipes by Occasions
*	Recipes by Time of Day
*	Recipes by Drinks
*	Recipe Desserts
*	Street Food
*	Recipes by Everyday Meals

## EXTRACTION CHALLENGES
The extraction process isn’t quite easy as it seems and we face several challenges throughout our journey. Some of these challenges are:
*	The recipe content in our browser doesn’t appear in ripper. 
*	An image has a different path than the others.
*	Even if the script is generated right, sometimes it may not appear in extraction.
*	Ingredients or Instructions appear in subheadings and those subheadings can only be selected as a single div.
*	An ad appears in the ripper and we can’t casually treat web pages on ripper like we do in the browser.

## SOLUTIONS TO EXTRACTION CHALLENGES
Let’s discuss solutions to the challenges we have been facing:
*	If the content of the web page doesn’t appear in the ripper, we review the “tree view” of the page and compare it with its inspect mode.
*	If an image has a different path, we inspect it in the browser and set its XPath manually.
*	If images can’t be picked on during extraction, we either select “link” from the list or select src in the “attributes” or do the content transformation.
*	To overcome the challenge of ingredients and instructions subheadings being in a single div we select list type “text”, add line breaks, and content transform it.
*	If we want to use ripper as we do in the browser, we select the option “navigate in the browser” option.

## LINKS TO OUR EXTRACTED WEBSITES

## 2-	Steps of Data Transformation
1)	Once the data has been successfully extracted, and exported, we convert the data into a SQL database file using SQLite Studio. The steps are as follows:
2)	Select the file named “internal_websitename”, which is database file from the output folder of the website’s Visual Web Ripper Project.
3)	Open SQLite Studio.
4)	Load the internal file into SQLite Studio using the add database option.
5)	Once Loaded, use the export database option to the same output folder as an SQL file of database with extension “.sql”.
6)	Once the .sql file of the project is successfully exported, we apply 5 changes in that SQL file to make it compatible and according to our data requirements of finalized database.
7)	The five changes are done by using Find and Replace option of Notepad. The five changes are as follows:
I.	Replace " with `
II.	Replace [ with `
III.	Replace ] with `
IV.	Replace nvarchar(4000) with text
V.	Replace guid with char(36)
VI.	Also, Comment PRAGMA BEGIN at start and at end.
8)	Once these changes are done, the data is successfully transformed into our desired SQL database, we upload it onto our SQL Server at the address: http://121.52.153.204/phpmyadmin/index.php

## 3-	Steps for Data Consolidation
After the recipe data of different websites has been extracted and transformed and uploaded to the server. We consolidate all the data by using MySQL scripts and MySQL Workbench to move and cleanse all the data from separate databases to one unified database (Group10). The steps involved are:
1)	Install and open MySQL Workbench.
2)	Setup a database connection using login credentials of the database server.
3)	Select the website database to use.
4)	If there are multiple parts of a website’s database, then they are merged before consolidation.
5)	Alter the recipe table by adding a column named “idid” after the “url” column.
6)	Fill the idid with recipe IDs using its ID from Extraction Sheet and filling the column in sequence using the format of ID+000000 and respective values onwards from 1,2,3….
7)	Create two tables named “temp” and “temp2” to separate duplicated and unique recipe records from recipe table. 
8)	The table “temp” will store the row_id and url of the recipes that are duplicated in the database (once or even more than one) and the table “temp” will store the row_id and url of the recipes that are unique and found only once in the recipe table of website’s database.
9)	After that, we take up all the attributes from the recipe table of website’s database and consolidate into the recipe table of the finalized database (Group10.Recipes) using its “idid” to uniquely identify each recipe and website it belongs to.
10)	After recipe table is successfully consolidated, we move on to consolidating other three tables (ingredients, instructions, nutrition).
11)	Using separate MySQL queries for subheadings and without subheadings we consolidate all the values (idid, source index, groupName, and recipeIngredient) of ingredients table of website’s database into ingredients table of the finalized database (Group10.Ingredients) using its “idid” as unique identifier.
12)	Just like ingredients, using separate MySQL queries for subheadings and without subheadings we consolidate all the values (idid, source index, howToStep, and recipeInstruction/step) of instructions table of website’s database into instructions table of the finalized database (Group10.Instructions) using its “idid” as unique identifier.
13)	Nutrition data is consolidated as same as the recipe table if they are extracted inside the recipe table and it is done because of different values of different nutrition present in it. We use a separate query if the nutrition is extracted as a separate table. 
14)	We consolidate all the values (idid, nutrition name) of nutrition table of website’s database into instructions table of the finalized database (Group10.Nutrition) using its “idid” as unique identifier.
15)	Once all the tables are filled, a website’s consolidation is completed. 

## 4-	Data Quality
The quality of the data is an important attribute that could drive the value of the data and hence, impact aspects of the outcome and popularize the website. So, we work on Recipe website's Database for regulatory compliance, customer satisfaction, or accuracy of decision making. We work on 4 main criteria used in 3 columns like recipeCategory, recipe Course and recipeCuisine in recipe table to measure the data quality.
Accuracy: For whatever data described, it needs to be accurate. Like spell mistake. 
Relevancy: The data should meet the requirements for the intended use. e.g; In recipeCuisine column, recipeCourse value add so it is not relevant then change using appropriate query.
Completeness: The data should not have missing values or miss data records. 
Consistency: The data should have the data format as expected and can be cross reference-able with the same results.



We apply queries on these 3 column for data quality. Some important queries that are:

Replace value in a column: 
UPDATE Table  SET Col1 = REPLACE(Col1,"Value","")

Replace value in one column to another column: 
UPDATE Table SET Col2=Col1 WHERE Col1 LIKE "%Value%"

Substring: 
UPDATE  Table SET Col2 = substring(Col1 ,position('Value' in Col1), length)

Substring + Concatenate: 
UPDATE Table SET Col2= CONCAT( Col2, substring(Col1,position('Value' IN Col1), length) ),Col1 = "" WHERE Col1 LIKE "%Value%"
















 
