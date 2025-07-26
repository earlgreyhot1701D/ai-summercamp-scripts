# 🛠️ AI Camp Setup Log – Phase 1 (System Build & Environment Prep)

## ✅ What I Set Out to Do
Prepare my local machine to develop and run AI chatbot projects using:
- Python
- AWS (Amazon Bedrock)
- LangChain
- Streamlit
- GitHub

This is part of my pre-camp practice using Ryan’s repo as a starter.

---

## 🧰 Tools I Used
- Git + Git Bash (for terminal commands and GitHub repo management)
- Python 3.13.1 (installed from [python.org](https://www.python.org/))
- pip (Python package manager)
- Visual Studio Code (text/code editor)
- AWS CLI (for secure access to AWS services like Bedrock)
- ChatGPT (as a build assistant and debugger)

---

## 🔍 Step-by-Step: What I Did

### System Prep
- Installed Git, Git Bash, and Python 3.13.1
- Installed AWS CLI
- Installed Visual Studio Code

### GitHub Setup
- Forked Ryan’s repo to my GitHub:  
  [https://github.com/earlgreyhot1701D/ai-summercamp-scripts](https://github.com/earlgreyhot1701D/ai-summercamp-scripts)
- Cloned the repo locally with:
  ```bash
  git clone https://github.com/earlgreyhot1701D/ai-summercamp-scripts.git
  ```
- Navigated into the repo folder using Git Bash

### Virtual Environment
- Created the environment:
  ```bash
  python -m venv .venv
  ```
- Activated it in Git Bash:
  ```bash
  source .venv/Scripts/activate
  ```
- Verified with the `(.venv)` prompt

### Package Installation
- No `requirements.txt` found
- Manually installed necessary packages:
  ```bash
  pip install streamlit langchain boto3 python-dotenv
  ```
- Verified package list using:
  ```bash
  pip list
  ```

### AWS CLI Setup
- Ran:
  ```bash
  aws configure
  ```
- Entered:
  - AWS Access Key ID and Secret
  - Region: `us-west-2`
  - Output format: `json`
- Verified connection with:
  ```bash
  aws sts get-caller-identity
  ```

---

## ⚠️ What Went Wrong (and How I Fixed It)

| Issue | Fix |
|-------|-----|
| `python` not recognized in Git Bash at first | Used `where python` in Command Prompt to confirm location; ensured Python installed properly with PATH setting |
| `requirements.txt` missing | Manually installed `streamlit`, `langchain`, `boto3`, `python-dotenv` |
| `newenv.sh` required a project name input | Bypassed the script and created `.venv` manually |
| Confusion about Copilot vs. ChatGPT | Learned that ChatGPT is external and exploratory; Copilot will be siloed and policy-compliant for court use |
| Unsure whether I was supposed to build or run the current repo | Clarified this is Phase 1 practice; CCP chatbot will be built in Phase 2 |

---

## ✅ Current Status
- Local Python + AWS development environment is complete
- Virtual environment is activated
- Python packages are installed
- AWS CLI is authenticated and working

---

## 🧭 Next Steps
- ✅ Run Ryan’s repo to practice launching and interacting with a chatbot app
- ⏩ Create new repo or folder for building **CCP chatbot** project from scratch using what I’ve learned
- ⏩ Document app run results and RAG implementation strategy in follow-up notes

---

📘 Credit: This setup was based on Ryan's original [AI Summer Camp scripts](https://github.com/ryan-court-ai/ai-summercamp-scripts), used here as a practice environment for pre-camp development and configuration.





