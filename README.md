WSAD: Web-Scraped Arabic Dataset for Text Simplification
This project collects and simplifies Arabic text from the OSCAR dataset and websites.
What It Does

OSCAR Mining: Gets Arabic sentences (30–300 characters) from OSCAR, saving ~150MB " YOU  CAN MAKE IT BIGGGER" to oscar_arabic.json.
URL Mining: Scrapes Arabic articles from URLs in urls.txt, saving up to 100 articles to articles.json.
Simplification: Cleans text and simplifies it using the Gemma3:4b model, saving to simple_pairs_ollama_corrected.json.
Cleanup: Removes English text, saving clean data to simple_pairs_ollama_corrected_cleaned.json.

Setup
Install dependencies:
pip install datasets newspaper3k lxml[html_clean] tqdm scrapy ollama

Install Ollama:
curl -fsSL https://ollama.com/install.sh | sh
ollama pull gemma3:4b

How to Use

OSCAR Mining:
python oscar_mining.py

Output: oscar_arabic.json

URL Mining: Edit urls.txt with URLs (e.g., https://mawdoo3.com/), then:
python url_mining.py

Output: articles.json

Simplification: Start Ollama:
nohup ollama serve &

Run:
python preprocess_simplify.py

Output: simple_pairs_ollama_corrected.json

Cleanup:
python postprocess.py

Output: simple_pairs_ollama_corrected_cleaned.json


Notes

Check urls.txt for valid URLs.
Review oscar_arabic.json and articles.json before simplifying.
Ollama must be running for simplification.

