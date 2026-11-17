# SE Lab 5: Static Code Analysis — Contact & Address Book Manager

## 1. Project Overview

This project is part of Software Engineering Lab 5 — Static Code Analysis.

The objective is to analyze and improve the quality, security, readability, and maintainability of a Python-based Contact & Address Book Manager using three static code analysis tools:

- **Pylint** — Code quality analysis
- **Bandit** — Security vulnerability detection
- **Flake8** — Code style and formatting analysis

The original Python program contained several security vulnerabilities, coding-standard violations, and formatting issues. These issues were identified, documented, and corrected while preserving the application's functionality.

## 2. Features of the Application

The Address Book Manager supports the following operations:

1. Add contacts with phone number validation.
2. Search contacts by name or phone number.
3. Update the city of an existing contact.
4. Group contacts based on their city.
5. Display contacts in alphabetical order.
6. Export contacts to a CSV file.
7. Create an address book backup using JSON.
8. Restore contacts from the backup.
9. Generate contact identifiers using SHA-256.

## 3. Technologies Used

| Technology | Purpose |
|---|---|
| Python 3.11.9 | Application development |
| Pylint 4.1.4 | Code quality analysis |
| Bandit 1.9.4 | Security analysis |
| Flake8 7.5.0 | Style and formatting analysis |
| Git | Version control |
| GitHub | Repository hosting |
| Visual Studio Code | Development environment |

## 4. Project Structure

```text
SE_Lab5_Address_Book/
│
├── address_book.py
├── README.md
├── issues.md
├── reflection.md
├── .gitignore
│
├── before/
│   ├── pylint_report.txt
│   ├── bandit_report.txt
│   └── flake8_report.txt
│
└── after/
    ├── pylint_report.txt
    ├── bandit_report.txt
    └── flake8_report.txt
```

The `before` folder contains the original analysis reports, and the `after` folder contains the reports generated after applying the fixes.

## 5. Installation and Setup

### Step 1: Clone the repository

```bash
git clone https://github.com/Bhavani-gh/SE_Lab5_Address_Book.git
cd SE_Lab5_Address_Book
```

### Step 2: Create a virtual environment

```bash
python -m venv venv
```

Activate it on Windows PowerShell:

```powershell
.\venv\Scripts\Activate.ps1
```

### Step 3: Install the required tools

```bash
python -m pip install pylint bandit flake8
```

## 6. Running the Application

Execute:

```bash
python address_book.py
```

### Expected Output

```text
Invalid phone number for Test User
No contact named Nobody
1 Kavya Nair 9988776655
2 Neha Sharma 9876543210
3 Rahul Verma 9123456780
Search 'ra': ['Rahul Verma']
By city: {'Bengaluru': ['Neha Sharma', 'Kavya Nair'], 'Chennai': ['Rahul Verma']}
Id for Neha: 8c1a8a
Contacts restored: 3 | first: Kavya Nair
Restored contacts match the in-memory address book: True
```

The output confirms that the application works after the improvements.

## 7. Static Code Analysis

Three tools were used to identify and resolve issues in the original Python code.

### 7.1 Pylint — Code Quality Analysis

Pylint identified:

- Missing module and function docstrings.
- Function and argument naming violations.
- Broad exception handling.
- Inefficient iteration using `range(len())`.
- Missing file encoding specifications.

**Fixes applied:**

- Added descriptive docstrings.
- Renamed functions and arguments using `snake_case`.
- Replaced `except Exception` with `except KeyError`.
- Replaced indexed loops with `enumerate()`.
- Specified UTF-8 encoding.
- Added a main execution guard.

**Result:** Pylint score improved from 5.40/10 to 10.00/10.

### 7.2 Bandit — Security Analysis

Bandit identified four security issues.

| Issue ID | Severity | Description | Fix |
|---|---|---|---|
| B324 | High | Weak MD5 hashing | Replaced with SHA-256 |
| B301 | Medium | Unsafe Pickle deserialization | Replaced with JSON |
| B403 | Low | Potentially unsafe Pickle module | Removed Pickle |
| B105 | Low | Hardcoded password | Removed unused password |

**Result:** Security findings reduced from four to zero.

### 7.3 Flake8 — Style Analysis

Flake8 identified three formatting violations:

| Error Code | Description | Fix |
|---|---|---|
| E225 | Missing whitespace around an operator | Corrected spacing |
| E231 | Missing whitespace after a comma | Corrected spacing |
| E501 | Line exceeded the permitted length | Reformatted long lines |

**Result:** Formatting violations reduced from three to zero.

## 8. Before and After Analysis Results

| Analysis Tool | Before Fixes | After Fixes |
|---|---|---|
| Pylint | 5.40/10 | 10.00/10 |
| Bandit | 4 security issues | 0 security issues |
| Flake8 | 3 formatting violations | 0 formatting violations |

All three analysis tools passed after the code improvements.

## 9. Generating Analysis Reports

### Pylint

```bash
python -m pylint address_book.py > after/pylint_report.txt
```

### Bandit

```bash
python -m bandit -r address_book.py > after/bandit_report.txt
```

### Flake8

```bash
python -m flake8 address_book.py > after/flake8_report.txt
```

The final reports are stored in the `after` directory.

## 10. Issues Documentation

The `issues.md` file documents the problems identified during static analysis.

It includes:

- Issue name and identification code.
- Issue type and severity.
- Original line numbers.
- Description of the problem.
- Fixes applied to resolve the issue.

At least four issues were fixed as required by the lab.

## 11. Reflection

The `reflection.md` file describes:

- What was learned from static code analysis.
- How Pylint, Bandit, and Flake8 improved the program.
- The most important security and code-quality issues resolved.
- How the fixes were verified.

## 12. GitHub Repository

**Repository:** [SE Lab 5 — Address Book Manager](https://github.com/Bhavani-gh/SE_Lab5_Address_Book)

**GitHub Account:** Bhavani-gh

Git is used to track changes to the application, documentation, and analysis reports.

## 13. Learning Outcomes

Through this lab, I learned to:

- Perform static code analysis without executing the source code.
- Identify and resolve security vulnerabilities.
- Improve Python code readability and maintainability.
- Follow PEP 8 coding conventions.
- Interpret Pylint, Bandit, and Flake8 reports.
- Compare code quality before and after improvements.
- Use Git and GitHub for version control.

## 14. Conclusion

The Static Code Analysis lab successfully improved the security, readability, and maintainability of the Contact & Address Book Manager.

The Pylint score improved from **5.40/10 to 10.00/10**, all **four Bandit security findings were resolved**, and all **three Flake8 violations were eliminated**.

The application was tested after modification and retained its intended functionality.

This lab demonstrated how static analysis tools help developers identify potential problems early and maintain better software quality.