# **📌 API Documentation – Tribal Language Learning App**  
**Version:** 1.0  
**Base URL:** `/api/v1`  
**Authentication:** JWT (Required for protected endpoints)  

---

## **1️⃣ Authentication & User Management**  

### **🔹 Register User**  
**Endpoint:** `POST /auth/register`  
**Description:** Create a new learner/instructor account.  
**Request Body:**  
```json
{
  "name": "Jean Dupont",
  "email": "jean@example.com",
  "password": "SecurePass123",
  "phone": "+237612345678",
  "tribe_id": "tribe_123",
  "dialect_id": "dialect_456",
  "role": "learner"
}
```
**Response:**  
```json
{
  "message": "User registered successfully",
  "user_id": "650f4e9a4567abcd12345678"
}
```

---

### **🔹 User Login**  
**Endpoint:** `POST /auth/login`  
**Description:** Authenticate and get JWT token.  
**Request Body:**  
```json
{
  "email": "jean@example.com",
  "password": "SecurePass123"
}
```
**Response:**  
```json
{
  "token": "eyJhbGciOiJIUz...",
  "expires_in": 86400
}
```

---

### **🔹 Get User Profile**  
**Endpoint:** `GET /users/profile`  
**Headers:** `Authorization: Bearer <token>`  
**Response:**  
```json
{
  "id": "650f4e9a4567abcd12345678",
  "name": "Jean Dupont",
  "role": "learner",
  "tribe": "Bankon",
  "dialect": "Coastal Bankon"
}
```

---

## **2️⃣ Module & Lesson Management**  

### **🔹 Create Module (Instructor Only)**  
**Endpoint:** `POST /modules`  
**Headers:** `Authorization: Bearer <token>`  
**Request Body:**  
```json
{
  "title": "Basic Greetings",
  "description": "Learn common greetings",
  "dialect_id": "dialect_456",
  "order": 1
}
```
**Response:**  
```json
{
  "message": "Module created",
  "module_id": "mod_123"
}
```

---

### **🔹 Add Lesson to Module (Instructor)**  
**Endpoint:** `POST /modules/{module_id}/lessons`  
**Headers:** `Authorization: Bearer <token>`  
**Request Body:**  
```json
{
  "title": "Morning Greetings",
  "content": {
    "text": "M̀bɔ́lɔ́ means 'Good morning'",
    "images": ["sunrise.jpg"],
    "audio": "mbolo.mp3"
  },
  "order": 1
}
```
**Response:**  
```json
{
  "message": "Lesson added",
  "lesson_id": "les_456"
}
```

---

### **🔹 Get Module Lessons**  
**Endpoint:** `GET /modules/{module_id}/lessons`  
**Response:**  
```json
[
  {
    "id": "les_456",
    "title": "Morning Greetings",
    "content": {
      "text": "M̀bɔ́lɔ́ means 'Good morning'",
      "images": ["sunrise.jpg"],
      "audio": "mbolo.mp3"
    }
  }
]
```

---

## **3️⃣ Quiz System**  

### **🔹 Add Module Quiz (Instructor)**  
**Endpoint:** `POST /modules/{module_id}/quiz`  
**Headers:** `Authorization: Bearer <token>`  
**Request Body (Matching Quiz):**  
```json
{
  "type": "matching",
  "pairs": [
    {"native": "Mbɔ́lɔ́", "translation": "Good morning"},
    {"native": "Mə̀sə́l", "translation": "Thank you"}
  ]
}
```
**Request Body (Multiple Choice):**  
```json
{
  "type": "multiple_choice",
  "question": "What does 'Mbɔ́lɔ́' mean?",
  "options": ["Good morning", "Good night", "Hello"],
  "correct_index": 0
}
```
**Response:**  
```json
{
  "message": "Quiz added",
  "quiz_id": "quiz_789"
}
```

---

### **🔹 Take Module Quiz**  
**Endpoint:** `POST /quizzes/{quiz_id}/submit`  
**Headers:** `Authorization: Bearer <token>`  
**Request Body (Matching Answers):**  
```json
{
  "answers": [
    {"Mbɔ́lɔ́": "Good morning"},
    {"Mə̀sə́l": "Thank you"}
  ]
}
```
**Response:**  
```json
{
  "score": 100,
  "correct": 2,
  "total": 2
}
```

---

## **4️⃣ Village Events**  

### **🔹 Create Event (Instructor)**  
**Endpoint:** `POST /events`  
**Headers:** `Authorization: Bearer <token>`  
**Request Body:**  
```json
{
  "title": "Harvest Festival",
  "date": "2024-08-15",
  "description": "Traditional storytelling night"
}
```
**Response:**  
```json
{
  "message": "Event created",
  "event_id": "evt_123"
}
```

---

### **🔹 Get Upcoming Events**  
**Endpoint:** `GET /events`  
**Response:**  
```json
[
  {
    "id": "evt_123",
    "title": "Harvest Festival",
    "date": "2024-08-15",
    "description": "Traditional storytelling night"
  }
]
```

---

## **🔐 HTTP Status Codes**  
| Code | Description                  |
|------|------------------------------|
| 200  | Success                      |
| 201  | Resource created             |
| 400  | Invalid request              |
| 401  | Unauthorized                 |
| 404  | Resource not found           |
| 500  | Internal server error        |

