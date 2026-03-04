# SMS Spam Classifier

A machine learning-based web application that classifies SMS messages as spam or legitimate (ham) using Naive Bayes classification.

## Features

- **Real-time SMS Classification**: Input any message and get instant spam/ham predictions
- **High Accuracy**: 95.9% accuracy on test dataset
- **Simple Web Interface**: User-friendly Streamlit application
- **TF-IDF Vectorization**: Advanced text preprocessing and feature extraction
- **Text Preprocessing**: Includes tokenization, stopword removal, stemming, and special character handling

## Tech Stack

- **Machine Learning**: Scikit-learn (MultinomialNB, TF-IDF)
- **Web Framework**: Streamlit
- **NLP**: NLTK (Natural Language Toolkit)
- **Data Processing**: Pandas, NumPy
- **Language**: Python 3.13

## Project Structure

```

sms-spam-classification/
   ├── app.py                      # Streamlit web application
   ├── spam-detection.ipynb        # Full training and evaluation notebook
   ├── spam.csv                    # Dataset (5,574 SMS messages)
   ├── model.pkl                   # Trained Naive Bayes model
   ├── vectorizer.pkl              # TF-IDF vectorizer
   ├── requirements.txt            # Python dependencies
   ├── .gitignore
   └── README.md                   # This file
```

## Installation

### Prerequisites
- Python 3.13+
- pip (Python package manager)

### Setup

1. **Clone or download the repository**
   ```bash
   cd sms-spam-classifier/sms-spam-classification
   ```

2. **Create virtual environment**
   ```bash
   python -m venv .venv
   .venv\Scripts\Activate.ps1  # On Windows PowerShell
   # or
   source .venv/bin/activate   # On Linux/Mac
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## Usage

### Running the Web Application

```bash
streamlit run app.py
```

The application will open in your browser at `http://localhost:8501`

### Using the Classifier

1. Enter an SMS message in the text area
2. Click the **Predict** button
3. View the classification result:
   - **Spam**: The message is likely spam
   - **Not Spam**: The message is legitimate (ham)

## Model Details

### Dataset
- **Source**: UCI Machine Learning Repository
- **Size**: 5,574 SMS messages
- **Classes**: 
  - Ham (legitimate): ~4,825 messages (86.6%)
  - Spam: ~747 messages (13.4%)

### Training Pipeline

1. **Data Preprocessing**:
   - Lowercase conversion
   - Tokenization using NLTK
   - Special character removal
   - Stopword removal
   - Stemming (Porter Stemmer)

2. **Feature Extraction**:
   - TF-IDF (Term Frequency-Inverse Document Frequency) vectorization
   - Converts text to numerical features

3. **Classification**:
   - MultinomialNB (Multinomial Naive Bayes)
   - Trained on 80% of data
   - Tested on 20% of data

### Performance Metrics

| Metric | Score |
|--------|-------|
| Accuracy | 95.94% |
| Precision | 100.0% |
| Confusion Matrix | [[896, 0], [42, 96]] |

## File Descriptions

### app.py
Streamlit web application that loads the trained model and vectorizer, handles user input, preprocesses text, and displays predictions.

### spam-detection.ipynb
Jupyter notebook containing:
- Exploratory Data Analysis (EDA)
- Data preprocessing and cleaning
- Model training and evaluation
- Visualization of spam vs ham characteristics
- Model persistence (pickle files)

### model.pkl
Serialized trained MultinomialNB model ready for predictions.

### vectorizer.pkl
Serialized TF-IDF vectorizer for text transformation.

## Requirements

Key dependencies:
- streamlit
- scikit-learn
- nltk
- pandas
- numpy

See `requirements.txt` for complete list.

## How It Works

1. **Input Text**: User enters an SMS message
2. **Preprocessing**: Text is converted to lowercase, tokenized, stopwords removed, and stemmed
3. **Vectorization**: Processed text is converted to TF-IDF features using the trained vectorizer
4. **Prediction**: The trained model predicts if the message is spam (1) or ham (0)
5. **Output**: Result is displayed as "Spam" or "Not Spam"

## Model Training

To retrain the model with new data:

1. Update `spam.csv` with new messages
2. Open `spam-detection.ipynb`
3. Run all cells in sequence
4. The pickle files will be updated automatically

## Limitations

- Works best for English SMS messages
- Limited to the patterns in the training data
- May not detect novel spam techniques effectively
- Best results for typical SMS-length messages

## Future Improvements

- Multi-language support
- Deep learning models (LSTM, BERT)
- Real-time model retraining
- More advanced feature engineering
- Integration with messaging platforms

## Author

Pavan

## License

Open source - Feel free to use and modify as needed.

## Acknowledgments

- Dataset from UCI Machine Learning Repository
- NLTK for NLP tools
- Scikit-learn for machine learning
- Streamlit for the web framework
