# Next Word Prediction

A Streamlit application that predicts the next word in a text sequence using a trained LSTM model. The model was trained on Shakespeare's *Hamlet* text and uses early stopping during training.

## Features

- Accepts a sequence of words as input.
- Uses an LSTM neural network to predict the next word.
- Loads a saved Keras model and tokenizer at startup.
- Provides predictions through a simple Streamlit interface.

## Project Files

- `app.py` - Streamlit application and prediction logic.
- `next_word_lstm.h5` - Trained LSTM model.
- `tokenizer.pickle` - Tokenizer used to convert words into model input sequences.
- `hamlet.txt` - Text used as the training corpus.
- `experiments.ipynb` - Notebook containing the data preparation and model experiments.

## Requirements

Use Python 3. The shared project dependency file is located one directory above this folder:

```bash
pip install -r ../requirements.txt
```

The main packages used by the application are TensorFlow, NumPy, and Streamlit.

## Run the App

From this directory, run:

```bash
streamlit run app.py
```

Streamlit will display a local URL in the terminal. Open that URL in a browser, enter a phrase, and click **Predict Next Word**.

The default example is:

```text
Fran. You come most
```

## How It Works

1. The input text is converted into token IDs using `tokenizer.pickle`.
2. The sequence is padded to the length expected by the LSTM model.
3. The model calculates probabilities for the next word.
4. The word with the highest predicted probability is displayed.

For longer input, the application keeps the most recent words so the sequence fits the model's expected input length.

## Notes

- Run the application from the `Predicting Next Word` directory so the model and tokenizer files can be found.
- The prediction quality depends on the training corpus and vocabulary. Since the model was trained on *Hamlet*, it performs best on text resembling that corpus.
- The saved model and tokenizer must remain in the same directory as `app.py`.
