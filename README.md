# File-Formats-Finder
# 📂 Real-Time Folder File Format Validator

This project is a **Python script** that continuously monitors a specified folder and validates the format of newly added files. It checks whether supported files contain **tabular data** (rows and columns) and provides instant feedback in your console.

---

## ✅ **What it does**

- Monitors a target folder **in real-time** for new files.
- Automatically checks the file type and whether it’s a valid file:
  - **CSV, XLSX, XLS, TXT** — checks if they contain rows and columns.
  - **PDF** — checks if they contain at least one table.
  - **DOCX** — checks if there is at least one table.
- Ignores temporary files (e.g., `~$file.xlsx`).
- Displays clear validation results for each new file.
- Runs continuously until you stop it manually.

---

## ⚙️ **How it works**

1. **Watchdog Library**  
   Uses [`watchdog`](https://pypi.org/project/watchdog/) to detect file creation events instantly.

2. **File Parsers:**
   - [`pandas`](https://pandas.pydata.org/) for reading `csv`, `xlsx`, `xls`, and `txt` files.
   - [`pdfplumber`](https://pypi.org/project/pdfplumber/) for extracting tables from PDF files.
   - [`python-docx`](https://python-docx.readthedocs.io/) for detecting tables in DOCX files.

3. **Validation Logic:**
   - For spreadsheets and text files: checks for at least 1 row and 1 column.
   - For PDFs: searches each page for tables.
   - For DOCX: checks the `tables` property.

4. **Console Output:**
   - ✅ Means the file is valid and contains tabular data.
   - ❌ Means the file is invalid or empty.
   - 🛑 Means a temporary file was ignored.

---

## 📂 **Supported File Types**

| Extension | Checks performed                          |
|-----------|-------------------------------------------|
| `.csv`    | Checks rows and columns using `pandas`    |
| `.xlsx`   | Checks rows and columns using `pandas`    |
| `.xls`    | Checks rows and columns using `pandas`    |
| `.txt`    | Assumes tab-separated; checks rows/cols   |
| `.pdf`    | Uses `pdfplumber` to find tables          |
| `.docx`   | Uses `python-docx` to detect tables       |

---

Install dependencies:
pip install pandas pdfplumber PyPDF2 python-docx watchdog openpyxl xlrd

requirements:
pandas
pdfplumber
PyPDF2
python-docx
watchdog
openpyxl
xlrd
