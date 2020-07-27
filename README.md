# Movies-ETL

## Introduction
In this module we learned about **Extract, Transform and Load** also known as ***ETL*** in order to prepare clean datasets of movie data. The datasets will then be used for a hackathon in which participants will predict the popular pictures with the information provided. 

Britta, who is a member of the Amazing Prime Video team has been tasked with creating the datasets for the hackathon. 

There are two data sources:
    1. A scrape of Wikipedia for all movies released since 1990.
    2. Rating data from the Movie Lens website.

## Extract
The first step was to extract data from the two sources. The scraped Wikipedia data was stored as a JSON and the Kaggle data stored in CSVs.

## Transform
After the data is extracted, it needs to be transformed. In order to do this, the data may need to be filtered, parsed, translated, sorted, interpolated, pivoted, summarized, aggregated, merged, etc. 

INSPECT-> PLAN -> EXECUTE

    We inspected the Wikipedia and Kaggle Data by using similar steps. 
    1. First used head(), this allowed us to inspect rows of data but also told us the shape of our DataFrame. The initial DataFrame contained 193 columns!
    2. Then we used list comprehension to filter out bad data. 
    3. After, we created two functions to clean the data. 
    4. The next step involved removing duplicates and null columns.
    5. We then converted and parsed the data. 
        a. We used regular expressions to search pattern.
        b. Then parsed the data by creating two forms.

### Merging Data
The last step before loading the data is to merge the clean Wikipedia and Kaggle data. This created redundant information which we had to analyze and make assumptions in order remove the disposable information.

### Assumption #1- Runtime
Both Wikipedia and Kaggle have runtimes, however after plotting the data we noticed Wikipedia data had some outliers, therefore the Kaggle data was a better choice to keep.

### Assumption #2- Budget
Budge column was also a duplicate for Wikipedia and Kaggle. The data was plotted again and the Wikipedia data appeared to have more outliers, therefore we kept Kaggle but still used Wikipedia data to fill in the gaps for any Kaggle data with no data. 

### Assumption #3- Box Office
This data was also numeric, so plotting the data helped us analyze the data and determine a resulution. In this case, we had the same results as we did for the budget, therefore we kept Kaggle data, and used Wikipedia data to fill in any zeros in the Kaggle data. 

### Assumption #4- Language
To determine which language column to use, we compared the counts of each, and then reviewed the data. The Wikipedia data had more information about multiple languages, but the Kaggle data was already consistent and in usable format, therefore the Wikipedia was dropped. 

### Assumption #5- Production Companies
By looking at a small sample, we were able to determine that Kaggle data was more consistent. Also, Wikipedia data would be too difficult to translate, therefore we kept Kaggle and dropped Wikipedia.

### Transform and Merge Rating Data
Britta wanted to include the rating data with the movie data, therefore she reduced the ratings data to a useful summary of rating information for each movie, and added it to the dataset available to the hackathon participants. 

## Load the data
Finally, in order to load the data we connected Pandas and SQL by creating a database, importing modules, creating a database engine and importing the Movie and Rating Data. 





