Got it! Here's the revised API documentation tailored for a web development context:

---

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
http://localhost:9009/api/exercises
```

**Request Body:**
```json
{
  "title": "Understanding Web Development Basics",
  "description": "This exercise covers fundamental concepts in web development, including HTML, CSS, and JavaScript.",
  "unit_id": 12345,
  "questions": [
    {
      "question": "What does HTML stand for?",
      "solution": "HyperText Markup Language",
      "choices": [
        { "text": "HyperText Markup Language", "is_correct": true },
        { "text": "HyperText Management Language", "is_correct": false },
        { "text": "HyperText Markdown Language", "is_correct": false },
        { "text": "HyperText Multi Language", "is_correct": false }
      ]
    },
    {
      "question": "Which property is used to change the background color in CSS?",
      "solution": "background-color",
      "choices": [
        { "text": "color", "is_correct": false },
        { "text": "background-color", "is_correct": true },
        { "text": "bgcolor", "is_correct": false },
        { "text": "background", "is_correct": false }
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
      "title": "Understanding Web Development Basics",
      "description": "This exercise covers fundamental concepts in web development, including HTML, CSS, and JavaScript.",
      "unit_id": 12345
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
http://localhost:9009/api/exercises
```

**Responses:**

- **200 OK**
  ```json
  {
    "success": true,
    "data": [
      {
        "id": 1,
        "title": "Understanding Web Development Basics",
        "description": "This exercise covers fundamental concepts in web development, including HTML, CSS, and JavaScript.",
        "unit_id": 12345,
        "questions": [
          {
            "id": 1,
            "question": "What does HTML stand for?",
            "solution": "HyperText Markup Language",
            "choices": [
              { "id": 1, "exercise_choice_text": "HyperText Markup Language", "is_correct": true },
              { "id": 2, "exercise_choice_text": "HyperText Management Language", "is_correct": false },
              { "id": 3, "exercise_choice_text": "HyperText Markdown Language", "is_correct": false },
              { "id": 4, "exercise_choice_text": "HyperText Multi Language", "is_correct": false }
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
http://localhost:9009/api/exercises/:id
```

Replace `:id` with the actual exercise ID.

**Responses:**

- **200 OK**
  ```json
  {
    "success": true,
    "data": {
      "id": 1,
      "title": "Understanding Web Development Basics",
      "description": "This exercise covers fundamental concepts in web development, including HTML, CSS, and JavaScript.",
      "unit_id": 12345,
      "questions": [
        {
          "id": 1,
          "question": "What does HTML stand for?",
          "solution": "HyperText Markup Language",
          "choices": [
            { "id": 1, "exercise_choice_text": "HyperText Markup Language", "is_correct": true },
            { "id": 2, "exercise_choice_text": "HyperText Management Language", "is_correct": false },
            { "id": 3, "exercise_choice_text": "HyperText Markdown Language", "is_correct": false },
            { "id": 4, "exercise_choice_text": "HyperText Multi Language", "is_correct": false }
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
http://localhost:9009/api/exercises/:id
```

Replace `:id` with the actual exercise ID.

**Request Body:**
```json
{
  "title": "Advanced Web Development Concepts",
  "description": "Updated description of web development exercise.",
  "unit_id": 12346,
  "questions": [
    {
      "id": 1,
      "question": "What is the purpose of JavaScript in web development?",
      "solution": "To add interactivity to web pages.",
      "choices": [
        { "id": 1, "text": "To style web pages.", "is_correct": false },
        { "id": 2, "text": "To structure web pages.", "is_correct": false },
        { "id": 3, "text": "To add interactivity to web pages.", "is_correct": true },
        { "id": 4, "text": "To handle server-side logic.", "is_correct": false }
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
      "title": "Advanced Web Development Concepts",
      "description": "Updated description of web development exercise.",
      "unit_id": 12346
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
http://localhost:9009/api/exercises/:id
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

---


