# Project README

## Curriculum - Session Authentication

### Short Specializations
- **Average:** 117.68%
- **0x02. Session authentication**
  - **Back-end**
  - **Authentication**
  - **By: Guillaume, CTO at Holberton School**
  - **Weight: 1**
  - **Project Duration: Feb 14, 2024, 6:00 AM to Feb 16, 2024, 6:00 AM**
  - **Auto Review Deadline: Feb 16, 2024, 6:00 AM**

### In a nutshell…
- **Auto QA review:**
  - **0.0/135 mandatory & 0.0/46 optional**
- **Altogether: 0.0%**
  - **Mandatory: 0.0%**
  - **Optional: 0.0%**
- **Calculation: 0.0% + (0.0% * 0.0%) == 0.0%**

### Background Context
In this project, you will implement Session Authentication. You are not allowed to install any other module.

In the industry, you should not implement your own Session authentication system and use a module or framework that does it for you (like in Python-Flask: Flask-HTTPAuth). Here, for the learning purpose, we will walk through each step of this mechanism to understand it by doing.

### Resources
- **Read or watch:**
  - [REST API Authentication Mechanisms - Only the session auth part](#)
  - [HTTP Cookie](#)
  - [Flask](#)
  - [Flask Cookie](#)

### Learning Objectives
At the end of this project, you are expected to be able to explain to anyone, without the help of Google:
#### General
- What authentication means
- What session authentication means
- What Cookies are
- How to send Cookies
- How to parse Cookies

### Requirements

#### Python Scripts
- All your files will be interpreted/compiled on Ubuntu 18.04 LTS using python3 (version 3.7)
- All your files should end with a new line
- The first line of all your files should be exactly `#!/usr/bin/env python3`
- A `README.md` file, at the root of the folder of the project, is mandatory
- Your code should use the `pycodestyle` style (version 2.5)
- All your files must be executable
- The length of your files will be tested using `wc`
- All your modules should have documentation (`python3 -c 'print(__import__("my_module").__doc__)'`)
- All your classes should have documentation (`python3 -c 'print(__import__("my_module").MyClass.__doc__)'`)
- All your functions (inside and outside a class) should have documentation (`python3 -c 'print(__import__("my_module").my_function.__doc__)'` and `python3 -c 'print(__import__("my_module").MyClass.my_function.__doc__)'`)
- A documentation is not a simple word, it’s a real sentence explaining what’s the purpose of the module, class, or method (the length of it will be verified)

## Tasks

### 0. Et moi et moi et moi!
#### Mandatory
- **Score:** 0.0%
- **Checks completed:** 0.0%

Copy all your work from the 0x06. Basic authentication project into this new folder.

...

### 7. New view for Session Authentication
#### Mandatory
- **Score:** 0.0%
- **Checks completed:** 0.0%

Create a new Flask view that handles all routes for the Session authentication.

In the file `api/v1/views/session_auth.py`, create a route `POST /auth_session/login` (`POST /api/v1/auth_session/login`):

- Slash tolerant (`/auth_session/login` == `/auth_session/login/`)
- You must use `request.form.get()` to retrieve email and password parameters
- If email is missing or empty, return the JSON `{ "error": "email missing" }` with the status code 400
- If password is missing or empty, return the JSON `{ "error": "password missing" }` with the status code 400
- Retrieve the User instance based on the email - you must use the class method `search` of `User` (same as the one used for the `BasicAuth`)
- If no User is found, return the JSON `{ "error": "no user found for this email" }` with the status code 404
- If the password is not the one of the User found, return the JSON `{ "error": "wrong password" }` with the status code 401 - you must use `is_valid_password` from the `User` instance
- Otherwise, create a Session ID for the User ID:
  - You must use `from api.v1.app import auth` - WARNING: please import it only where you need it -

 If you want to know why, ask in the linkedin thread!
  - Create a Session ID - you must use `auth.create_session(user_id)` - that will return your Session ID
  - Update the User's session ID with the new created Session ID
  - Return the JSON `{ "user_id": "<user_id>", "session_id": "<session_id>" }` with the status code 200
...

### General Instructions
- Copy all your work from the 0x06. Basic authentication project into this new folder.
- You will work on your new folder.
- Your code should not be executed when imported.
- We recommend you use the "requests" module to test your code (`requests.get('http://127.0.0.1:5000/auth')`)
- Important: after cloning your project from the "starting" repository:
  - Create a new branch
  - Name this branch with the usual format: `lastname/firstname-feature` (example: `stewart/alex-feature`)
  - You will push this branch throughout the project to the remote. Never push the main branch!
  - Create a new file `__init__.py` in your folder `api/v1`


---

This project involves implementing session authentication using Flask in Python. It requires creating routes for session authentication, handling user login, and managing session IDs. The instructions provide detailed information on the tasks to be completed, including creating new views, handling different error scenarios, and updating user session IDs. The project also emphasizes documentation, code organization, and style adherence.

To successfully complete this project, you should have knowledge of Flask, HTTP cookies, and session authentication mechanisms. Additionally, it is essential to follow the provided instructions for code structure, documentation, and testing.