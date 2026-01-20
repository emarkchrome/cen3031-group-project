# API Documentation

This document outlines the API endpoints available in the StudySmart backend.

## Base URL
All endpoints are relative to the server's base URL (e.g., `http://localhost:3000`).

## Endpoints

### 1. Extract Text from PDF
Extracts text content from an uploaded PDF file.

- **URL**: `/api/extract-text`
- **Method**: `POST`
- **Content-Type**: `multipart/form-data`
- **Body Parameters**:
  - `pdf`: The PDF file to be processed.

- **Success Response**:
  - **Code**: 200 OK
  - **Content**:
    ```json
    {
      "text": "Extracted text content from the PDF..."
    }
    ```

- **Error Response**:
  - **Code**: 400 Bad Request
  - **Content**: `{ "error": "No file uploaded" }`

### 2. Generate Study Content
Generates summaries, flashcards, or quizzes using OpenAI based on provided text.

- **URL**: `/api/generate-content`
- **Method**: `POST`
- **Content-Type**: `application/json`
- **Body Parameters**:
  - `text` (string): The text content to generate study aids from.
  - `mode` (string, optional): The specific type of content to return (`summary`, `flashcards`, or `quiz`). If omitted, returns all.

- **Success Response**:
  - **Code**: 200 OK
  - **Content**:
    ```json
    {
      "summary": "Concise summary...",
      "flashcards": [
        { "question": "...", "answer": "..." }
      ],
      "quiz": [
        { "question": "...", "options": [...], "answer": "..." }
      ]
    }
    ```

### 3. Fetch User Study Materials
Retrieves all study materials (summaries, flashcards, quizzes) for a specific user.

- **URL**: `/api/study-materials/:userId`
- **Method**: `GET`
- **URL Parameters**:
  - `userId`: The ID of the user.

- **Success Response**:
  - **Code**: 200 OK
  - **Content**:
    ```json
    {
      "summaries": [...],
      "flashcards": [...],
      "quizzes": [...]
    }
    ```

### 4. Save Study Content
Saves generated study content to the database.

- **URL**: `/api/save-study-content`
- **Method**: `POST`
- **Content-Type**: `application/json`
- **Body Parameters**:
  - `title` (string): Title of the content.
  - `type` (string): Type of content (`summary`, `flashcards`, `quiz`).
  - `content` (object): The actual content data.
  - `timestamp` (string): Creation timestamp.
  - `fileName` (string): Source filename.
  - `userId` (string): ID of the user.

- **Success Response**:
  - **Code**: 201 Created
  - **Content**:
    ```json
    {
      "message": "Study content saved successfully",
      "savedContent": { ... }
    }
    ```

### 5. Create User
Registers a new user in the database.

- **URL**: `/api/user`
- **Method**: `POST`
- **Content-Type**: `application/json`
- **Body Parameters**:
  - `id` (string): The user ID (e.g., from Clerk).

- **Success Response**:
  - **Code**: 200 OK

- **Error Response**:
  - **Code**: 400 Bad Request (if ID is invalid).
