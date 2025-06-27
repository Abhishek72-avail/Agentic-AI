# AI Agentic Development Environment Setup

This guide will help you set up a complete development environment for AI agentic projects using VS Code and the uv package manager.

## About uv

uv is an extremely fast Python package installer and resolver, written in Rust. It's designed as a drop-in replacement for pip and pip-tools, offering significantly faster package installation and dependency resolution.

## Prerequisites

- VS Code installed
- Python 3.8+ installed
- uv package manager installed (see installation instructions in `aboutuv.md`)

## Environment Setup

### 1. Create Project Folder

```bash
mkdir agentic-ai
cd agentic-ai
```

### 2. Initialize uv Project

```bash
uv init
```

This command will create the basic project structure with:
- `pyproject.toml` - Project configuration file
- `README.md` - Project documentation
- `src/` - Source code directory
- `.python-version` - Python version specification

### 3. Install Required Packages

Install the core packages for AI agentic development:

```bash
# Install TensorFlow
uv add tensorflow

# Install HTTP requests library
uv add requests

# Install LangChain for AI agent development
uv add langchain

# Install Jupyter kernel for notebook support
uv add ipykernel
```

Alternative installation method using uv pip:
```bash
uv pip install tensorflow
```

### 4. Verify Installation

Check that all packages are installed correctly:

```bash
uv pip list
```

## Running Your Project

### Execute Python Files

To run your main Python file:

```bash
uv run main.py
```

### Using Jupyter Notebooks

This project supports Jupyter notebooks for interactive development:

1. After installing `ipykernel`, you can create and run Jupyter notebooks
2. VS Code will automatically detect the uv environment
3. Select the correct Python interpreter in VS Code (should show the uv environment path)

## Project Structure

```
agentic-ai/
├── pyproject.toml          # Project configuration
├── README.md               # Project documentation
├── main.py                 # Main application file
├── src/                    # Source code directory
├── notebooks/              # Jupyter notebooks (optional)
└── .python-version         # Python version file
```

## Development Workflow

1. **Activate Environment**: uv automatically manages the virtual environment
2. **Install Dependencies**: Use `uv add <package-name>` to add new packages
3. **Run Code**: Use `uv run <script.py>` to execute Python files
4. **Notebook Development**: Use VS Code's Jupyter extension with the uv environment

## Key Commands Reference

| Command | Description |
|---------|-------------|
| `uv init` | Initialize new project |
| `uv add <package>` | Add a new dependency |
| `uv run <script.py>` | Run Python script |
| `uv pip install <package>` | Install package using pip interface |
| `uv pip list` | List installed packages |
| `uv sync` | Install all dependencies from pyproject.toml |

## Next Steps

1. Create your `main.py` file in the project root
2. Start developing your AI agentic application
3. Use Jupyter notebooks for experimentation and prototyping
4. Leverage LangChain for building sophisticated AI agents

## Troubleshooting

- If VS Code doesn't detect the Python interpreter, manually select it from the uv environment
- Ensure uv is properly installed by running `uv --version`
- For installation issues, refer to the `aboutuv.md` file for OS-specific installation instructions

---

Happy coding with your AI agentic project! 🚀