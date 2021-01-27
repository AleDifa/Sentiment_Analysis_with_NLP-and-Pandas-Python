# Data Analysis and Sentiment Analysis with nlp

The following representation extrapolates the essential components, to see the complete code in Python [clicca qui](https://github.com/AleDifa/Sentiment_Analysis_with_NLP-and-Pandas-Python/blob/main/Wine%20project.ipynb):small_blue_diamond:, otherwise you can see a representation in [google presentation](https://docs.google.com/presentation/d/15xcLOsAlaafO6LvSy9XRyjX7a-JPYaXHCRBXGUfrZLk/edit?usp=sharing):green_apple:

The focus of the project is how to interpret the data to choose the best product in the wine market to produce and the best text to be associated with the bottle for a good marketing impact. To understand the best product we will rely on data analysis, while to understand which are the most captivating words to use we will rely on NLP techniques.
<br>

### Wine Project
1) Cleaning dataset
2) Create Visualization data
3) Sentiment Analysis use method Natural Language Processing for analyze text 
4) Conclusion


df.drop_duplicates("description", keep=False, inplace=True)
df.dropna(subset=["designation","price"], inplace=True)

check outlayer
