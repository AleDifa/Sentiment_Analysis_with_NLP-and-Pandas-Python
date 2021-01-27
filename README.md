# Data Analysis and Sentiment Analysis with nlp

The following representation extrapolates the essential components, to see the complete code in Python [clicca qui](https://github.com/AleDifa/Sentiment_Analysis_with_NLP-and-Pandas-Python/blob/main/Wine%20project.ipynb):small_blue_diamond:, otherwise you can see a representation in [google presentation](https://docs.google.com/presentation/d/15xcLOsAlaafO6LvSy9XRyjX7a-JPYaXHCRBXGUfrZLk/edit?usp=sharing):green_apple:

The focus of the project is how to interpret the data to choose the best product in the wine market to produce and the best text to be associated with the bottle for a good marketing impact. To understand the best product we will rely on data analysis, while to understand which are the most captivating words to use we will rely on NLP techniques.
<br>

### Wine Project
1) Cleaning dataset
2) Create Visualization data
3) Sentiment Analysis use method Natural Language Processing for analyze text 
4) Conclusion


#### Cleaning Data

```python
df.drop_duplicates("description", keep=False, inplace=True)
df.dropna(subset=["designation","price"], inplace=True)
```

Delete white space
```python
white_space=[]
for a in df.itertuples():
    if type(a) == str:
        if a.isspace():
            blanks.append(a)
```

check outlayer
<img width="280" alt="Capture1" src="https://user-images.githubusercontent.com/37181764/105983230-b3a28480-6098-11eb-94fe-25c29d21ddab.PNG">
