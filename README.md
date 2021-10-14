# data-512-a2
*README file for 512hw2 (short reflection included)*
---

### Introduction <br>
The goal of this assignment is to explore the concept of bias through data on Wikipedia articles - specifically, articles on political figures from a variety of countries. In particular, we're interested in the following information:
- the countries with the greatest and least coverage of politicians on Wikipedia compared to their population.
- the countries with the highest and lowest proportion of high quality articles about politicians.
- a ranking of geographic regions by articles-per-person and proportion of high quality articles.

### Data Source and Information <br>
There are two initial data files downloaded in csv format:<br>
- The Wikipedia politicians by country dataset called 'page_data.csv'. (https://figshare.com/articles/dataset/Untitled_Item/5513449)
  - Three columns in this data are used in this project
    - 'page' - the article name
    - 'country' - the politician's country
    - 'rev_id' - the revision id for the wikipedia page
- The population data is available in CSV format as 'WPDS_2020_data.csv'. (https://docs.google.com/spreadsheets/d/1CFJO2zna2No5KqNm9rPK5PCACoXKzb-nycJFhV689Iw/edit)
  - Three columns in this data are used in this project
    - 'Name' - country or region name
    - 'Type' - includes three fields (world, sub_region or country) that represent the type of the name column
    - 'Population' - the population for the world, country or region

There are also two additional data files generated through this assignment:<br>
- 'wp_wpds_countries-no_match.csv'
  - When merging the wikipedia politicians by country dataset and the population data, the population data sometimes doesn't have an entry for the correspondnig wikipedia page (or vice versa).
  - Some entries in the population data doesn't correspond to countries, but subregions or the whole world.
- 'wp_wpds_politicians_by_country.csv'
  - The result of successfully merged dataset.
  - There are five columns in this dataset
    - 'article_name' - the article name
    - 'country' - the politician's country
    - 'revision_id' - the revision id for the wikipedia page (same as the rev_id in the initial data file)
    - 'article_quality_est.' - the prediction score (if available) gathered by using the ORES machine learning system
    - 'population' - population of the country

### Analysis Steps <br>
The detailed data cleaning and analysis steps are included in the jupyter notebook 'hcds-a2-bias.ipynb'.<br>
There is a list of articles for which I was not able to gather ORES scores. I included the log in the notebook as well.

### Analysis Results & Reflection <br>
For this relection, I firstly want to talk about some of the practices I learnt on improving reproducibility. We had an in-class activity discussing the reproducibility of data science proejects, and our group was able to find many potential improvements. I attempted to install some of these improvements during this assignment. For example, I included the complete data files and their sources, keeped all the necessary comments along the way, and wrote an in-detail README file. I was surprised to find that this level of documentation actually helped me check my own work and made me work more efficient. One additional thing I noticed during this project is that the variable names should be appropiate. For instance, there are a lot of intermediate dataframes during the analysis (by_country and by_region). It's so easy to lose track of what you're working on or make mistakes if you don't name the variables carefully. <br>
Now I want to discuss the results and the biases. Since we're using the data of English wikipedia for this project, I expected the score predictions for English-speaking countries/regions are higher than non-English-speaking countries/regions, thus resulting in a higher percentage of 'FA' or 'GA' quality articles. After seeing the results, however, I was shocked that north korea, saudi arabia and romania are ranked the top 3 countries with the highest percentage of high-quality articles. It is probably due to the fact that there are very few politician articles in those countries and these articles happen to be high-quality. In addition, I found that the article proportion (article count/population*100) is not a good metric for politician coverage since countries with large populations like india and china would be ranked among the bottom natrually. Those bottom ten countries are also non-English speaking countries as well. <br>
This suggests that when using English wikipedia as a data source, we need to recognize the exsiting bias and adjust for it. For instance, if we want to evaluate the politician coverage on wikipedia, we should include other language source as well and take the population factor into consideration.


