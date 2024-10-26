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

All you have to do is run it by putting the main domain name of your target after the -d argument.

By default, a number of dorking and filetypes are hardcoded. If you'd like to choose your own keyword to search, and only search on certain filetypes, you can use the `-kw` and `-ft` options. 
By default, scraping is limited to the first 9 pages of google results, but if you want to decrease or increase this option, use the `-mp` argument.

All you have to do is launch the tool, and the scraping, downloading, extraction and LLM processing phases will take care of themselves. You'll be presented with an output folder containing all the files downloaded and processed, as well as a **results file** indicating which files potentially contain credentials or leaks of sensitive information. 

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

*LLM llama 3.2 is not yet perfect and can make mistakes. To improve reliability, you can use nemotron, but it requires more hardware.*
