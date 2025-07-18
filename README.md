# Cal Poly AI Summer Camp: Scripts for Creating Python Projects

Welcome to our AI Summer Camp! This project give you scripts to launch your python projects with ease!

## Contact Information

**Instructor**: Ryan Gertz - rgertz@calpoly.edu

Feel free to reach out if you have questions about:
- Cross-platform compatibility issues
- Project organization strategies
- General development environment setup


## Video Tutorial

For a complete walkthrough of this project, check out my video explanation:
[AI Summer Camp Tutorial - Shell Scripts for Starting Projects](https://drive.google.com/file/d/1xrKQHcGWVSqYFgO3iwtMwgPK2nAYxKWn/view?usp=drive_link)

## What You'll Get

- **Automated Project Setup**: Create new Python projects with virtual environments
- **Intelligent Cleanup**: Remove old test projects and experiments safely
- **Cross-Platform Support**: Works on macOS, Linux, and Windows (Git Bash/WSL)
- **Development Best Practices**: Pre-configured with .gitignore, environment files, and project structure

## Scripts Overview

### `newenv.sh` - Project Setup Script
Creates a new Python project with a complete development environment:

1. **Creates Project Directory**: Sets up folder structure in your workspace
2. **Virtual Environment**: Creates and activates a Python virtual environment
3. **Development Files**: Generates .env, requirements.txt, .gitignore, and main.py
4. **Package Installation**: Installs python-dotenv for environment variable management
5. **IDE Integration**: Automatically opens the project in VS Code

### `cleanup_projects.sh` - Workspace Cleanup Script
Safely removes old projects:

1. **Age Filtering**: Optionally restrict to projects older than N days
2. **Safety Confirmation**: Shows what will be deleted before proceeding
3. **Cross-Platform**: Works consistently across different operating systems

## Prerequisites

Before you start, you'll need:

### 1. System Requirements
- **Bash shell**: Built-in on macOS/Linux, Git Bash on Windows
- **Python 3.7+**: Download from [python.org](https://www.python.org/downloads/)
- **pip**: Usually included with Python installations
- **VS Code**: For automatic IDE integration


### 2. File Permissions
Make the scripts executable:
```bash
chmod +x newenv.sh cleanup_projects.sh
```

## How to Use the Scripts

### Setting Up a New Project

1. **Make the script executable**:
   ```bash
   chmod +x newenv.sh
   ```

2. **Run the script**:
   ```bash
   ./newenv.sh my_awesome_project
   ```

3. **Start coding**: The script will:
   - Create your project folder
   - Set up a virtual environment
   - Generate starter files
   - Open VS Code

### Cleaning Up Old Projects

1. **Make the script executable**:
   ```bash
   chmod +x cleanup_projects.sh
   ```

2. **Clean up test projects**:
   ```bash
   ./cleanup_projects.sh '*test'
   ```

3. **Clean up old experiments (older than 7 days)**:
   ```bash
   ./cleanup_projects.sh 'experiment*' 7
   ```

4. **Clean up all projects matching a pattern**:
   ```bash
   ./cleanup_projects.sh 'old_*'
   ```

## Project Structure Created

When you run `newenv.sh`, here's what gets created:

```
my_project/
├── .venv/                 # Virtual environment
├── .env                   # Environment variables
├── .gitignore            # Git ignore rules
├── main.py               # Starter Python file
└── requirements.txt      # Package dependencies
```

### Generated Files Explained

**`.env`**: Contains environment variables (secrets, API keys, etc.)
```
SECRET_KEY=your_secret_key_here
```

**`main.py`**: Starter Python file with environment variable loading
```python
import os
from dotenv import load_dotenv

load_dotenv()
secret = os.getenv("SECRET_KEY")

print(f"Hello from my_project!")
print(f"Loaded secret key: {secret}")
```

**`.gitignore`**: Comprehensive ignore file for Python projects
- Virtual environment files
- Python cache files
- IDE configuration
- Environment files

## Common Issues and Solutions

### "Permission denied"
Make the scripts executable:
```bash
chmod +x newenv.sh cleanup_projects.sh
```

### "Python 3 not found"
- **macOS**: Install via Homebrew: `brew install python3`
- **Linux**: Use package manager: `sudo apt-get install python3`
- **Windows**: Download from [python.org](https://www.python.org/downloads/), and make sure Python is in your [PATH](https://stackoverflow.com/questions/3701646/how-to-add-to-the-pythonpath-in-windows-so-it-finds-my-modules-packages) variable


### "Virtual environment not activating"
The script handles activation automatically, but to manually activate:
- **Windows**: `source .venv/Scripts/activate`
- **macOS/Linux**: `source .venv/bin/activate`

## Best Practices

### Project Naming
- Use descriptive names: `flask_blog_app` instead of `project1`
- Include version numbers: `api_v2`, `experiment_3`
- Use consistent patterns: `tutorial_`, `assignment_`, `test_`


### Environment Variables
- Never commit `.env` files to version control
- Use meaningful variable names
- Document required environment variables in README

## Troubleshooting

### Script Won't Execute
1. Check file permissions: `ls -la newenv.sh`
2. Make executable: `chmod +x newenv.sh`
3. Run with bash: `bash newenv.sh project_name`

### Path Issues
1. Check your workspace exists: `ls ~/Documents/Workspace`
2. Create if needed: `mkdir -p ~/Documents/Workspace`
3. Verify script can write: `touch ~/Documents/Workspace/test && rm ~/Documents/Workspace/test`

### Python Issues
1. Check Python version: `python3 --version`
2. Check pip: `pip3 --version`
3. Update pip: `python3 -m pip install --upgrade pip`

## Getting Help

If you encounter issues:
1. Check the error message carefully
2. Verify all prerequisites are installed
3. Try running individual commands manually
4. Check file permissions and paths
5. Contact the developer for support

---

**Happy coding!** 🚀
