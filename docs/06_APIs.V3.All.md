# **📌 API Documentation – Tribal Language Learning App**  
**Version:** 3.0 (V1 to V3)  
**Base URL:** `/api/v1` (V1), `/api/v2` (V2), `/api/v3` (V3)  
**Authentication:** JWT (Required for protected endpoints)  

---

## **🔷 Version 1 (V1) – Core Features**  

### **1️⃣ Authentication & User Management**  
#### **Register User**  
**Endpoint:** `POST /api/v1/auth/register`  
**Request Body:**  
```json
{
  "name": "Jean Dupont",
  "email": "jean@example.com",
  "password": "SecurePass123",
  "tribe_id": "tribe_123",
  "dialect_id": "dialect_456"
}
```  
**Response:**  
```json
{ "user_id": "usr_123", "message": "User registered" }
```  

#### **User Login**  
**Endpoint:** `POST /api/v1/auth/login`  
**Response:**  
```json
{ "token": "eyJhbGciOiJIUz...", "expires_in": 86400 }
```  

---

### **2️⃣ Module & Lesson Management**  
#### **Create Module** (Instructor Only)  
**Endpoint:** `POST /api/v1/modules`  
**Request Body:**  
```json
{
  "title": "Basic Greetings",
  "dialect_id": "dialect_456",
  "order": 1
}
```  
**Response:**  
```json
{ "module_id": "mod_123" }
```  

#### **Add Lesson to Module**  
**Endpoint:** `POST /api/v1/modules/{module_id}/lessons`  
**Request Body:**  
```json
{
  "title": "Morning Greetings",
  "text": "Mbɔ́lɔ́ means 'Good morning'",
  "images": ["sunrise.jpg"]
}
```  
**Response:**  
```json
{ "lesson_id": "les_456" }
```  

---

### **3️⃣ Quizzes**  
#### **Add Module Quiz** (Instructor)  
**Endpoint:** `POST /api/v1/modules/{module_id}/quiz`  
**Request Body (Matching):**  
```json
{
  "type": "matching",
  "pairs": [{"native": "Mbɔ́lɔ́", "translation": "Good morning"}]
}
```  
**Response:**  
```json
{ "quiz_id": "quiz_789" }
```  

#### **Take Quiz**  
**Endpoint:** `POST /api/v1/quizzes/{quiz_id}/submit`  
**Request Body:**  
```json
{ "answers": [{"Mbɔ́lɔ́": "Good morning"}] }
```  
**Response:**  
```json
{ "score": 100, "correct": 1, "total": 1 }
```  

---

### **4️⃣ Events**  
#### **Create Event**  
**Endpoint:** `POST /api/v1/events`  
**Request Body:**  
```json
{ "title": "Harvest Festival", "date": "2024-08-15" }
```  
**Response:**  
```json
{ "event_id": "evt_123" }
```  

#### **Get Events**  
**Endpoint:** `GET /api/v1/events`  
**Response:**  
```json
[{ "id": "evt_123", "title": "Harvest Festival", "date": "2024-08-15" }]
```  

---

## **🔷 Version 2 (V2) – Enhanced Learning**  

### **1️⃣ Multimedia Lessons**  
#### **Add Audio to Lesson**  
**Endpoint:** `PATCH /api/v2/lessons/{lesson_id}`  
**Request Body:**  
```json
{ "audio": "m̀bɔ́lɔ́.mp3" }
```  
**Response:**  
```json
{ "message": "Audio added to lesson" }
```  

---

### **2️⃣ Advanced Quizzes**  
#### **Voice Recognition Quiz**  
**Endpoint:** `POST /api/v2/quizzes`  
**Request Body:**  
```json
{
  "type": "voice",
  "target_phrase": "Mbɔ́lɔ́",
  "reference_audio": "m̀bɔ́lɔ́.mp3"
}
```  
**Response:**  
```json
{ "quiz_id": "quiz_789" }
```  

---

### **3️⃣ Progress Tracking**  
#### **Get Progress**  
**Endpoint:** `GET /api/v2/users/{user_id}/progress`  
**Response:**  
```json
{
  "completed_modules": 3,
  "average_score": 85,
  "recent_quizzes": [
    { "quiz_id": "quiz_789", "score": 100 }
  ]
}
```  

---

## **🔷 Version 3 (V3) – Community & Advanced Features**  

### **1️⃣ Instructor Chat**  
#### **Send Message**  
**Endpoint:** `POST /api/v3/chat`  
**Request Body:**  
```json
{ "receiver_id": "usr_456", "message": "How do I pronounce Mbɔ́lɔ́?" }
```  
**Response:**  
```json
{ "message_id": "msg_123" }
```  

#### **Get Chat History**  
**Endpoint:** `GET /api/v3/chat/{user_id}`  
**Response:**  
```json
[
  {
    "sender": "usr_123",
    "message": "How do I pronounce Mbɔ́lɔ́?",
    "timestamp": "2024-03-15T10:00:00Z"
  }
]
```  

---

### **2️⃣ Offline Access**  
#### **Download Module**  
**Endpoint:** `GET /api/v3/modules/{module_id}/download`  
**Response:**  
```json
{
  "module": { "title": "Basic Greetings" },
  "lessons": [ { "title": "Morning Greetings" } ],
  "quiz": { "type": "matching" }
}
```  

---

### **3️⃣ Admin Tools**  
#### **Manage Tribes**  
**Endpoint:** `POST /api/v3/admin/tribes`  
**Request Body:**  
```json
{ "name": "New Tribe", "region": "Southwest" }
```  
**Response:**  
```json
{ "tribe_id": "tribe_789" }
```  

#### **Export Data**  
**Endpoint:** `GET /api/v3/admin/export?type=progress`  
**Response:** CSV/JSON file with tribe-wide progress data.  

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

---

## **🌐 Versioning Strategy**  
- **Path-Based:** `/api/v1`, `/api/v2`, `/api/v3`  
- **Backward Compatibility:** V2/V3 support all V1 endpoints.  
- **Deprecation Policy:** Old versions phased out after 6 months.  
