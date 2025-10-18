# Quick Reference Card

## 🚀 Common Commands

```bash
# Setup (uses existing or downloads portable Python)
./setup.sh

# Clean rebuild (removes everything, starts fresh)
./setup.sh --force-clean

# Show help
./setup.sh --help

# Activate Poetry shell
poetry shell

# Run commands with Poetry
poetry run python src/main.py
poetry run pytest
```

## 📊 Quick Decision Guide

```
First time?
└─ ./setup.sh

Something broken?
└─ ./setup.sh --force-clean

Add dependency?
└─ poetry add package-name

Add dev dependency?
└─ poetry add --group dev package-name

Update dependencies?
└─ poetry update
```

## 🎯 Common Workflows

| Task | Commands |
|------|----------|
| **Initial setup** | `./setup.sh` |
| **Activate shell** | `poetry shell` |
| **Daily development** | `poetry shell` → `python src/main.py` |
| **Add dependency** | `poetry add package-name` |
| **Add dev dependency** | `poetry add --group dev pytest-mock` |
| **Run tests** | `poetry run pytest` or `pytest --cov=src` |
| **Format code** | `poetry run black src/ tests/` |
| **Update deps** | `poetry update` |
| **Fix issues** | `./setup.sh --force-clean` |

## 📁 What Gets Created

```
.python/          # Portable Python (~80MB, gitignored)
.venv/            # Virtual environment (~50MB, gitignored)
poetry.lock       # Locked dependencies (commit for reproducibility)
```

## 🎨 Color Guide

- ✅ Green = Success, found existing
- 📥 Blue = Downloading/installing
- 🧹 Yellow = Cleaning
- ❌ Red = Error
- 💡 Light blue = Info/tips

## ⚡ Speed Guide

| Operation | Time | Network |
|-----------|------|---------|
| First setup (download) | 1-2 min | Required |
| Reuse existing Python | 10-30 sec | Optional |
| Clean rebuild | 1-2 min | Required |
| `poetry add` | 5-15 sec | Required |

## 💾 Disk Space

| Item | Size |
|------|------|
| Portable Python | ~80 MB |
| Virtual environment | ~50 MB |
| Total | ~150 MB |

## 🚫 .gitignore

Always ignore these:
```gitignore
.python/
.venv/
# poetry.lock - Usually committed for reproducibility
```

## 🔧 Quick Fixes

```bash
# Virtual environment broken
rm -rf .venv/ poetry.lock && ./setup.sh

# Everything broken
./setup.sh --force-clean

# Poetry not working
source .venv/bin/activate && pip install --upgrade poetry

# Dependencies out of sync
poetry install

# Clear Poetry cache
poetry cache clear pypi --all
```

## 📦 Poetry-Specific Commands

```bash
# Show installed packages
poetry show

# Show dependency tree
poetry show --tree

# Show outdated packages
poetry show --outdated

# Export requirements.txt
poetry export -f requirements.txt --output requirements.txt

# Check pyproject.toml validity
poetry check

# Get virtual environment info
poetry env info
```

## 🎯 Key Principles

1. **Always portable** - Never uses system Python
2. **Reuse when possible** - Keeps existing `.python/` if found
3. **Fresh venv** - Always recreates `.venv/`
4. **Clean on demand** - `--force-clean` for fresh start
5. **Poetry manages deps** - Use `poetry add/remove/update`

## 📞 Need Help?

```bash
# Show help
./setup.sh --help

# Poetry help
poetry --help
poetry add --help

# Check versions
.python/bin/python3 --version
poetry --version
poetry env info

# Debug
ls -la .python/bin/
ls -la .venv/bin/
poetry config --list
```
