# User Authentication Service

## Overview

This project focuses on implementing a user authentication service using Flask, SQLAlchemy, and bcrypt. The goal is to create a secure and functional authentication system, following best practices and industry standards. The project is divided into several tasks, each covering a specific aspect of the authentication service.

## Curriculum

### Short Specializations - User Authentication Service

**Average Score: 122.1%**

**0x03. User authentication service**

**Back-end**

**Authentication**

- **By:** Emmanuel Turlay, Staff Software Engineer at Cruise

**Project Duration:**
- Start: Feb 19, 2024, 6:00 AM
- End: Feb 23, 2024, 6:00 AM

**Checker Release Date:**
- Feb 20, 2024, 6:00 AM

**Auto Review:**
- An auto review will be launched at the deadline

## Learning Objectives

Upon completion of this project, you should be able to explain the following concepts without relying on external resources:

1. Declaration of API routes in a Flask app
2. Handling cookies in a Flask app
3. Retrieving request form data in Flask
4. Returning various HTTP status codes
5. Using SQLAlchemy for database interactions
6. Implementing user authentication and authorization in a secure manner

## Resources

Read or watch:

- Flask documentation
- Requests module
- HTTP status codes

## Requirements

- Allowed editors: vi, vim, emacs
- All files interpreted/compiled on Ubuntu 18.04 LTS using Python 3 (version 3.7)
- Files should end with a new line
- The first line of all files should be exactly `#!/usr/bin/env python3`
- Mandatory README.md file at the root of the project folder
- Code should follow the Pycodestyle style (version 2.5)
- SQLAlchemy version 1.3.x should be used
- All files must be executable
- File lengths will be tested using `wc`
- All modules, classes, and functions should have documentation
- Documentation should be in the form of sentences explaining the purpose of the module, class, or method
- Functions should be type-annotated

## Setup

You will need to install bcrypt:

```bash
pip3 install bcrypt
```

## Tasks

### 0. User model

- Create a SQLAlchemy model named User for a database table named users.
- The model should have attributes: id (integer primary key), email (non-nullable string), hashed_password (non-nullable string), session_id (nullable string), reset_token (nullable string).

### 1. Create user

- Implement the add_user method in the provided DB class.
- This method should add a user to the database, taking email and hashed_password as arguments.
- No validations are required at this stage.

### 2. Find user

- Implement the find_user_by method in the DB class.
- This method should take arbitrary keyword arguments and return the first row found in the users table based on the input arguments.
- Raise NoResultFound and InvalidRequestError when no results are found or when wrong query arguments are passed, respectively.

### 3. Update user

- Implement the update_user method in the DB class.
- This method should take a user_id integer and arbitrary keyword arguments, locate the user using find_user_by, update the user's attributes, and commit changes to the database.
- Raise a ValueError if an argument that does not correspond to a user attribute is passed.

### 4. Hash password

- Define a _hash_password method in the auth module.
- This method should take a password string as an argument and return the salted hash of the input password using bcrypt.hashpw.

### 5. Register user

- Implement the register_user method in the Auth class.
- This method should take mandatory email and password string arguments and return a User object.
- If the user already exists with the provided email, raise a ValueError.
- If not, hash the password using _hash_password, save the user to the database using self._db, and return the User object.

### 6. Basic Flask app

- Set up a basic Flask app with a single GET route ("/") returning a JSON payload: {"message": "Bienvenue"}.
- Add code to run the app if __name__ == "__main__".

### 7. Register user endpoint

- Implement the POST /users endpoint in the app module.
- Use the Auth object to register a user based on form data fields: "email" and "password".
- Respond with JSON payload: {"email": "<registered email>", "message": "user created"} if successful.
- If the user is already registered, respond with JSON payload: {"message": "email already registered"} and return a 400 status code.

### 8. Credentials validation

- Implement the valid_login method in the Auth class.
- Expect email and password as required arguments and return a boolean.
- Locate the user by email and check the password using bcrypt.checkpw. Return True if the password matches, otherwise return False.

### 9. Generate UUIDs

- Implement a _generate_uuid function in the auth module.
- Use the uuid module to generate a string representation of a new UUID.

### 10. Get session ID

- Implement the create_session method in the Auth class.
- Take an email string as an argument and return the session ID as a string.
- Find the user corresponding to the email, generate a new UUID, store it in the database as the user's session_id, and return the session ID.

### 11. Log in

- Implement a login function to respond to the POST /sessions route.
- Expect form data with "email" and "password" fields.
- If the login information is incorrect, respond with a 401 HTTP status.
- If correct, create a new session for the user, store the session ID as a cookie, and return a JSON payload: {"email": "<user email>", "message": "logged in"}.

### 12. Find user by session ID

- Implement the get_user_from_session_id method in the Auth class.
- Take a session_id string as an argument and return the corresponding User or None.
- Return None if the session ID is None or no user is found.

### 13. Destroy session

- Implement the destroy_session method in the Auth class.
- Take a user_id integer as an argument and update the corresponding user's session ID to None.

### 14. Log out

- Implement a logout function to respond to the DELETE /sessions route.
- Expect the session ID as a cookie.
- Find the user with the requested session ID, destroy the session, and redirect the user to GET /.
- If the user does not exist, respond with a 403 HTTP status.

### 15. User profile

- Implement a profile function to respond to the GET /profile route.
- Expect a session_id cookie and use it to find the user.
- If the user exists, respond with a 200 HTTP status and the JSON payload: {"email": "<user email>"}.
- If the session ID is invalid or the user does not exist, respond with a 403 HTTP status.

### 16. Generate reset password token

- Implement the get_reset_password_token method in the Auth class.
- Take an email string as an argument, find the corresponding user, generate a

 new UUID, store it in the database as the user's reset_token, and return the reset token.

### 17. Update password using token

- Implement the update_password_with_token method in the Auth class.
- Take email, reset_token, and new_password as arguments.
- Find the user by email and reset_token, update the user's password, and clear the reset_token.
- Return True if successful, False if the reset_token is invalid.

### 18. Reset password

- Implement a reset_password function to respond to the POST /reset_password route.
- Expect form data with "email" and "password" fields.
- Use the Auth object to generate a reset token and update the user's password.
- If successful, respond with JSON payload: {"email": "<user email>", "message": "password updated"}.
- If the email is not registered, respond with JSON payload: {"message": "email not registered"} and return a 400 status code.

## Final deliverable

- A fully functional Flask app implementing the described user authentication service.
- All necessary dependencies and modules should be included.
- The provided checker will validate your app by testing the implemented functionality.

## Tasks Note

Please make sure to test your code thoroughly before submitting it. The provided checker will check the correctness of your implementation by testing various scenarios and interactions with the authentication service.
