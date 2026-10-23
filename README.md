# 🧠 Question Analyzer

A Streamlit app where you type a question and Google's Gemini Flash model **analyzes it**
(category, intent, difficulty, key concepts) and then **answers it**, with suggested follow-up questions.

## Features
- Structured analysis + Markdown answer
- Answer styles: Concise, Detailed, Explain like I'm 12
- Session history of previous questions
- API key via sidebar, Streamlit secrets, or environment variable
- Model name is configurable (no code change needed when Google releases a new Flash version)

## Project structure
```
.
├── app.py             # Streamlit app
├── requirements.txt   # Python dependencies
└── README.md
```

## Run locally
1. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
2. Install and run:
   ```bash
   python -m venv .venv
   source .venv/bin/activate        # Windows: .venv\Scripts\activate
   pip install -r requirements.txt
   ```
3. Provide your key (pick one):
   - Paste it in the app sidebar, **or**
   - Set an environment variable:
     - macOS/Linux: `export GEMINI_API_KEY="your-key"`
     - Windows PowerShell: `$env:GEMINI_API_KEY="your-key"`
   - Or create `.streamlit/secrets.toml` containing `GEMINI_API_KEY = "your-key"`
4. Start the app:
   ```bash
   streamlit run app.py
   ```

## Configuration
| Setting | Where | Default |
|---|---|---|
| `GEMINI_API_KEY` | sidebar / secrets / env var | none (required) |
| `GEMINI_MODEL` | env var or sidebar field | `gemini-2.5-flash` |

## Deploy on Streamlit Community Cloud
1. Push this repo to GitHub (never commit your API key or `.streamlit/secrets.toml`).
2. Go to [share.streamlit.io](https://share.streamlit.io), sign in with GitHub, click **Create app**.
3. Select your repo, branch `main`, and main file `app.py`.
4. Open **Advanced settings → Secrets** and add:
   ```toml
   GEMINI_API_KEY = "your-key"
   ```
5. Click **Deploy**.

## Troubleshooting
- **"No API key found"**: add the key in the sidebar, env var, or secrets.
- **404 / model not found**: the model name may have changed; set a current Flash model name in the sidebar.
- **429 / quota errors**: you hit the free-tier rate limit; wait a bit and retry.
- **Empty response**: the model may have blocked the content; rephrase the question.

## License
MIT
