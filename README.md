# StudyNest

StudyNest helps learners review scattered notes. Save notes in your browser, ask questions grounded in them, generate five practice questions with suggested answers, or get a short summary. Use the **VI / EN** switch to change the interface and the language of AI responses. Your language choice is saved in the browser.

**Live demo:** https://hacktobefest2026-studynest.onrender.com/

## Run locally

1. Create an API key in the [Groq Console](https://console.groq.com/keys).
2. Install dependencies: `python -m pip install -r requirements.txt`.
3. Copy `config_example.py` to `config.py` and put your key in `GROQ_API_KEY`.
4. Run `python app.py` and open `http://127.0.0.1:8000`.

The default model is `openai/gpt-oss-20b`. Change `GROQ_MODEL` in `config.py` if you want to use another model available to your Groq account. `config.py` is ignored by Git. Never commit or share your API key.

## Deploy on Render

The repository includes `render.yaml` for a Python Web Service. In the [Render Dashboard](https://dashboard.render.com/), choose **New → Blueprint**, connect this repository, and enter `GROQ_API_KEY` when prompted. You can also create a Web Service manually with:

- Build command: `pip install -r requirements.txt`
- Start command: `python app.py`
- Environment variable: `GROQ_API_KEY` set to your secret key

The app reads the deployment's `PORT` and binds to the required interface automatically. Once deployed, `/api/health` should return `"configured": true`.

## How it works

The front end is a single HTML file served by a small Python HTTP server. Notes and the chosen language are stored in browser `localStorage`. When you use an AI feature, the server sends the notes to Groq with instructions to answer from the notes and acknowledge missing information. The public demo allows at most 30 AI requests per hour across visitors.

StudyNest uses the open-weight GPT-OSS model through Groq. This avoids downloading a large model to a computer with limited disk space. Notes are sent to Groq only when an AI feature is used; consider this before entering sensitive information.

## Limitations

- AI features need an internet connection and a Groq API key.
- AI answers may be wrong. Check them against your source material.
- Notes stay in one browser and currently have no export or synchronization feature.
