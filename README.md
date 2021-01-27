# Data Analysis and Sentiment Analysis with nlp

The following representation extrapolates the essential components, to see the complete code in Python [click me!](https://github.com/AleDifa/Sentiment_Analysis_with_NLP-and-Pandas-Python/blob/main/Data%20Analysis%20and%20Sentiment%20Analysis%20with%20nlp%20-%20Wine%20project.ipynb):small_blue_diamond:, otherwise you can see a representation in [google presentation](https://docs.google.com/presentation/d/15xcLOsAlaafO6LvSy9XRyjX7a-JPYaXHCRBXGUfrZLk/edit?usp=sharing):green_apple:

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
<br>
check outlayer 
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


#### Sentiment Analysis use method Natural Language Processing for analyze text 

import Spicy Library and load English language
```python
import spacy
from nltk.corpus import stopwords
from nltk.sentiment.vader import SentimentIntensityAnalyzer
nlp = spacy.load('en')
sid = SentimentIntensityAnalyzer()
```
<br>
New column with polarity for each row in descrption column
```python
Best_5_points["scores"] = Best_5_points["description"].apply(lambda description: sid.polarity_scores(description))
```
<img width="384" alt="Capture10" src="https://user-images.githubusercontent.com/37181764/105986714-915f3580-609d-11eb-8568-a63c7f8fc006.PNG">


we have create new column with compund, comp_score and rating, let's create tokenized_sents
```python
from nltk.tokenize import word_tokenize
Best_5_points['tokenized_sents'] = Best_5_points.apply(lambda row: nltk.word_tokenize(row['description']), axis=1)
```
<img width="446" alt="Capture11" src="https://user-images.githubusercontent.com/37181764/105987481-a12b4980-609e-11eb-893b-b1ef57bc5185.PNG">

Generate WordCloud from the best  wine Tokenizations

<img width="350" alt="Capture12" src="https://user-images.githubusercontent.com/37181764/105988404-da17ee00-609f-11eb-82e4-b2b456f0606d.PNG">

Count the occurency

```python
cnt = Counter()
for word in total_5_wine_description:
    cnt[word] +=1
cnt.most_common()
```

<img width="114" alt="Capture13" src="https://user-images.githubusercontent.com/37181764/105988754-6b876000-60a0-11eb-8d62-afe9cbc3b8a9.PNG">

#### Conclusion

>Where to Focus new Investment?<br>
For the market The Pinot Noir by WIlliam Selyem have the best Quality and the lowest Price!, the most wines came from to Us and the Italian wines have the highest positive scores in the market. For the wine description we can consulting the most common words reported by the highest points wines and the most commons words by the 5 best wine. 


<img width="567" alt="index" src="https://user-images.githubusercontent.com/37181764/105993314-8957c380-60a6-11eb-9ba1-f35cacded2c7.png">

