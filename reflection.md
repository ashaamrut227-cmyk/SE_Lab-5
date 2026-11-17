# SE Lab 5 — Static Code Analysis Reflection

### 1. What did you learn from static code analysis?

I learned that static code analysis helps identify bugs, security vulnerabilities and coding-style problems without executing the program. It improves code quality, readability, security and maintainability.

### 2. How did Pylint, Bandit and Flake8 help improve your code?

**Pylint:** Identified naming convention violations, missing docstrings, broad exception handling and inefficient loops. After fixing these issues, my Pylint score improved from 5.40/10 to 10.00/10.

**Bandit:** Identified four security issues, including weak MD5 hashing, unsafe Pickle deserialization and a hardcoded password. After applying the fixes, Bandit reported zero issues.

**Flake8:** Identified three formatting violations involving whitespace and line length. After correcting the formatting, Flake8 reported zero violations.

### 3. What were the most important issues you fixed?

The most important security issues were weak MD5 hashing and unsafe Pickle deserialization.

I replaced MD5 with SHA-256 and replaced Pickle backup and restoration with JSON. I also removed the unused hardcoded password and improved exception handling.

These changes reduced the security risks identified by Bandit.

### 4. How did you verify that your fixes were successful?

I reran the Python program after making the changes and confirmed that the address book operations still worked correctly.

I also reran all three static analysis tools and compared their results with the original reports.

| Tool | Before | After |
|---|---|---|
| Pylint | 5.40/10 | 10.00/10 |
| Bandit | 4 issues | 0 issues |
| Flake8 | 3 violations | 0 violations |

The final results showed that the identified issues were resolved while preserving the program's functionality.

## Conclusion

This lab helped me understand the importance of writing secure, readable and maintainable Python code. I learned how to use Pylint, Bandit and Flake8 to detect issues, apply fixes and verify improvements.