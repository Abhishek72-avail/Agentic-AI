# UV - An Extremely Fast Python Package Installer and Resolver

<div align="center">
  <img src="https://github.com/astral-sh/uv/raw/main/assets/logo.png" alt="UV Logo" width="200"/>
  
  [![PyPI](https://img.shields.io/pypi/v/uv?logo=python&logoColor=fff&style=flat-square)](https://pypi.org/project/uv/)
  [![Downloads](https://img.shields.io/pypi/dm/uv?style=flat-square)](https://pypi.org/project/uv/)
  [![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)](https://github.com/astral-sh/uv/blob/main/LICENSE-MIT)
  
  **10-100x faster than pip** | **Drop-in replacement for pip** | **Written in Rust**
</div>

---

## 🚀 What is UV?

UV is an extremely fast Python package installer and resolver, written in Rust. It's designed as a drop-in replacement for `pip` and `pip-tools`, offering:

- **🔥 Blazing Fast**: 10-100x faster than pip
- **🔄 Drop-in Replacement**: Works with existing `requirements.txt` files
- **🛡️ Reliable**: Advanced dependency resolution
- **🎯 Modern**: Built with modern Python packaging standards
- **⚡ Zero Dependencies**: Single binary with no external dependencies

---

## 📦 Installation

### Option 1: Install via pip (Recommended)
```bash
pip install uv
```

### Option 2: Install via pipx
```bash
pipx install uv
```

### Option 3: Standalone Installation (macOS/Linux)
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Option 4: Standalone Installation (Windows)
```powershell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### Option 5: Package Managers

#### Homebrew (macOS)
```bash
brew install uv
```

#### Cargo (Rust)
```bash
cargo install uv
```

---

## 🛠️ Environment Setup & Usage

### Basic Usage - Drop-in pip Replacement

UV can be used as a direct replacement for pip:

```bash
# Instead of: pip install requests
uv pip install requests

# Instead of: pip install -r requirements.txt
uv pip install -r requirements.txt

# Instead of: pip freeze
uv pip freeze
```

### Creating and Managing Virtual Environments

#### Create a new project with virtual environment
```bash
# Create a new project directory
mkdir my-python-project
cd my-python-project

# Create a virtual environment
uv venv

# Activate the virtual environment
# On macOS/Linux:
source .venv/bin/activate
# On Windows:
.venv\Scripts\activate
```

#### Install packages in the virtual environment
```bash
# Install packages
uv pip install fastapi uvicorn pandas numpy

# Install from requirements.txt
uv pip install -r requirements.txt

# Install development dependencies
uv pip install pytest black flake8 mypy
```

#### Generate requirements.txt
```bash
# Generate requirements.txt
uv pip freeze > requirements.txt

# Or compile from pyproject.toml
uv pip compile pyproject.toml -o requirements.txt
```

### Advanced Environment Management

#### Using specific Python versions
```bash
# Create venv with specific Python version
uv venv --python 3.11

# Or with system python
uv venv --python python3.9
```

#### Project-based workflow
```bash
# Initialize a new project
mkdir my-app && cd my-app

# Create virtual environment
uv venv

# Install dependencies
echo "fastapi>=0.68.0" > requirements.in
uv pip compile requirements.in -o requirements.txt
uv pip install -r requirements.txt
```

---

## 🎯 Common Commands

| Command | Description | Example |
|---------|-------------|---------|
| `uv pip install` | Install packages | `uv pip install requests pandas` |
| `uv pip install -r` | Install from requirements | `uv pip install -r requirements.txt` |
| `uv pip install -e` | Install in editable mode | `uv pip install -e .` |
| `uv pip uninstall` | Uninstall packages | `uv pip uninstall requests` |
| `uv pip freeze` | List installed packages | `uv pip freeze > requirements.txt` |
| `uv pip list` | List packages (table format) | `uv pip list` |
| `uv pip show` | Show package info | `uv pip show requests` |
| `uv pip compile` | Compile requirements | `uv pip compile requirements.in` |
| `uv venv` | Create virtual environment | `uv venv .venv` |

---

## 🔧 Configuration

### Environment Variables
```bash
# Set custom index URL
export UV_INDEX_URL="https://pypi.org/simple"

# Use cache directory
export UV_CACHE_DIR="~/.cache/uv"

# Disable cache
export UV_NO_CACHE=1
```

### Configuration File
Create `.uvrc` or `uv.toml` in your project:

```toml
[tool.uv]
index-url = "https://pypi.org/simple"
cache-dir = "~/.cache/uv"
python-downloads = "automatic"
```

---

## 🚀 Performance Comparison

| Tool | Time to install | Relative Speed |
|------|----------------|----------------|
| **uv** | 1.2s | **100x faster** |
| pip | 120s | 1x (baseline) |
| poetry | 45s | 2.7x faster |
| pipenv | 180s | 0.7x slower |

*Installing 100 packages from PyPI*

---

## 📋 Quick Start Example

Here's a complete example of setting up a Python project with UV:

```bash
# 1. Create project directory
mkdir fastapi-app && cd fastapi-app

# 2. Create virtual environment
uv venv

# 3. Activate virtual environment (Linux/macOS)
source .venv/bin/activate

# 4. Create requirements.in
cat > requirements.in << EOF
fastapi>=0.68.0
uvicorn[standard]>=0.15.0
pydantic>=1.8.0
EOF

# 5. Compile and install dependencies
uv pip compile requirements.in -o requirements.txt
uv pip install -r requirements.txt

# 6. Create main.py
cat > main.py << EOF
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello, UV!"}
EOF

# 7. Run the application
uvicorn main:app --reload
```

---

## 🆚 UV vs Other Tools

### UV vs pip
- **Speed**: 10-100x faster
- **Dependency Resolution**: More reliable
- **Compatibility**: Drop-in replacement

### UV vs Poetry
- **Speed**: Significantly faster
- **Simplicity**: Less configuration needed
- **Focus**: Package installation vs full project management

### UV vs Pipenv
- **Performance**: Much faster
- **Reliability**: Better dependency resolution
- **Maintenance**: More actively developed

---

## 🐛 Troubleshooting

### Common Issues

#### 1. Permission Errors
```bash
# Use --user flag
uv pip install --user package-name
```

#### 2. SSL Certificate Issues
```bash
# Use trusted host
uv pip install --trusted-host pypi.org package-name
```

#### 3. Clear Cache
```bash
# Clear UV cache
uv cache clean
```

#### 4. Virtual Environment Not Found
```bash
# Ensure you're in the right directory and venv exists
ls -la .venv/
# Or create new venv
uv venv --force
```

---

## 📚 Additional Resources

- **Official Documentation**: [https://github.com/astral-sh/uv](https://github.com/astral-sh/uv)
- **PyPI Package**: [https://pypi.org/project/uv/](https://pypi.org/project/uv/)
- **Release Notes**: [https://github.com/astral-sh/uv/releases](https://github.com/astral-sh/uv/releases)
- **Discord Community**: [https://discord.gg/astral-sh](https://discord.gg/astral-sh)

---

## 🤝 Contributing

UV is open source and welcomes contributions! Check out the [contributing guide](https://github.com/astral-sh/uv/blob/main/CONTRIBUTING.md) to get started.

---

## 📄 License

UV is licensed under the [MIT License](https://github.com/astral-sh/uv/blob/main/LICENSE-MIT).

---

<div align="center">
  <p><strong>⭐ Star the project on GitHub if you find it useful!</strong></p>
  <p>Made with ❤️ by <a href="https://astral.sh">Astral</a></p>
</div>
