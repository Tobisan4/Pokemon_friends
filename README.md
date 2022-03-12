### Pokemon_friends - Project 2 - Extract Load Transform

### Background

The power of ETL (Extract, Transform, Load)

Before any data analysis is done and trends and conclusions are established, there are the data sources. A data source that is easy to access, properly formatted and validated is a key to any analysis. ETL is a process that helps create that data source. As the name suggests, it Extracts data from different sources and Transforms them into digestable information before Loading them a repository that will be easy for any analyst to access. 

### Proposal

# Data Sources

We searched for topics that we are interested, in the end we chose two topics that we found in Kaggle [https://www.kaggle.com/](https://www.kaggle.com/). We selected a Pokemon themed dataset because of our familiarity with this particular segment. We also selected a Chick-Fil-A dataset, because were curious to learn about the nutritional portion of one of our favorite fast food chains.


ThiagoAZen. (February 2022). All Pokemon with stats, Version 1. Retrieved from [https://www.kaggle.com/thiagoazen/all-pokemon-with-stats/](https://www.kaggle.com/thiagoazen/all-pokemon-with-stats/)

Prasert Kanawattanachai. (March 2022). Chick-fil-A nutrition facts, Version 1. Retrieved from [https://www.kaggle.com/prasertk/chickfila-nutirtion-facts/](https://www.kaggle.com/prasertk/chickfila-nutirtion-facts/)

# Database 

The transformed data will be loaded to a Postgres relational database named: Pokemon_friends

# Comments And Findings

- The first comments we can make was it was 



### Project Report

### All Pokemon With Stats

Who doesn't like Pokemons? For this project we downloaded the [Pokemon data](PokemonDb.csv) from Kaggle. Focusing only on the basic type of Pokemons, we filtered out any variations of any Pokemon in the data set. The data was sorted using the Pokemon type categories, first by the Primary type (Type1) then by the Secondary type (Type2). Two new columns were then added, the Total Offensive and Total Defensive numbers which were calculated based on each Pokemon's stats. Additional steps like setting the title case for the Name, Type1 and Type2 columns, and formatting non numerical entrees were also done for better data presentation. The final step was loading it to the database, Pokemon_friends, for storage.
 
### Chick-Fil-A Nutrition Facts

Which Pokemon player doesn't like chicken?! As the second data set for the project, we downloaded the [Chick-Fil-A data](chick-fil-a-nutrition.csv) also from Kaggle. This time, we decided to limit our scope to items in the menu meant for single servings. The first process was filtering out large order sizes, using keywords like but not limited to; Tray, Gallon, Bucket, Catering and Bag to identify and remove these items from the data set. The next step was making our data types of our target columns consistent. This being about nutrition information, our data dealt with numbers. We had to transform most columns to "float" data type for consistency and also as a consideration for any downstream process dealing with numbers. The source column "Serving Size" was particluarly more challenging as each row data included a trailing letter "g" as a reference to grams. An additional step of removing the letter was done for each row before the data type was converted to "float". Additional steps like setting the title case for the Menu column was done for better data presentation. The final step was loading it to the database, Pokemon_friends, for storage.

## References

ThiagoAZen. (February 2022). All Pokemon with stats, Version 1. Retrieved from [https://www.kaggle.com/thiagoazen/all-pokemon-with-stats/](https://www.kaggle.com/thiagoazen/all-pokemon-with-stats/)

Prasert Kanawattanachai. (March 2022). Chick-fil-A nutrition facts, Version 1. Retrieved from [https://www.kaggle.com/prasertk/chickfila-nutirtion-facts/](https://www.kaggle.com/prasertk/chickfila-nutirtion-facts/)



