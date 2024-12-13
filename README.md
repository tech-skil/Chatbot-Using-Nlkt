Certainly! Below is a detailed README file for your GitHub repository, covering the code you provided and its usage.

---

# Chatbot Using nlkt 

## Overview

This repository contains the implementation of **TriploChatbot**, a natural language processing (NLP)-based chatbot built using deep learning and the Keras framework. The chatbot is designed to predict responses to user input based on predefined intents and trained machine learning models. It uses techniques like tokenization, lemmatization, and bag-of-words to understand and respond to text input effectively.

The code integrates a trained machine learning model, NLTK (Natural Language Toolkit) for text processing, and the TensorFlow Keras framework to create a deep learning-based response system. The chatbot can also fetch additional information about specific places, such as overviews, historical significance, and other details, based on the user’s queries.

## Features

- **Intent Prediction**: The chatbot predicts user intents based on input text and provides a response accordingly.
- **Place Information Retrieval**: The chatbot can provide detailed overviews and historical information for specific places (from a given `intents.json` file).
- **Pretrained Model**: The chatbot uses a pretrained Keras model (`TriploChatbot.h5`) to predict responses for user inputs.
- **NLTK Integration**: The chatbot leverages NLTK for tokenization, lemmatization, and text preprocessing.

## Structure

The repository includes the following key files:

- **`triplo_chatbot.py`**: Main Python script that loads the model, processes input, and provides responses based on predicted intent.
- **`intents.json`**: JSON file containing predefined intents and responses for the chatbot.
- **`words.pkl`**: Pickled list of words from the training data used to create the bag-of-words representation.
- **`classes.pkl`**: Pickled list of classes (intents) used for predicting intent classes.
- **`TriploChatbot.h5`**: Pretrained Keras model file for intent prediction.
- **`pretraining.py`**: Script for training the model using data from the intents file and generating a pretrained model.

---

## Installation

To use this chatbot, follow these steps:

### 1. Clone the Repository

```bash
git clone https://github.com/tech-skil/Chatbot-Using-Nlkt
cd Chatbot-using-NLKT
```

### 2. Install Dependencies

Make sure you have Python installed (preferably Python 3.x). Install the required Python packages using `pip`.

```bash
pip install -r requirements.txt
```

The required libraries include:
- `nltk`
- `tensorflow`
- `numpy`
- `scikit-learn`
- `pickle`

### 3. Download NLTK Data

The script uses NLTK's word tokenizer and lemmatizer. The required NLTK data (like the Punkt tokenizer) will be automatically downloaded when you run the script.

```python
import nltk
nltk.download('punkt')
```

---

## Usage

### 1. Pretraining the Model

The `pretraining.py` script is responsible for training the model using your dataset. If you don't already have a pretrained model (`TriploChatbot.h5`), follow these steps to train one.

Run the `pretraining.py` script to create a trained model based on the intents from `intents.json`.

```bash
python pretraining.py
```

This script:
- Loads the intents from `intents.json`.
- Processes the data (tokenizes, lemmatizes, and creates a bag of words).
- Trains a deep learning model (using TensorFlow and Keras).
- Saves the trained model (`TriploChatbot.h5`) to disk.

### 2. Running the Chatbot

To start chatting with the bot, run the `triplo_chatbot.py` script.

```bash
python triplo_chatbot.py
```

You can interact with the bot by typing messages. The bot will predict the intent of your message and respond accordingly. If the bot recognizes a place (e.g., "Tell me about Paris"), it will retrieve detailed information about that place from the `intents.json` file.

To exit the chatbot, type `exit`, `quit`, or `bye`.

---

## Code Breakdown

### Key Functions

1. **`clean_up_sentence(sentence)`**
   - Tokenizes and lemmatizes the input sentence to standardize the text before processing.

2. **`bag_of_words(sentence)`**
   - Converts the input sentence into a bag-of-words representation, where each word is matched to a corresponding position in the vocabulary list (`words.pkl`).

3. **`predict_class(sentence)`**
   - Uses the trained model (`TriploChatbot.h5`) to predict the intent of the input sentence. It returns the predicted intent and its associated probability.

4. **`get_overview(place_name, intents_json)`**
   - Fetches an overview of a place based on the intent of the message. This function extracts details such as the purpose of the visit and historical significance from the `intents.json` file.

5. **`extract_place_name(message)`**
   - Extracts a place name from the user’s query using regular expressions.

6. **`get_response(intents_list, intents_json, message)`**
   - Fetches the appropriate response based on the predicted intent. If the intent is related to a place, it fetches information about the place. Otherwise, it returns a response from the predefined set of responses.

---

## Example Interaction

**User:** `Tell me about the Eiffel Tower`

**Bot:** `Here is what I know about Eiffel Tower:
- Purpose of Visit: Tourist attraction
- Historical Significance: Landmark of France, built in 1889
- Summary: The Eiffel Tower is a wrought-iron lattice tower on the Champ de Mars in Paris, France.`

---

## Intent and Data Structure

The `intents.json` file contains various intents and their corresponding responses. It follows this structure:

```json
{
  "information_model": {
    "topics": [
      {
        "name": "eiffel tower",
        "details": {
          "overview": {
            "purpose_of_visit": "Tourist attraction",
            "historical_significance": "Landmark of France, built in 1889",
            "summary": "The Eiffel Tower is a wrought-iron lattice tower on the Champ de Mars in Paris, France."
          }
        }
      }
    ]
  },
  "intents": [
    {
      "intent": "greeting",
      "responses": [
        "Hello!",
        "Hi there!",
        "Good day!"
      ]
    },
    {
      "intent": "ask_about_place",
      "responses": [
        "Tell me more about this place.",
        "What can you tell me about this place?"
      ]
    }
  ]
}
```

---

## Contributing

Contributions are welcome! If you would like to improve this project, please fork the repository, create a new branch, and submit a pull request with your changes.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- TensorFlow/Keras for building the machine learning model.
- NLTK for natural language processing tools.
- All contributors and developers of open-source libraries.

---

This README should serve as a helpful guide to using and understanding the Triplo Chatbot.
