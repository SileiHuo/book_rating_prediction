# Book Rating Prediction

## Project Background
Explore NLP and Classification models to predict book rating (high/low) based on:
- Book Description (Text Data)
- Book Author (Author Average Rating - Numeric Data)
- Book Publisher (Top Publisher Name - One Hot Encoding on Publisher Catergory)

## Dataset
**Dataset source**: [USCD Book Graph](https://sites.google.com/eng.ucsd.edu/ucsdbookgraph/home)

## Data Preprocessing
**Text Preprocessing** - Please refer to Notebook1

Clean the Description Text Data, steps inlcuding:
- Check text data column impurity
- Remove HTML/RegExp Tags using regexpression cleaning by importing re
```python
import re

CLEANR = re.compile('<.*?>|&([a-z0-9]+|#[0-9]{1,6}|#x[0-9a-f]{1,6});')

def cleantext(text):
    cleantext = re.sub(CLEANR, ' ', text)
    return cleantext
```
- Remove newline/whitespace tags
```python
# define functin of removing slashn
def remove_slashn(text):
    # remove the '\n' in sentence
    text = text.replace('\n', ' ')
    
    return text
```
- Adjust double dashes, remove punctuations and numbers

```python
# define function

def remove_punct_number(sentence):
    # replace double dash
    sentence = sentence.replace('--', '- -')
    # remove digits
    sentence = re.sub(r'\d+', '', sentence)
    
    for punctuation_mark in string.punctuation:
        sentence = sentence.replace(punctuation_mark,'')
    
    return sentence
```
- Using fasttext to detect English language

```python
# define the language detect 

def fasttext_language_predict(text, model = language_model):
    text = str(text).replace("\n", " ")
    prediction = model.predict([text])
    
    return str(prediction[0])[12:14]
```

**


