# **Tribal Language Learning App**  

---

## **1. Introduction**  
This document outlines the core functionality of a minimal tribal language learning app designed for basic language preservation and instruction. The system focuses on essential features for learners, instructors, and administrators.  

---

## **2. System Actors and Their Roles**  

### **2.1 Learner**  
- Completes lessons and quizzes.  
- Tracks progress.  
- Sends questions to instructors via chat.  
- Receives notifications and event reminders.  

### **2.2 Instructor**  
- Creates/approves lessons and quizzes.  
- Responds to learner questions in chat.  
- Publishes announcements and event details.  

### **2.3 Admin**  
- Manages user accounts (learners/instructors).  
- Uploads learning modules and quizzes.  
- Configures tribe-specific settings.  

---

## **3. Core Use Cases**  

### **3.1 User Registration**  
1. User signs up with email/phone.  
2. Selects tribe and dialect.  
3. Profile is created with basic details.  

### **3.2 Completing a Lesson**  
1. Learner selects a lesson (e.g., "Basic Greetings").  
2. Views text, images, and listens to audio.  
3. Marks lesson as completed.  

### **3.3 Taking a Quiz**  
1. System serves quiz after lesson completion.  
2. Quiz types:  
   - **Matching:** Pair words with translations.  
   - **Multiple Choice:** Select correct answers.  
   - **Voice Check:** Record pronunciation.  
3. Results saved to track progress.  

### **3.4 Tracking Progress**  
1. Learner views dashboard:  
   - Completed lessons.  
   - Quiz scores.  
   - Time spent learning.  

### **3.5 Instructor Chat**  
1. Learner sends a question via chat.  
2. Instructor responds with text/voice message.  
3. Chat history saved for reference.  

### **3.6 Managing Village Events**  
1. Instructor posts event (e.g., "Cultural Storytelling Night").  
2. Event appears in app calendar.  
3. Learners receive notifications.  

### **3.7 Admin Module Upload**  
1. Admin uploads a lesson (text + images + audio).  
2. Links quiz to the lesson.  
3. Publishes module to learners.  

---

## **4. Simplified Security & Features**  
- **Authentication:** Email/phone signup + password.  
- **Data Privacy:** Basic encryption for user data.  
- **Backups:** Weekly cloud backups of lessons and progress.  
