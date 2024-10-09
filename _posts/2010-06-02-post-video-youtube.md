---
title: "EDGAR Poetry Bot"
categories:
  - Post Formats
tags:
  - Post Formats
last_modified_at: 2018-02-01T12:54:35-05:00
---
# EDGAR - Poetry Chatbot

A simple intent-driven NLP ChatBot that provides poems based on the user's emotions and also allows users to add emotions with corresponding poetry, line by line. These new, added poems can then be accessed in the future by expressing the emotion that corresponds with them. 

You can use it here (Gmail account required): [EDGAR, The Poetry Bot](https://colab.research.google.com/drive/1tPSSPTP4n-p-GKTKaz8RkV04kJQtW5ly?usp=sharing)

To begin:
1.  Click "Runtime" in the toolbar above.
2.  Click "Run all"

Tell it how you feel (ex. I feel sad, I feel joy) to recieve a poem that'll fit the mood.
Feel free to add new poems. He'll tell you how!

If you get sick of him at any time, say "quit"

And chat away! :)

The final poetry dataset including your changes will be automatically downloaded to the browser at the end. Feel free to not save it.

## Getting Started - Get a Personal Poetry Chatbot!

You can either run this in your Google Colab notebook (suggested) or locally as a Python file.

## Prerequisites - Google Colab

Download the EDGARPoemsChatbot.ipynb file and upload it into your Google Colab notebook. 
Save the PoetryIntents1234.json file into your own github or Google Drive.

In the first code chunk of the EDGARPoemsChatbot.ipynb file, adjust 'file_path' to be the path to your copy of the PoetryIntents1234.json file.

```
file_path = 'https://raw.githubusercontent.com/alvs210/PoetryChatter/main/PoetryIntents1234.json'
```
If you saved the file in your github, then simply replace the present URL with the URL to the file in your github.

If you saved the file in your Google Drive, this requires you to mount your Google Drive and direct a path to the file through your Google Drive.
To mount your Google Drive, add this code chunk:
```
from google.colab import drive
drive.mount('/content/drive')
```
Then replace the file_path with the path to the PoetryIntents1234.json file in your Drive. The code below should help!
```
from google.colab import files
uploaded = files.upload()

import json
with open('your_file_name.json', 'r') as f:
  data = json.load(f)
```
## Prerequisites - Local File

Download the .py file and the PoetryIntents1234.json file. You will need to adjust the code, as we did for the Google Colab file, to import and read the PoetryIntents1234.json file. Ensure both files are in the same current directory.

You'll also need the followng installations!

```
install nltk
install tensorflow as tf
install json
install numpy as np
install pandas as pd
install pickle
install random

```

## Data Pre-Processing

I downloaded [this](https://commons.datacite.org/doi.org/10.17632/n9vbc8g9cx.1) poetry dataset with various poems organized based on the 'Navarasa' emotion classification system, which consists of nine primary emotions such as Love, Sad, Anger, Hate, Fear, Surprise, Courage, Joy, and Peace. I continued to add more emotions as I interacted with EDGAR.

I first cleaned the data through the simple and basic CleanData.py, which got rid of NaN values, removed the first row that is a header, and then separated the poems and their emotions into two columns, one for poems one for emotions.

I then passed the cleaned dataset into IntentsCreator.py, which is uses the intents/patterns/responses framework for NLP processing.
  This framework consists of 
- "intents," which represent to a goal or objective the user wants to achieve (in our case, it corresponds to an emotion);
- "patterns," which are examples or phrases that can be matched to a particular intent and indicate the intent of the user's input (indicates emotion)
- "responses," which are a pool of potential responses the Chatbot can choose from; each intent has its own pool of responses (poems for each emotion)

## Future Improvements

- Implement a continuation of conversation after a poem is provided (ex. give me a sadder poem)
- Search for a poem based on a word from that poem, author, etc.
- Organize and find poems according to their rhythm, length, and more

## Acknowledgments

This project would not be possible without:
- [A Simple Chatbot by Vedro](https://github.com/vedrosuwandi/ChatBot)
- [Medium Article](https://handsonai.medium.com/build-a-chat-bot-from-scratch-using-python-and-tensorflow-fd189bcfae45)
- [A Very In-Depth Tutorial](https://pythonprogramming.net/chatbot-deep-learning-python-tensorflow/#google_vignette) that I didn't end up using but was very fun to read
- And Gemini and ChatGPT used for debugging, code evaluation, etc.!
