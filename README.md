# Web Summarizer (OpenAI + BeautifulSoup)

A small Jupyter Notebook project that:

- Scrapes a webpage (title + visible text) using **Requests + BeautifulSoup**
- Summarizes it using the **OpenAI API**
- Renders the result as **Markdown** inside the notebook

Notebook: `web_Summerizer.ipynb`

---

## Features

- Fetch website content: `fetch_website_contents(url)`
- Summarize a URL with OpenAI: `summarize(url)`
- Display the summary in a notebook cell: `display_summary(url)`

---

## Requirements

- Python 3.9+ (recommended)
- Jupyter Notebook or JupyterLab

Python packages used in the notebook:

- `openai`
- `python-dotenv`
- `requests`
- `beautifulsoup4`

---

## Setup

### 1) Create a virtual environment (recommended)

```bash
python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows (PowerShell)
.venv\Scripts\Activate.ps1
```

### 2) Install dependencies

```bash
pip install -U openai python-dotenv requests beautifulsoup4
```

---

## Get an OpenAI API key

1. Create (or sign into) your OpenAI Developer Platform account.
2. Go to the API keys page:
   - https://platform.openai.com/account/api-keys
3. Click **Create new secret key**.
4. (Optional) Set permissions for the key.
5. Copy the key and store it somewhere safe (you typically can’t view the full secret again).

**Important:** Keep your API key private. Don’t commit it to GitHub and don’t paste it into client-side apps.

---

## Configure your API key (recommended: `.env`)

Create a file named `.env` in the project root:

```env
OPENAI_API_KEY=sk-...your_key_here...
```

Then add `.env` to your `.gitignore`:

```gitignore
.env
```

The notebook uses `python-dotenv` to load the key into the `OPENAI_API_KEY` environment variable.

### Alternative: set an environment variable

```bash
# macOS/Linux
export OPENAI_API_KEY="sk-..."

# Windows (PowerShell)
$env:OPENAI_API_KEY="sk-..."
```

---

## Run the notebook

```bash
jupyter notebook
# or
jupyter lab
```

Open `web_Summerizer.ipynb` and run the cells.

---

## Quick usage

Inside the notebook:

```python
display_summary("https://example.com")
```

---

## Notes & troubleshooting

- Some websites block automated requests. The notebook sets a browser-like `User-Agent`, but a site may still deny access.
- If you get an authentication error, confirm `OPENAI_API_KEY` is set/loaded and that you copied the key correctly.

---

## Security

- Treat your API key like a password.
- Rotate/revoke keys you believe were exposed.

---

## Author

- **Prathamesh Uravane**
- **Email:** upratham2002@gmail.com

## License

Add a license if you plan to make this public (MIT/Apache-2.0 are common choices).
