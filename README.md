# API Documentation: Get Course Code by Roll Number

## API Endpoint

**GET** `https://api.fai.codes/apars/profile/user/{roll}`

This API allows you to retrieve the course codes associated with a users profile, given their roll number.

---

## Request Parameters

- **roll** (required): The roll number of the user whose courses are to be retrieved.

---

## Example Request

**URL Format**:  
`https://api.fai.codes/apars/profile/user/{roll}`

**Example URL**:  
`https://api.fai.codes/apars/profile/user/491905`

---

## Response

The API returns a JSON object containing the users roll number and the list of course codes they are enrolled in.

### Success Response

- **Status**: `200 OK`
- **Content-Type**: `application/json`

```json
{
  "roll": "491905",
  "courseCodes": [
    "352",
    "353",
    "302",
    "301",
    "300"
  ]
}
```
---

### Error Responses

- **Status**: `404 Not Found`  

  - **Reason**: User with the provided roll number not found.  
  - **Example Response**:  
    ```json
    {
      "error": "User not found"
    }
    ```
---

- **Status**: `500 Internal Server Error`  

  - **Reason**: There was an issue with the server, such as a database connection failure.  
  - **Example Response**:  
    ```json
    {
      "error": "Internal server error"
    }
    ```
---

### CORS Policy

This API enforces a CORS policy, allowing requests only from authorized domains. Unauthorized domains will be blocked.

---
### Authentication

This API does not require any authentication tokens, but it requires valid roll numbers that exist in the system.

---

### Error Handling

- Ensure the roll number provided exists in the database to avoid `404 Not Found` errors.
- If the database is unavailable or there are internal server issues, a `500 Internal Server Error` will be returned.
