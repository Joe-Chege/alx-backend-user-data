# ALX Back-end User Data Project

## Project Overview

This project focuses on implementing back-end authentication features and data security practices. The tasks involve handling personally identifiable information (PII), implementing log filtering, encrypting passwords, and connecting to a secure database.

### Contributor

- **Emmanuel Turlay**
  - Staff Software Engineer at Cruise

### Project Details

- **Weight:** 1
- **Project Start:** Feb 7, 2024, 6:00 AM
- **Project End:** Feb 9, 2024, 6:00 AM
- **Checker Release:** Feb 7, 2024, 6:00 PM
- **QA Review:** Manual review required (request it upon project completion)
- **Auto Review:** Will be launched at the deadline

## Learning Objectives

By the end of this project, you are expected to be able to explain to anyone, without the help of Google:

1. Examples of Personally Identifiable Information (PII).
2. How to implement a log filter that will obfuscate PII fields.
3. How to encrypt a password and check the validity of an input password.
4. How to authenticate to a database using environment variables.

## Requirements

- **Interpreter/Compiler:** Ubuntu 18.04 LTS with Python 3.7
- **File Format:** All files should end with a new line.
- **Shebang:** The first line of all files should be `#!/usr/bin/env python3`.
- **README.md:** A mandatory file at the root of the project folder.
- **Coding Style:** Use pycodestyle style (version 2.5).
- **Executable:** All files must be executable.
- **File Length:** The length of your files will be tested using `wc`.
- **Documentation:**
  - All modules, classes, and functions should have documentation.
  - Documentation should be a real sentence explaining the purpose of the module, class, or method.
  - Documentation length will be verified.
- **Type Annotations:** All functions should be type-annotated.

## Tasks

### 0. Regex-ing

Write a function called `filter_datum` that returns the log message obfuscated.

#### Arguments:

- `fields`: a list of strings representing all fields to obfuscate
- `redaction`: a string representing by what the field will be obfuscated
- `message`: a string representing the log line
- `separator`: a string representing by which character is separating all fields in the log line (message)

The function should use a regex to replace occurrences of certain field values.

### 1. Log formatter

Update the `RedactingFormatter` class to accept a list of strings `fields` constructor argument. Implement the `format` method to filter values in incoming log records using `filter_datum`. Values for fields in `fields` should be filtered.

### 2. Create logger

Implement a `get_logger` function that takes no arguments and returns a `logging.Logger` object. The logger should be named "user_data" and only log up to `logging.INFO` level. It should not propagate messages to other loggers. It should have a `StreamHandler` with `RedactingFormatter` as formatter.

Create a tuple `PII_FIELDS` constant at the root of the module containing the fields from `user_data.csv` that are considered PII.

### 3. Connect to secure database

Implement a `get_db` function that returns a connector to the database (`mysql.connector.connection.MySQLConnection` object). Use the os module to obtain credentials from the environment and use the module `mysql-connector-python` to connect to the MySQL database.

### 4. Read and filter data

Implement a `main` function that obtains a database connection using `get_db` and retrieves all rows in the `users` table. Display each row under a filtered format.

### 5. Encrypting passwords

Implement a `hash_password` function that expects one string argument `password` and returns a salted, hashed password, which is a byte string. Use the `bcrypt` package to perform the hashing.

### 6. Check valid password

Implement an `is_valid` function that expects 2 arguments and returns a boolean. Use bcrypt to validate that the provided password matches the hashed password.

## Usage

1. Clone the repository: `git clone https://github.com/your-username/alx-backend-user-data.git`
2. Navigate to the project directory: `cd alx-backend-user-data`
3. Install dependencies: `pip install -r requirements.txt`

## Contribution Guidelines

1. Fork the repository on GitHub.
2. Create a new branch with a descriptive name: `git checkout -b feature-name`.
3. Make your changes and commit them: `git commit -m 'Implement authentication feature'`.
4. Push your changes to the branch: `git push origin feature-name`.
5. Submit a pull request on GitHub.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

*Copyright © 2024 ALX, All rights reserved.*