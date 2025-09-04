# Recruitly API Specification

Base URL: `/api/v1`

---

## Endpoints

### Resume APIs
- **POST** `/resumes/upload`  
  Upload a resume (PDF/DOCX).  
  **Request:** file upload  
  **Response:**  
  ```json
  { "candidate_id": 123, "status": "processed" }
  ```

- **GET** `/resumes/{id}`  
  Get parsed resume details.  
  **Response:**  
  ```json
  { "id": 123, "name": "John Doe", "skills": ["Python", "ML"], "experience": "5 years" }
  ```

---

### Job APIs
- **POST** `/jobs`  
  Create a new job description.  
  **Request:**  
  ```json
  { "title": "Data Scientist", "description": "Strong in ML, Python" }
  ```  
  **Response:**  
  ```json
  { "job_id": 45, "status": "created" }
  ```

- **GET** `/jobs/{id}`  
  Retrieve job description details.

---

### Candidate Ranking
- **POST** `/ranking`  
  Match candidates to a job.  
  **Request:**  
  ```json
  { "job_id": 45 }
  ```  
  **Response:**  
  ```json
  [
    { "candidate_id": 123, "score": 0.92 },
    { "candidate_id": 456, "score": 0.81 }
  ]
  ```

---

### Generative AI
- **POST** `/genai/summarize`  
  Summarize a resume.  
  **Request:** `{ "candidate_id": 123 }`  
  **Response:** `"John Doe is a Data Scientist with 5 years of experience in Python and ML."`

- **POST** `/genai/questions`  
  Generate interview questions for a job.  
  **Request:** `{ "job_id": 45 }`  
  **Response:** `["What is your experience with ML models?", "Explain overfitting."]`

---

### Agent Orchestration
- **POST** `/agents/screening`  
  Run screening agent for a job.  

- **POST** `/agents/engagement`  
  Draft candidate communication.
