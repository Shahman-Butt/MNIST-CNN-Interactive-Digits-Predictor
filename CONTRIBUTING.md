# Contributing to Handwritten Digit Recognizer

Thank you for your interest in contributing to this project! All contributions—bug reports, fixes, documentation updates, and new features—are highly appreciated.

## How Can I Contribute?

### Reporting Bugs
If you find a bug, please create an Issue and include:
- A clear description of the problem.
- Steps to reproduce it.
- Your operating system and Python version.
- Any error messages or console logs.

### Feature Requests
If you have an idea for a new feature (like supporting MacOS screen capture or improving the GUI), feel free to open an Issue to discuss it before opening a PR.

### Pull Requests
1. Fork the repository and create your branch from `main`.
2. Ensure your code follows the standard Python (PEP 8) style.
3. If you've modified the model architecture (`train_digit_recognizer.py`), please include details about the new accuracy and validation loss.
4. Update the `README.md` and `docs/` if you add new features.
5. Open a Pull Request.

## Local Development Setup
1. Clone the project.
2. Install dependencies: `pip install -r requirements.txt`
3. Make sure to run the `gui_digit_recognizer.py` script locally to test any GUI changes using `win32gui` on Windows.
