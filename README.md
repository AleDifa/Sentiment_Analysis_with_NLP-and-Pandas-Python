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
<img width="735" alt="Capture3" src="https://user-images.githubusercontent.com/37181764/105983807-8dc9af80-6099-11eb-8041-df055c37152c.PNG">

check outlayer <br>
<img width="517" alt="Capture1" src="https://user-images.githubusercontent.com/37181764/105984223-19434080-609a-11eb-9380-0ceef266d3fd.PNG">

#### Create Visualization
```python
df["variety"].value_counts().head().plot(kind="bar")
df["country"].value_counts().head().plot(kind="bar")
```
Relation about selling count by wine variety and country with more production 
<img width="534" alt="Capture6" src="https://user-images.githubusercontent.com/37181764/105985304-96bb8080-609b-11eb-8001-6dbbe5440a37.PNG">
<br>

```python
df.loc[df['price'].idxmax()]
df.loc[df['points'].idxmax()]

largest_five=df.nlargest(5, ['price'])
ax = sn.barplot(x="wine and winery", y="price" ,data=largest_five)
# rortate x label , problem to rotate the name not fit the bar 
ax.set_xticklabels(ax.get_xticklabels(),rotation=90)
ax.set_title("Relation price for wine")
```
<br>
Relation about Wine Winery and Points, at left we have the wine with more Points and the wine with higghest price  

<img width="647" alt="Capture9" src="https://user-images.githubusercontent.com/37181764/105985751-324cf100-609c-11eb-9cd1-e55ca83b6d0a.PNG">
