# Website Summarizer (OpenAI API + Ollama)

Summarize the content of any web page using either:

- **OpenAI API** (cloud models)
- **Ollama** (local models via an OpenAI-compatible endpoint)

Included notebooks:

- `summerizer_Openai.ipynb` — uses OpenAI API
- `summerizer_Ollama.ipynb` — uses Ollama running locally on `http://localhost:11434`

---

## What’s inside

- Web scraping with `requests` + `BeautifulSoup`
- A small summarization helper (`summarize(url)`) in each notebook
- Model calls via the **OpenAI Python SDK** (`from openai import OpenAI`)

---

## Prerequisites

- Python **3.10+**
- Jupyter (Notebook or Lab)

### Install dependencies

You can use a virtual environment (recommended):

```bash
python -m venv .venv

# macOS/Linux
source .venv/bin/activate

# Windows (PowerShell)
# .venv\Scripts\Activate.ps1

pip install -U pip
```

Install packages:

```bash
pip install -U openai python-dotenv beautifulsoup4 requests ipython jupyter
```

---

## Run the notebooks

Start Jupyter:

```bash
jupyter lab
# or: jupyter notebook
```

Then open either:

- `summerizer_Openai.ipynb`
- `summerizer_Ollama.ipynb`

---

## OpenAI API setup (cloud)

### 1) Create an OpenAI API key

1. Sign in to the OpenAI Developer Platform.
2. Open the API keys page: https://platform.openai.com/account/api-keys
3. Click **Create new secret key**.
4. Copy the key and store it securely.

### 2) Add the key to your environment

Create a `.env` file in the project root:

```bash
# .env (do not commit this file)
OPENAI_API_KEY=sk-proj-xxxxxxxxxxxxxxxxxxxxxxxx
```

The OpenAI notebook loads this key using `python-dotenv`.

### 3) Run `summerizer_Openai.ipynb`

Execute the cells top-to-bottom. Update the `model=` value if you want to use a different OpenAI model.

---

## Ollama setup (local)

The Ollama notebook uses Ollama’s **OpenAI-compatible** endpoint and calls it with the OpenAI Python SDK.

### 1) Install Ollama

Download/install Ollama for your OS:

- Docs home: https://docs.ollama.com/
- Quickstart: https://docs.ollama.com/quickstart

### 2) Start Ollama

- **macOS / Windows:** Ollama typically runs in the background after installation and serves an API on `http://localhost:11434`.
- **Linux:** start the server manually:

```bash
ollama serve
```

### 3) Pull a model

The notebook uses `llama3.2` by default:

```bash
ollama pull llama3.2
```

(You can swap this for any model you have installed.)

### 4) Run `summerizer_Ollama.ipynb`

The notebook points the client to:

```python
OLLAMA_BASE_URL = "http://localhost:11434/v1"
ollama = OpenAI(base_url=OLLAMA_BASE_URL, api_key="ollama")
```

Then it calls:

```python
ollama.chat.completions.create(model="llama3.2", messages=messages)
```

---

## Troubleshooting

- **`No API key was found`**: make sure `.env` exists and contains `OPENAI_API_KEY=...`, or export it in your shell.
- **Connection refused to Ollama**: confirm Ollama is running and listening on `http://localhost:11434`.
- **Model not found (Ollama)**: run `ollama pull <model>`.
- **Port already in use**: another Ollama instance may already be running; stop it or free port `11434`.

---

## Security notes

- Never commit `.env` or any API keys.
- Add this to your `.gitignore`:

```gitignore
.env
.venv/
__pycache__/
.ipynb_checkpoints/
```

---

## License

MIT


## Author

- **Prathamesh Uravane**
- **Email:** upratham2002@gmail.com

