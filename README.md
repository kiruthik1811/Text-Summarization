Text Summarization Project
📌 Overview
This project implements Text Summarization using both Extractive and Abstractive approaches. It leverages LexRank for extractive summarization and BART (facebook/bart-large-cnn) for abstractive summarization. The aim is to generate concise summaries while preserving the key meaning of the original text.

🚀 Features
Extractive Summarization using sumy (LexRank algorithm).

Abstractive Summarization using Hugging Face Transformers (BART model).

Preprocessing with nltk and spacy.

Easy-to-use Python functions with example outputs.

🔧 Installation & Setup
1. Clone the Repository
bash
Copy
Edit
git clone https://github.com/kiruthik1811/Text-Summarization
cd Text-Summarization
2. Install Dependencies
bash
Copy
Edit
pip install -r requirements.txt
Or install manually:

bash
Copy
Edit
pip install nltk spacy transformers sumy
python -m spacy download en_core_web_sm
3. Download Required NLTK Data
python
Copy
Edit
import nltk
nltk.download('punkt')
nltk.download('punkt_tab')  # For sumy tokenization
📖 Usage
Extractive Summary
python
Copy
Edit
from sumy.parsers.plaintext import PlaintextParser
from sumy.nlp.tokenizers import Tokenizer
from sumy.summarizers.lex_rank import LexRankSummarizer

def extractive_summary(text, sentences_count=3):
    parser = PlaintextParser.from_string(text, Tokenizer("english"))
    summarizer = LexRankSummarizer()
    summary = summarizer(parser.document, sentences_count)
    return ' '.join([str(sentence) for sentence in summary])

text = """
Artificial intelligence (AI) is intelligence demonstrated by machines...
"""
print("Extractive Summary:\n", extractive_summary(text))
Abstractive Summary
python
Copy
Edit
from transformers import pipeline

def abstractive_summary(text, max_length=130, min_length=30):
    summarizer = pipeline("summarization", model="facebook/bart-large-cnn")
    summary = summarizer(text, max_length=max_length, min_length=min_length, do_sample=False)
    return summary[0]['summary_text']

text = """
Artificial intelligence (AI) is intelligence demonstrated by machines...
"""
print("Abstractive Summary:\n", abstractive_summary(text))
📝 Sample Output
vbnet
Copy
Edit
Original Text:
Artificial intelligence (AI) is intelligence demonstrated by machines...

Extractive Summary:
Artificial intelligence (AI) is intelligence demonstrated by machines...

Abstractive Summary:
Artificial intelligence (AI) is intelligence demonstrated by machines...
📌 Future Improvements
Add a web interface using Flask or Streamlit.

Support multilingual summarization.

Integrate BERT or Pegasus for better abstractive summaries.

🤝 Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss the proposed feature.

📜 License
This project is licensed under the MIT License – see the LICENSE file for details.

