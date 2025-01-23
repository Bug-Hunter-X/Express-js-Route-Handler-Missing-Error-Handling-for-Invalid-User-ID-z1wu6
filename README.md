# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers: missing error handling for invalid input.  Specifically, the code attempts to parse a user ID as an integer without checking if the ID is actually a number. This can lead to unexpected crashes or exceptions.

## Bug

The `bug.js` file contains the erroneous code. The route handler for `/users/:id` attempts to find a user based on the ID provided in the request parameters.  It converts the ID to an integer using `parseInt()`, but doesn't handle the case where the ID is not a valid integer. If a non-numeric ID is provided, `parseInt()` will return `NaN`, leading to an error when comparing it to user IDs.

## Solution

The `bugSolution.js` file provides a corrected version of the code.  It includes error handling to check if the ID is a valid number before attempting to find the user.  If the ID is not a valid number, it returns a 400 Bad Request response.  Otherwise, it proceeds as before, returning the user or a 404 Not Found response if no user is found.