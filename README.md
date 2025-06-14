
## WSAD: A Web-Scraped Arabic Dataset for Text Simplification

This project collects and simplifies Arabic text from the OSCAR dataset and websites.

## What It Does
1. **OSCAR Mining**: Gets Arabic sentences (30–300 characters) from OSCAR, saving ~150MB __YOU CAN CHANGE IT__  to `oscar_arabic.json`.
2. **URL Mining**: Scrapes Arabic articles from URLs in `urls.txt`, saving up to 100 articles  __YOU CAN CHANGE IT__  to `articles.json`.
3. **Simplification**: Cleans text and simplifies it using the Gemma3:4b model, saving to `simple_pairs_ollama_corrected.json`.
4. **Cleanup**: Removes English text, saving clean data to `simple_pairs_ollama_corrected_cleaned.json`.

## Setup
Install dependencies:
```bash
pip install datasets newspaper3k lxml[html_clean] tqdm scrapy ollama
```

Install Ollama:
```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama pull gemma3:4b
```

## How to Use
1. **OSCAR Mining**:
   ```bash
   python oscar_mining.py
   ```
   Output: `oscar_arabic.json`

2. **URL Mining**:
   Edit `urls.txt` with URLs (e.g., https://mawdoo3.com/), then:
   ```bash
   python url_mining.py
   ```
   Output: `articles.json`

3. **Simplification**:
   Start Ollama:
   ```bash
   nohup ollama serve &
   ```
   Run:
   ```bash
   python preprocess_simplify.py
   ```
   Output: `simple_pairs_ollama_corrected.json`

4. **Cleanup**:
   ```bash
   python postprocess.py
   ```
   Output: `simple_pairs_ollama_corrected_cleaned.json`

## Notes
- Check `urls.txt` for valid URLs.
- Review `oscar_arabic.json` and `articles.json` before simplifying.
- Ollama must be running for simplification.
