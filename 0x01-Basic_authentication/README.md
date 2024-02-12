# README.md for Basic Authentication Project

## Overview

This project focuses on implementing Basic Authentication for a simple API. The purpose is to understand the authentication process and gain insights into Base64 encoding, HTTP headers, and the Flask framework.

## Learning Objectives

By the end of this project, you should be able to explain:

- What authentication means
- What Base64 is
- How to encode a string in Base64
- What Basic authentication means
- How to send the Authorization header

## Project Structure

The project is organized into several tasks, each building upon the previous one. Here's an overview of the tasks:

### Task 0: Simple Basic API

Set up and start a simple API with a User model. The storage of users is done via serialization/deserialization in files. The focus is on understanding the API setup.

### Task 1: Error Handler - Unauthorized

Implement an error handler for HTTP status code 401 (Unauthorized). Create an endpoint that raises a 401 error for testing purposes.

### Task 2: Error Handler - Forbidden

Implement an error handler for HTTP status code 403 (Forbidden). Create an endpoint that raises a 403 error for testing purposes.

### Task 3: Auth Class

Create a class named `Auth` to manage API authentication. The class includes methods for requiring authentication, handling authorization headers, and retrieving the current user.

### Task 4: Define Routes Without Authentication

Update the `require_auth` method in the `Auth` class to define routes that don't need authentication. Paths ending with a slash should be treated slash-tolerantly.

### Task 5: Request Validation

Validate all requests to secure the API. Implement checks in the `before_request` method to ensure proper authentication, authorization, and user validation.

### Task 6: Basic Auth

Create a class named `BasicAuth` that inherits from `Auth`. This class will serve as the template for Basic Authentication. Update the API to use `BasicAuth` based on the `AUTH_TYPE` environment variable.

### Task 7: Basic - Base64 Part

Implement methods in the `BasicAuth` class to extract the Base64 part of the Authorization header.

### Task 8: Basic - Base64 Decode

Implement a method in the `BasicAuth` class to decode the Base64 Authorization header.

### Task 9: Basic - User Credentials

Implement a method in the `BasicAuth` class to extract user credentials from the decoded Base64 Authorization header.

### Task 10: Basic - User Object

Implement a method in the `BasicAuth` class to retrieve the User instance based on email and password.

### Task 11: Overload Current User

Overload the `current_user` method in the `BasicAuth` class to retrieve the User instance for a request using the implemented authentication methods.

### Task 12: Allow Password with ":"

Improve the method to allow passwords with colons.

### Task 13: Require Auth with Stars

Enhance the `require_auth` method to allow the use of asterisks (*) at the end of excluded paths for a more flexible authentication setup.

## Getting Started

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/alx-backend-user-data.git
   ```

2. Install dependencies:

   ```bash
   pip3 install -r requirements.txt
   ```

3. Start the API:

   ```bash
   API_HOST=0.0.0.0 API_PORT=5000 python3 -m api.v1.app
   ```

4. Test the API using `curl` or a web browser.

## Testing

To test the implemented features, use `curl` or a tool of your choice to interact with the API endpoints. Refer to the specific task descriptions for testing examples.

```bash
curl "http://0.0.0.0:5000/api/v1/your-endpoint"
```

## Notes

- Ensure that your code adheres to the specified coding style using `pycodestyle`.
- Provide proper documentation for your modules, classes, and functions.
- Keep the README updated with any additional information or changes to the project.

