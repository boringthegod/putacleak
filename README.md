# putacleak

# Description

Automate your dorking and analysis of your target's files: Files are automatically downloaded and analyzed with LLM Llama3.2 to eliminate false positives (which often represent 90% of the documents found by dorking, a tedious task to perform yourself).

![](https://i.ibb.co/hZ5j54r/Capture.png)

# Requirements

- [Python 3](https://www.python.org/download/releases/3.0/)

- install pip requirements : `pip install -r requirements.txt`

- install uncensored LLama3.2 : `ollama run artifish/llama3.2-uncensored`

- **Residential proxies to change line 27 and 28**


# Usage


```bash
usage: putacleak.py [-h] -d DOMAIN [-ft FILETYPE] [-kw KEYWORDS] [-mp MAX_PAGES] [-v]

putacleak - search for potentially sensitive files using google dorking and then analyze their content with LLM

options:
  -h, --help            show this help message and exit
  -d DOMAIN, --domain DOMAIN
                        Domain to search, for example: carrefour.fr
  -ft FILETYPE, --filetype FILETYPE
                        File types to search, separated by commas (e.g.: pdf,docx,doc)
  -kw KEYWORDS, --keywords KEYWORDS
                        Keywords to search for, separated by commas (e.g.: creds,"mot de passe",admin)
  -mp MAX_PAGES, --max-pages MAX_PAGES
                        Maximum number of pages to scrape (default 9)
  -v, --verbose         Activate verbose mode for more details

Examples:
  ./putacleak.py -d carrefour.fr
  ./putacleak.py -d carrefour.fr -v
  ./putacleak.py -d carrefour.fr -ft pdf,sh,txt,docm
  ./putacleak.py -d carrefour.fr -kw pass,credential,"mot de passe",administrator
  ./putacleak.py -d carrefour.fr -kw pass,credential,"mot de passe",administrator -ft pdf,sh,txt,docm -mp 13
```
