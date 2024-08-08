# Exercise API Documentation

This document provides information about the Exercise API endpoints available in the application.

## Base URL

```
http://localhost:9009/api/exercise
```

## Endpoints

### 1. Create a New Exercise

- **Endpoint:** `POST /create`
- **Description:** Creates a new exercise.

**Request Body:**

```json
{
  "title": "string",
  "description": "string",
  "unit_id": "integer"
}
```

- **title**: The title of the exercise (required).
- **description**: A detailed description of the exercise (required).
- **unit_id**: The ID of the unit to which the exercise belongs (required).

**Response:**

- **201 Created**

```json
{
  "success": true,
  "message": "Exercise was created successfully",
  "data": {
    "id": "integer",
    "title": "string",
    "description": "string",
    "unit_id": "integer"
  }
}
```

- **400 Bad Request**

```json
{
  "success": false,
  "message": "Error message describing the issue"
}
```

### 2. Get All Exercises

- **Endpoint:** `GET /get-all`
- **Description:** Retrieves all exercises.

**Response:**

- **200 OK**

```json
{
  "success": true,
  "message": "Exercises retrieved successfully",
  "data": [
    {
      "id": "integer",
      "title": "string",
      "description": "string",
      "unit_id": "integer",
      "unit": {
        "id": "integer",
        "title": "string"
      }
    }
  ]
}
```

- **404 Not Found**

```json
{
  "success": false,
  "message": "No exercises found"
}
```

### 3. Get an Exercise by ID

- **Endpoint:** `GET /get/:id`
- **Description:** Retrieves a specific exercise by its ID.

**URL Parameters:**

- **id**: The ID of the exercise (required).

**Response:**

- **200 OK**

```json
{
  "success": true,
  "message": "Exercise retrieved successfully",
  "data": {
    "id": "integer",
    "title": "string",
    "description": "string",
    "unit_id": "integer",
    "unit": {
      "id": "integer",
      "title": "string"
    }
  }
}
```

- **404 Not Found**

```json
{
  "success": false,
  "message": "Exercise not found with id {id}"
}
```

### 4. Update an Exercise by ID

- **Endpoint:** `POST /update/:id`
- **Description:** Updates an existing exercise by its ID.

**URL Parameters:**

- **id**: The ID of the exercise (required).

**Request Body:**

```json
{
  "title": "string",
  "description": "string",
  "unit_id": "integer"
}
```

- **title**: The updated title of the exercise (optional).
- **description**: The updated description of the exercise (optional).
- **unit_id**: The updated unit ID associated with the exercise (optional).

**Response:**

- **200 OK**

```json
{
  "success": true,
  "message": "Exercise updated successfully",
  "data": {
    "id": "integer",
    "title": "string",
    "description": "string",
    "unit_id": "integer"
  }
}
```

- **404 Not Found**

```json
{
  "success": false,
  "message": "Exercise not found with id {id}"
}
```

### 5. Delete an Exercise by ID

- **Endpoint:** `DELETE /delete/:id`
- **Description:** Deletes an exercise by its ID.

**URL Parameters:**

- **id**: The ID of the exercise (required).

**Response:**

- **200 OK**

```json
{
  "success": true,
  "message": "Exercise deleted successfully"
}
```

- **404 Not Found**

```json
{
  "success": false,
  "message": "Exercise not found with id {id}"
}
```

## Middleware

### Validation Middleware

- **`validateExercise`**: Middleware to validate the request body for creating or updating an exercise. Ensures that required fields are provided and have valid values.

- **`validateRequest`**: Middleware to handle validation errors and send appropriate responses.

## Example Requests

- **Creating an Exercise**

```bash
curl -X POST http://localhost:9009/api/exercise/create \
-H "Content-Type: application/json" \
-d '{"title": "New Exercise", "description": "Details about the exercise", "unit_id": 1}'
```

- **Getting All Exercises**

```bash
curl -X GET http://localhost:9009/api/exercise/get-all
```

- **Getting an Exercise by ID**

```bash
curl -X GET http://localhost:9009/api/exercise/get/1
```

- **Updating an Exercise**

```bash
curl -X POST http://localhost:9009/api/exercise/update/1 \
-H "Content-Type: application/json" \
-d '{"title": "Updated Exercise", "description": "Updated details", "unit_id": 2}'
```

- **Deleting an Exercise**

```bash
curl -X DELETE http://localhost:9009/api/exercise/delete/1
```

---
