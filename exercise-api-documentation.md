# Exercise API Documentation

This document provides information about the Exercise API endpoints available in the application.

## Base URL

```
http://localhost:9009/api
```

#### **1. Create a New Exercise**

**Endpoint:** `POST /exercises`

**Description:** Create a new exercise with associated questions and choices.

**Request URL:**
```
http://127.0.0.1:9009/api/exercises
```

**Request Body:**
```json
{
  "title": "Cell Biology Fundamentals",
  "description": "This exercise covers key concepts in cell biology, including cell structure and function.",
  "unit_id": 3335438,
  "questions": [
    {
      "question": "Which organelle is known as the powerhouse of the cell?",
      "solution": "Mitochondria",
      "choices": [
        { "text": "Nucleus", "is_correct": false },
        { "text": "Endoplasmic Reticulum", "is_correct": false },
        { "text": "Mitochondria", "is_correct": true },
        { "text": "Golgi Apparatus", "is_correct": false }
      ]
    },
    {
      "question": "What is the primary function of the cell membrane?",
      "solution": "To regulate what enters and exits the cell.",
      "choices": [
        { "text": "To provide structural support to the cell.", "is_correct": false },
        { "text": "To regulate what enters and exits the cell.", "is_correct": true },
        { "text": "To store genetic information.", "is_correct": false },
        { "text": "To synthesize proteins.", "is_correct": false }
      ]
    }
  ]
}
```

**Responses:**

- **201 Created**
  ```json
  {
    "success": true,
    "message": "Exercise and associated data created successfully",
    "data": {
      "id": 1,
      "title": "Cell Biology Fundamentals",
      "description": "This exercise covers key concepts in cell biology, including cell structure and function.",
      "unit_id": 3335438
    }
  }
  ```

- **400 Bad Request** (for invalid data)
  ```json
  {
    "success": false,
    "message": "Validation error message"
  }
  ```

#### **2. Get All Exercises**

**Endpoint:** `GET /exercises`

**Description:** Retrieve all exercises with their associated questions and choices.

**Request URL:**
```
http://127.0.0.1:9009/api/exercises
```

**Responses:**

- **200 OK**
  ```json
  {
    "success": true,
    "data": [
      {
        "id": 1,
        "title": "Cell Biology Fundamentals",
        "description": "This exercise covers key concepts in cell biology, including cell structure and function.",
        "unit_id": 3335438,
        "questions": [
          {
            "id": 1,
            "question": "Which organelle is known as the powerhouse of the cell?",
            "solution": "Mitochondria",
            "choices": [
              { "id": 1, "exercise_choice_text": "Nucleus", "is_correct": false },
              { "id": 2, "exercise_choice_text": "Endoplasmic Reticulum", "is_correct": false },
              { "id": 3, "exercise_choice_text": "Mitochondria", "is_correct": true },
              { "id": 4, "exercise_choice_text": "Golgi Apparatus", "is_correct": false }
            ]
          }
        ]
      }
    ]
  }
  ```

- **404 Not Found** (if no exercises exist)
  ```json
  {
    "success": false,
    "message": "No exercises found"
  }
  ```

#### **3. Get Exercise by ID**

**Endpoint:** `GET /exercises/:id`

**Description:** Retrieve an exercise by ID with its associated questions and choices.

**Request URL:**
```
http://127.0.0.1:9009/api/exercises/:id
```

Replace `:id` with the actual exercise ID.

**Responses:**

- **200 OK**
  ```json
  {
    "success": true,
    "data": {
      "id": 1,
      "title": "Cell Biology Fundamentals",
      "description": "This exercise covers key concepts in cell biology, including cell structure and function.",
      "unit_id": 3335438,
      "questions": [
        {
          "id": 1,
          "question": "Which organelle is known as the powerhouse of the cell?",
          "solution": "Mitochondria",
          "choices": [
            { "id": 1, "exercise_choice_text": "Nucleus", "is_correct": false },
            { "id": 2, "exercise_choice_text": "Endoplasmic Reticulum", "is_correct": false },
            { "id": 3, "exercise_choice_text": "Mitochondria", "is_correct": true },
            { "id": 4, "exercise_choice_text": "Golgi Apparatus", "is_correct": false }
          ]
        }
      ]
    }
  }
  ```

- **404 Not Found** (if the exercise with the given ID does not exist)
  ```json
  {
    "success": false,
    "message": "Exercise not found"
  }
  ```

#### **4. Update an Existing Exercise**

**Endpoint:** `PUT /exercises/:id`

**Description:** Update an existing exercise along with its associated questions and choices.

**Request URL:**
```
http://127.0.0.1:9009/api/exercises/:id
```

Replace `:id` with the actual exercise ID.

**Request Body:**
```json
{
  "title": "Updated Cell Biology Fundamentals",
  "description": "Updated description of cell biology exercise.",
  "unit_id": 3335439,
  "questions": [
    {
      "id": 1,
      "question": "What is the new primary function of the cell membrane?",
      "solution": "Updated solution",
      "choices": [
        { "id": 1, "text": "To provide structural support to the cell.", "is_correct": false },
        { "id": 2, "text": "To regulate what enters and exits the cell.", "is_correct": true },
        { "id": 3, "text": "To store genetic information.", "is_correct": false },
        { "id": 4, "text": "To synthesize proteins.", "is_correct": false }
      ]
    }
  ]
}
```

**Responses:**

- **200 OK**
  ```json
  {
    "success": true,
    "message": "Exercise and associated data updated successfully",
    "data": {
      "id": 1,
      "title": "Updated Cell Biology Fundamentals",
      "description": "Updated description of cell biology exercise.",
      "unit_id": 3335439
    }
  }
  ```

- **404 Not Found** (if the exercise with the given ID does not exist)
  ```json
  {
    "success": false,
    "message": "Exercise not found"
  }
  ```

- **400 Bad Request** (for invalid data)
  ```json
  {
    "success": false,
    "message": "Validation error message"
  }
  ```

#### **5. Delete an Exercise**

**Endpoint:** `DELETE /exercises/:id`

**Description:** Delete an exercise along with its associated questions and choices.

**Request URL:**
```
http://127.0.0.1:9009/api/exercises/:id
```

Replace `:id` with the actual exercise ID.

**Responses:**

- **200 OK**
  ```json
  {
    "success": true,
    "message": "Exercise and associated data deleted successfully"
  }
  ```

- **404 Not Found** (if the exercise with the given ID does not exist)
  ```json
  {
    "success": false,
    "message": "Exercise not found"
  }
  ```

