# AI Jailbreak & Prompt-Injection Research Lab

A small, beginner-friendly Streamlit application for testing how a locally hosted language model handles instruction conflicts and prompt-injection-like text.

> This project is for defensive evaluation and education. It does not disable a model's safeguards or guarantee that a model is secure.

## Features

- Connects to a local Ollama server.
- Lets you provide a trusted system instruction and a test prompt.
- Runs safe, predefined prompt-injection test cases.
- Flags simple instruction-conflict phrases for manual review.
- Keeps model execution local when using local Ollama.

## Requirements

- Python 3.10+
- [Ollama](https://ollama.com/)
- A model downloaded through Ollama

## Setup on Windows

Open PowerShell in this project folder:

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
ollama pull llama3.2
ollama serve
```

Open a second PowerShell window in the project folder and run:

```powershell
.venv\Scripts\Activate.ps1
streamlit run app.py
```

The app should open in your browser. If Ollama is already running as a background service, you do not need to run `ollama serve` again.

## Run tests

```powershell
python -c "from evaluator import evaluate_response; print(evaluate_response('Ignore previous instructions', 'I will follow the trusted task.'))"
```

## Publish to GitHub

1. Create a new empty repository on GitHub.
2. Open PowerShell in this folder.
3. Run:

```powershell
git init
git add .
git commit -m "Initial AI robustness research lab"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/ai-jailbreak-research-lab.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username.

## Important limitations

- Phrase matching is not a security verdict. It can produce false positives and false negatives.
- A model's refusal or compliance must be judged against the test's expected behavior.
- Do not test systems you do not own or have permission to assess.
- Do not enter private data, credentials, or confidential prompts into a third-party model.
