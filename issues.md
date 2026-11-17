# SE Lab 5 — Static Code Analysis: Issues Identified

| Issue | Type | Original Line | Description | Fix Approach |
|---|---|---|---|---|
| B324 — Weak MD5 | Security (High) | 19 | MD5 is a weak hashing algorithm. | Replaced MD5 with SHA-256. |
| B301 — Unsafe deserialization | Security (Medium) | 67 | Loading Pickle data can execute malicious code. | Replaced `pickle.load()` with `json.load()`. |
| B403 — Pickle import | Security (Low) | 3 | Pickle can introduce security risks when handling untrusted data. | Replaced Pickle with JSON. |
| B105 — Hardcoded password | Security (Low) | 6 | A password was stored directly in the source code. | Removed the unused hardcoded password. |
| C0103 — Invalid naming | Code Quality | Multiple | Function and argument names did not follow snake_case. | Renamed functions and arguments. |
| C0116 — Missing docstrings | Documentation | Multiple | Functions lacked descriptions. | Added function docstrings. |
| W0718 — Broad exception | Code Quality | 35 | Catching all exceptions can hide unexpected errors. | Replaced `except Exception` with `except KeyError`. |
| C0200 — Inefficient iteration | Code Quality | 49 | Used `range(len())` to iterate over contacts. | Replaced with `enumerate()`. |
| W1514 — Missing encoding | Code Quality | 54 | CSV file was opened without specifying encoding. | Added `encoding="utf-8"`. |
| E225, E231, E501 | Formatting | Multiple | Incorrect whitespace and long lines. | Corrected formatting to follow PEP 8. |

## Results

| Tool | Before | After |
|---|---|---|
| Pylint | 5.40/10 | 10.00/10 |
| Bandit | 4 issues | 0 issues |
| Flake8 | 3 violations | 0 violations |

## Conclusion

Static code analysis helped identify security vulnerabilities, code quality problems and formatting issues without executing the program. The corrected address book maintains its original functionality while improving security, readability and maintainability.