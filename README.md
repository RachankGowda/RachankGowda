# PythonAIChatbot

A Streamlit AI chatbot built with Python, LangChain, LangGraph, and Groq. The chatbot can answer questions, perform addition, and greet users through custom tools.

## Features

- Groq language model integration
- LangGraph ReAct agent
- Calculator tool for adding two numbers
- Greeting tool
- Streamlit chat interface with message history
- Sidebar controls for clearing the conversation
- `.env` configuration for API credentials

## Architecture

```text
User Input
    |
    v
Streamlit Web Interface
    |
    v
main.py
    |
    +--> ChatGroq Language Model
    |
    +--> LangGraph ReAct Agent
            |
            +--> calculator(a, b)
            |
            +--> say_hello(name)
    |
    v
Streamed Assistant Response
```

## Project Structure

```text
Rachan/
├── main.py
├── README.md
├── .env
├── .gitignore
└── .venv/.
```

## How It Works

1. Loads environment variables from `.env`.
2. Initializes the Groq model using `ChatGroq`.
3. Registers the `calculator` and `say_hello` tools.
4. Creates a LangGraph ReAct agent.
5. Accepts user messages through the Streamlit chat window.
6. Sends the request to the LangGraph agent.
7. Displays the response in the conversation view.

## Requirements

- Python 3.10 or newer
- Groq API key
- Internet connection

## Installation

Open PowerShell in the project directory:

```powershell
cd "C:\Users\LAB2\Desktop\Rachan"
```

### 1. Create a virtual environment

```powershell
python -m venv .venv
```

### 2. Activate the virtual environment

```powershell
.venv\Scripts\Activate.ps1
```

If activation is blocked, run:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Then activate the environment again.

### 3. Install dependencies

```powershell
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Configure environment variables

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key
GROQ_MODEL=qwen/qwen3.6-27b
```

Replace `your_groq_api_key` with your actual Groq API key.

## Run the Application

```powershell
streamlit run main.py
```

Streamlit opens the app in your browser. Add `GROQ_API_KEY` to `.env` before sending a message.

Example prompts:

```text
What is 25 plus 15?
```

```text
Say hello to Rachan.
```

Stop the Streamlit process with `Ctrl+C` to exit.

## Save Dependencies

```powershell
pip freeze > requirements.txt
```

To install dependencies later:

```powershell
pip install -r requirements.txt
```

## Deactivate the Virtual Environment

```powershell
deactivate
```

## Security

Add the following entries to `.gitignore`:

```gitignore
.venv/
.env
__pycache__/
*.py[cod]
```

Never commit `.env`, because it contains your API key.