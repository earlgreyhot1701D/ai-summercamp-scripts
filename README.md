# Development Tools: Project Setup & Cleanup Scripts

A collection of cross-platform bash scripts to streamline your development workflow. These tools help you quickly set up Python projects with virtual environments and efficiently manage your workspace by cleaning up old projects.

## Contact Information

**Developer**: Ryan Gertz - rgertz@calpoly.edu

Feel free to reach out if you have questions about:
- Cross-platform compatibility issues
- Customizing the scripts for your workflow
- Virtual environment best practices
- Project organization strategies
- General development environment setup

## What You'll Get

- **Automated Project Setup**: Create new Python projects with virtual environments in seconds
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
Safely removes old projects based on patterns and age:

1. **Pattern Matching**: Find projects using glob patterns (e.g., '*test', 'experiment*')
2. **Age Filtering**: Optionally restrict to projects older than N days
3. **Safety Confirmation**: Shows what will be deleted before proceeding
4. **Cross-Platform**: Works consistently across different operating systems

## Prerequisites

Before you start, you'll need:

### 1. System Requirements
- **Bash shell**: Built-in on macOS/Linux, Git Bash on Windows
- **Python 3.7+**: Download from [python.org](https://www.python.org/downloads/)
- **pip**: Usually included with Python installations

### 2. Optional Tools
- **VS Code**: For automatic IDE integration
- **Git**: For version control (recommended)

### 3. File Permissions
Make the scripts executable:
```bash
chmod +x newenv.sh cleanup_projects.sh
```

## Understanding the Scripts

### Key Features

**Cross-Platform Detection**: Automatically detects your operating system and sets appropriate workspace paths:
- **macOS**: `~/Documents/Workspace`
- **Linux**: `~/workspace`
- **Windows**: `~/Documents/Workspace`

**Python Detection**: Intelligently finds Python 3 installation whether it's called `python3` or `python`.

**Virtual Environment Management**: Creates isolated Python environments to avoid dependency conflicts.

**Safety First**: The cleanup script always shows what will be deleted and asks for confirmation.

### The Functions Explained

#### `newenv.sh` Functions
- **`set_base_dir()`**: Detects OS and sets workspace location
- **`find_python()`**: Locates Python 3 installation
- **`find_pip()`**: Finds the correct pip command
- **Main script**: Creates project structure and files

#### `cleanup_projects.sh` Functions
- **`set_base_dir()`**: Sets workspace location based on OS
- **Pattern matching**: Uses `find` command with glob patterns
- **Age filtering**: Optional time-based project filtering
- **Safety confirmation**: Interactive deletion approval

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
   - Open VS Code (if available)

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

## Customizing the Scripts

### Change Default Workspace Location

Edit the `set_base_dir()` function in either script:

```bash
set_base_dir() {
  case "$(uname -s)" in
    Darwin)
      BASE_DIR="$HOME/my_custom_workspace"  # Your custom path
      ;;
    Linux)
      BASE_DIR="$HOME/my_custom_workspace"
      ;;
    # ... etc
  esac
}
```

### Add Additional Project Files

Modify the file creation section in `newenv.sh`:

```bash
# Add more project files
cat <<EOL > README.md
# $PROJECT_NAME

Your project description here.
EOL

echo "flask" >> requirements.txt  # Add default packages
```

### Custom Cleanup Patterns

Create aliases for common cleanup tasks:

```bash
# Add to your .bashrc or .zshrc
alias cleanup_tests='./cleanup_projects.sh "*test*"'
alias cleanup_old='./cleanup_projects.sh "*" 30'  # 30 days old
alias cleanup_experiments='./cleanup_projects.sh "exp_*" 7'
```

## Common Use Cases

### For Students
- **Quick assignments**: `./newenv.sh cs101_assignment3`
- **Lab experiments**: `./newenv.sh lab_week5_experiment`
- **Clean up semester**: `./cleanup_projects.sh 'cs*' 90`

### For Developers
- **Prototypes**: `./newenv.sh api_prototype_v2`
- **Code challenges**: `./newenv.sh leetcode_daily`
- **Clean up experiments**: `./cleanup_projects.sh 'test_*' 14`

### For Workshops/Tutorials
- **Tutorial projects**: `./newenv.sh tutorial_flask_app`
- **Workshop cleanup**: `./cleanup_projects.sh 'workshop_*' 1`

## Common Issues and Solutions

### "Permission denied"
Make the scripts executable:
```bash
chmod +x newenv.sh cleanup_projects.sh
```

### "Python 3 not found"
- **macOS**: Install via Homebrew: `brew install python3`
- **Linux**: Use package manager: `sudo apt-get install python3`
- **Windows**: Download from [python.org](https://www.python.org/downloads/)

### "Cannot access workspace"
The script will try to create the workspace directory, but you may need to:
1. Create it manually: `mkdir -p ~/Documents/Workspace`
2. Or modify the script to use a different location

### "VS Code not opening"
Install the `code` command:
1. Open VS Code
2. Command Palette (Ctrl/Cmd+Shift+P)
3. Type "Shell Command: Install 'code' command in PATH"

### "Virtual environment not activating"
The script handles activation automatically, but to manually activate:
- **Windows**: `source .venv/Scripts/activate`
- **macOS/Linux**: `source .venv/bin/activate`

## Best Practices

### Project Naming
- Use descriptive names: `flask_blog_app` instead of `project1`
- Include version numbers: `api_v2`, `experiment_3`
- Use consistent patterns: `tutorial_`, `assignment_`, `test_`

### Cleanup Strategy
- **Daily**: Clean up obvious test projects
- **Weekly**: Remove projects older than 7 days
- **Monthly**: Deep clean projects older than 30 days
- **Semester end**: Clean up course-related projects

### Environment Variables
- Never commit `.env` files to version control
- Use meaningful variable names
- Document required environment variables in README

## Safety Features

### Cleanup Script Safety
- **Preview mode**: Shows what will be deleted before confirmation
- **Pattern matching**: Only deletes exactly what you specify
- **Age filtering**: Prevents accidental deletion of recent work
- **Error handling**: Fails safely if permissions are insufficient

### Project Setup Safety
- **Existing project check**: Won't overwrite existing directories
- **Virtual environment isolation**: Prevents package conflicts
- **Automatic .gitignore**: Prevents accidental commits of sensitive files

## Advanced Usage

### Batch Project Creation
```bash
for project in api_test frontend_test database_test; do
  ./newenv.sh "$project"
done
```

### Conditional Cleanup
```bash
# Only clean up if there are many test projects
count=$(find ~/Documents/Workspace -name "*test*" -type d | wc -l)
if [ "$count" -gt 10 ]; then
  ./cleanup_projects.sh '*test*' 7
fi
```

### Integration with Other Tools
```bash
# Create project and initialize git
./newenv.sh my_project
cd ~/Documents/Workspace/my_project
git init
git add .
git commit -m "Initial commit"
```

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

## Example Workflow

Here's a typical development workflow using these scripts:

```bash
# Monday: Start a new project
./newenv.sh machine_learning_experiment

# Work on the project throughout the week
cd ~/Documents/Workspace/machine_learning_experiment
source .venv/bin/activate
pip install pandas numpy
pip freeze > requirements.txt

# Friday: Clean up old test projects
./cleanup_projects.sh '*test*' 7

# Monthly cleanup
./cleanup_projects.sh 'experiment_*' 30
```

---

**Happy coding!** 🚀

These scripts are designed to make your development workflow smoother and more organized. Start with the defaults, then customize them to match your specific needs and preferences.