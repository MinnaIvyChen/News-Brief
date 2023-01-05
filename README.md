News Brief

# Install
!pip install sumy

# Summarize news in English
import nltk
nltk.download('punkt')

# Import 
from sumy.parsers.html import HtmlParser
from sumy.parsers.plaintext import PlaintextParser
from sumy.nlp.tokenizers import Tokenizer
from sumy.summarizers.lsa import LsaSummarizer as Summarizer
from sumy.nlp.stemmers import Stemmer
from sumy.utils import get_stop_words

# Usage

LANGUAGE = "english"

SENTENCES_COUNT = 10

# News source
url = "https://www.nbcnews.com/politics/congress/tiktok-banned-house-issued-mobile-devices-rcna63403"

parser = HtmlParser.from_url(url, Tokenizer(LANGUAGE))
summarizer = Summarizer(Stemmer(LANGUAGE))
summarizer.stop_words = get_stop_words(LANGUAGE)
sumies = summarizer(parser.document, SENTENCES_COUNT)
for i, sentence in enumerate(sumies):
    print('{}. {}'.format(i+1, sentence))
