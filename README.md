# Carolus Archive

Static one-page archive site dedicated to Carlo Chiavegato, in arte Carolus (1923-2015): painting, photography, biography, critique, and contacts.

## Local Development

On Windows:

```powershell
.\serve.bat
```

The site is served from `site/` at:

```text
http://localhost:8000
```

There is no build step, package manager, linter, or test suite. Edit `site/index.html` and reload the browser.

## Project Structure

```text
site/
  index.html
  assets/
serve.bat
```

`FOTO-SITO NONNO/` contains source and unprocessed archive material and is intentionally ignored for the public repository.

## Daily Workflow

```powershell
git status
git add site/index.html site/assets README.md .gitignore serve.bat
git commit -m "Update Carolus archive"
git push
```
