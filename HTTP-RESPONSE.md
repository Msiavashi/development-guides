
### Error Response Format

**HTTP Status Codes:**

- `400 Bad Request`: Invalid client request (e.g., missing or invalid parameters).
- `401 Unauthorized`: Authentication failure.
- `403 Forbidden`: Authorization failure.
- `404 Not Found`: Resource not found.
- `422 Unprocessable Entity`: Request contains semantic errors (e.g., validation errors).
- `500 Internal Server Error`: Unexpected server error.

**Response Body Format (JSON):**

```json
{
  "status": "error",
  "message": "A human-readable error message describing the issue.",
  "code": "UNIQUE_ERROR_CODE",  // Unique error code (optional)
  "details": {
    "field1": "Details about the error for field1 (optional)",
    "field2": "Details about the error for field2 (optional)",
    // Additional error details as needed
  }
}
```

**Examples:**

1. **Invalid Input Data (400 Bad Request)**

   ```json
   {
     "status": "error",
     "message": "Invalid input data.",
     "code": "INVALID_INPUT",
     "details": {
       "email": "Email address is not valid.",
       "password": "Password must be at least 8 characters."
     }
   }
   ```

2. **Authentication Failure (401 Unauthorized)**

   ```json
   {
     "status": "error",
     "message": "Authentication failed. Please provide valid credentials.",
     "code": "AUTH_FAILURE"
   }
   ```

3. **Permission Denied (403 Forbidden)**

   ```json
   {
     "status": "error",
     "message": "Permission denied. You do not have the necessary access rights.",
     "code": "PERMISSION_DENIED"
   }
   ```

4. **Resource Not Found (404 Not Found)**

   ```json
   {
     "status": "error",
     "message": "The requested resource was not found.",
     "code": "RESOURCE_NOT_FOUND"
   }
   ```

5. **Validation Error (422 Unprocessable Entity)**

   ```json
   {
     "status": "error",
     "message": "Validation failed for the request.",
     "code": "VALIDATION_ERROR",
     "details": {
       "field1": "Value is required.",
       "field2": "Value must be a positive integer."
     }
   }
   ```

6. **Server Error (500 Internal Server Error)**

   ```json
   {
     "status": "error",
     "message": "An unexpected server error occurred. Please try again later.",
     "code": "SERVER_ERROR"
   }
   ```

### Success Response Format (Nested Data)

**HTTP Status Code:**

- `200 OK`: Successful GET request.
- `201 Created`: Successful POST request resulting in a new resource.
- `204 No Content`: Successful request with no response body (e.g., successful DELETE).

**Response Body Format (JSON):**

```json
{
  "status": "success",
  "data": {
    "user": {
      // Data representing the successful response
    }
  }
}
```

**Example:**

- **Successful User Retrieval (200 OK)**

   ```json
   {
     "status": "success",
     "data": {
       "user": {
         "user_id": 12345,
         "username": "john_doe",
         "email": "john@example.com"
       }
     }
   }
   ```

### Warning Response Format

**HTTP Status Code:**

- `200 OK`: Successful request with a warning message.

**Response Body Format (JSON):**

```json
{
  "status": "warning",
  "message": "A human-readable warning message describing the issue.",
  "code": "UNIQUE_WARNING_CODE",  // Unique warning code (optional)
  "details": {
    "field1": "Details about the warning for field1 (optional)",
    "field2": "Details about the warning for field2 (optional)",
    // Additional warning details as needed
  }
}
```

**Example:**

- **Unusual User Activity Detected (200 OK with Warning)**

   ```json
   {
     "status": "warning",
     "message": "Unusual user activity detected.",
     "code": "UNUSUAL_ACTIVITY",
     "details": {
       "ip_address": "192.168.1.100",
       "reason": "Multiple login attempts within a short time."
     }
   }
   ```

### Informational Response Format

**HTTP Status Code:**

- `200 OK`: Successful request with an informational message.

**Response Body Format (JSON):**

```json
{
  "status": "info",
  "message": "A human-readable informational message.",
  "code": "UNIQUE_INFO_CODE",  // Unique informational code (optional)
  "details": {
    "field1": "Details about the informational message for field1 (optional)",
    "field2": "Details about the informational message for field2 (optional)",
    // Additional informational details as needed
  }
}
```

**Example:**

- **Account Update Successful (200 OK with Info)**

   ```json
   {
     "status": "info",
     "message": "Account update successful.",
     "code": "ACCOUNT_UPDATE",
     "details": {
       "username": "new_username",
       "email": "new_email@example.com"
     }
   }
   ```
