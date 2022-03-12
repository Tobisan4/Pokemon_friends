# Pokemon_friends - Project 2 - Extract Load Transform


# Background

The power of ETL (Extract, Transform, Load)

Before any data analysis is done and trends and conclusions are established, there are the data sources. A data source that is easy to access, properly formatted and validated is a key to any analysis. ETL is a process that helps create that data source. As the name suggests, it Extracts data from different sources and Transforms them into digestable information before Loading them a repository that will be easy for any analyst to access. 


# Proposal


### Data Sources

We searched for topics that we are interested, in the end we chose two topics that we found in Kaggle [https://www.kaggle.com/](https://www.kaggle.com/). We selected a Pokemon themed dataset because of our familiarity with this particular segment. We also selected a Chick-Fil-A dataset, because were curious to learn about the nutritional portion of one of our favorite fast food chains.


ThiagoAZen. (February 2022). All Pokemon with stats, Version 1. Retrieved from [https://www.kaggle.com/thiagoazen/all-pokemon-with-stats/](https://www.kaggle.com/thiagoazen/all-pokemon-with-stats/)

Prasert Kanawattanachai. (March 2022). Chick-fil-A nutrition facts, Version 1. Retrieved from [https://www.kaggle.com/prasertk/chickfila-nutirtion-facts/](https://www.kaggle.com/prasertk/chickfila-nutirtion-facts/)


### Database 

The transformed data will be loaded to a Postgres relational database named: Pokemon_friends


### Comments And Findings

- Selecting the datasets was harder than we initially thought. Kaggle gave us a wide variety of options but we decided to select datasets that we know we could have fun with.

- The Pokemon dataset included a lot of different types of Pokemons and any variations that Pokemon may have. This created multiple entrees for certain Pokemons. We decided to focus only on the basic types of Pokemons.

- Pokemons can be grouped by types. All will have a primary type but some have a secondary type. In our analysis we plan to group each Pokemon to its primary type then group it by its secondary type if the information is available.

- The Chick-Fil-A datat set included menu items ranging from a packet of sauce, single serving items, gallon drinks and serving trays. In our analysis, we will only focus on single serving items.

- When loaded to a dataframe, the Chick-Fil-A dataset have different data types to what we felt were similar data columns. Our plan is to convert all the nutrition based values to float data type.


# Project Report


## Extract

### All Pokemon With Stats

We downloaded the [Pokemon data](Resources/PokemonDb.csv) as a csv file from Kaggle. The csv file was then read into a dataframe with the following data types.

    Column Name  Data Type
    Name         object
    Variation    object
    Type1        object
    Type2        object
    Total         int64
    HP            int64
    Attack        int64
    Defense       int64
    Sp.Atk        int64
    Sp.Def        int64
    Speed         int64


### Chick-Fil-A Nutrition Facts

We downloaded the [Chick-Fil-A data](Resources/chick-fil-a-nutrition.csv) as a csv file from Kaggle. The csv file was then read into a dataframe with the following data types.

    Column Name          Data Type
    Menu                  object
    Serving size          object
    Calories             float64
    Fat (G)              float64
    Sat. Fat (G)         float64
    Trans Fat (G)        float64
    Cholesterol (MG)       int64
    Sodium (MG)            int64
    Carbohydrates (G)      int64
    Fiber (G)              int64
    Sugar (G)              int64
    Protein (G)            int64


## Transform

### All Pokemon With Stats

These are the steps done to transform the data

1. Filtered the dataset to only include the basic types of Pokemons, any variation was removed
2. Removed the columns ("Variations" & "Total") that were not needed
3. Replaced any NaN data with a blank
4. Set the title case for the following data columns: "Name", "Type1", "Type2"
5. Grouped the Pokemons first by their Primary type classification ("Type1") then by their secondary type ("Type2")
6. Created and populated the "Total Attack" stats column (Total Attack = Attack + Sp.Atk)
7. Created and populated the "Total Defense" stats column (Total Defense = Defense + Sp.Def)
8. Reset the index column values

### Chick-Fil-A Nutrition Facts

These are the steps done to transform the data

1.Filtered the dataset to only include the single serving menu items, using the keywords below to remove unwanted items
    - Tray
    - Gallon
    - Bucket
    - 8oz
    - Ice Scoop
    - 96
    - Catering
    - Bag
2. Edit the "Serving Size" data column
    2.a. Remove the trailing "g" from each data row
    2.b. Rename column header from "Serving Size" to "Serving Size (G)"
3. Convert the data types of the following columns to float
    - Serving Size (G)
    - Cholesterol (MG)
    - Sodium (MG)
    - Carbohydrates (G)
    - Fiber (G)
    - Sugar (G)
    - Protein (G)
4. Set the title case for the "Menu" data column
5. Grouped the dataset first by calorie value ("Calories") then by serving size ("Serving Size (G)")
6. Reset the index column values


## Additional information 

For more information, please open the file [ETL Mapping document.xlsx](ETL Mapping document.xlsx)


## Load

### All Pokemon With Stats

After transformation the final dataframe had the following data structure

    Column Name      Data Type
    Name             object
    Type1            object
    Type2            object
    HP                int64
    Attack            int64
    Defense           int64
    Sp.Atk            int64
    Sp.Def            int64
    Speed             int64
    Total Attack      int64
    Total Defense     int64

The dataframe was then loaded to the Postgres database: Pokemon_friends, in the table: pokemon_data


### Chick-Fil-A Nutrition Facts

After transformation the final dataframee had the following data structure

    Column Name          Data Type
    Menu                  object
    Serving Size (G)     float64
    Calories             float64
    Fat (G)              float64
    Sat. Fat (G)         float64
    Trans Fat (G)        float64
    Cholesterol (MG)     float64
    Sodium (MG)          float64
    Carbohydrates (G)    float64
    Fiber (G)            float64
    Sugar (G)            float64
    Protein (G)          float64

The dataframe was then loaded to the Postgres database: Pokemon_friends, in the table: chick_fil_a

## Why These Topics

The main reason for picking these topics is that we were both intrigued by the datasets and also we thought it will be loads of fun to look into these information.

Pokemon is a popular toy/game for a lot of people, us included. It appeals to a wide range of age groups and a lot of people are playing Pokemon Go in their mobile devices. With this in mind, we set on reviewing the data and looking at the different types of Pokemons and stats for each one.

Chick-Fil-A is a popular fast food chain and serves a lot of meals in a daily basis. We were interested in finding out what are the nutritional information for the menu items we order from them.



# References

ThiagoAZen. (February 2022). All Pokemon with stats, Version 1. Retrieved from [https://www.kaggle.com/thiagoazen/all-pokemon-with-stats/](https://www.kaggle.com/thiagoazen/all-pokemon-with-stats/)

Prasert Kanawattanachai. (March 2022). Chick-fil-A nutrition facts, Version 1. Retrieved from [https://www.kaggle.com/prasertk/chickfila-nutirtion-facts/](https://www.kaggle.com/prasertk/chickfila-nutirtion-facts/)



