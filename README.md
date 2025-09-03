# HireFusion AI

HireFusion AI is an **AI-powered recruitment platform** built on AWS that automates the hiring workflow by analyzing resumes and grading interview videos. The project integrates multiple AWS services to deliver a scalable, secure, and intelligent recruitment solution.

---

## 🚀 Key Features

### 1. Resume Analyzer

* Upload resumes in **PDF, DOCX, or TXT** formats.
* Extracts text using **Amazon Textract**.
* Identifies skills and keywords with **Amazon Comprehend**.
* Generates a score based on detected skills.
* Stores results (skills, score, filename) in **Amazon DynamoDB**.

### 2. Interview Grader

* Upload interviews in **MP4, MOV, or AVI** formats.
* Detects facial expressions and gestures using **Amazon Rekognition**.
* Converts speech to text with **Amazon Transcribe**.
* Analyzes sentiment of responses with **Amazon Comprehend**.
* Produces an interview score combining emotion + sentiment analysis.
* Stores results in **Amazon DynamoDB**.

---

## 📂 Project Structure

```
hirefusion-ai/
│
├── backend/
│   ├── resume_analyzer/
│   │   ├── Lambda_function_for_resume_analysis.py
│   │   └── test_resume_lambda.py
│   ├── interview_grader/
│   │   ├── video_resume_analyzer_lambda_1.py
│   │   ├── test_video_lambda_1.py
│   │   ├── video_resume_analyzer_lambda_2.py
│   │   └── test_video_lambda_2.py
│   └── app.py
│
├── frontend/
│   ├── index.html             # Landing page
│   ├── ind.html               # Login / Signup
│   ├── dashboard.html         # User dashboard
│   ├── resume-analyzer.html   # Resume analysis UI
│   └── interview-grader.html  # Interview grading UI
│
├── docs/
│   ├── flow_chart.jpg
│   ├── HireFusionAI_documentation.pdf
│   └── README.md
│
└── README.md                  # Project README
```

---

## 🏗️ AWS Architecture

* **Amazon S3** – Stores uploaded resumes & interview videos.
* **AWS Lambda** – Serverless functions process resumes & videos.
* **Amazon Textract** – Extracts text from resumes.
* **Amazon Comprehend** – Detects skills & performs sentiment analysis.
* **Amazon Rekognition** – Analyzes facial expressions & gestures.
* **Amazon Transcribe** – Converts interview speech to text.
* **Amazon DynamoDB** – Stores analysis results.
* **Amazon API Gateway** – Provides secure REST APIs for frontend-backend communication.
* **Amazon CloudWatch** – Monitors function performance & logs.

![Flow Chart](docs/flow_chart.jpg)

---

## 🔄 Workflow

### Resume Analysis

1. User uploads resume → S3 bucket.
2. S3 event triggers Resume Analyzer Lambda.
3. Textract extracts text → Comprehend detects skills.
4. Score is generated and saved in DynamoDB.
5. Results returned to the frontend.

### Interview Grading

1. User uploads video → S3 bucket.
2. S3 event triggers Interview Grader Lambda.
3. Rekognition analyzes expressions → Transcribe converts audio.
4. Comprehend performs sentiment analysis.
5. Score generated and stored in DynamoDB.
6. Results displayed on frontend.

---

## ⚙️ Setup Instructions

### Prerequisites

* AWS Account with permissions for Lambda, S3, Rekognition, Textract, Comprehend, Transcribe, DynamoDB, and API Gateway.
* Node.js & Python 3.x installed.
* AWS CLI configured locally.

### Steps

1. Clone the repo:

   ```bash
   git clone https://github.com/yourusername/hirefusion-ai.git
   cd hirefusion-ai
   ```
2. Deploy backend Lambda functions:

   * Upload code in `backend/resume_analyzer` and `backend/interview_grader`.
   * Attach IAM roles with required permissions.
3. Create S3 buckets for resumes and videos.
4. Configure API Gateway endpoints for resume & video analysis.
5. Deploy frontend files (`frontend/`) to an S3 static website or hosting service.
6. Test the full pipeline by uploading resumes and interview videos.

---

## 📊 Tech Stack

* **Frontend**: HTML, CSS, JavaScript
* **Backend**: AWS Lambda (Python)
* **Database**: Amazon DynamoDB
* **Cloud Services**: S3, Textract, Comprehend, Rekognition, Transcribe, API Gateway, CloudWatch

---

## 📈 Future Improvements

* Add support for **ATS scoring** with customizable skill weights.
* Enable **real-time video streaming analysis**.
* Integrate **email notifications** for recruiters.
* Provide a **analytics dashboard** for recruiters using Amazon QuickSight.

---

## 👨‍💻 Author

**Srivallisa Sai Veerabhadra Ayyan Bikkavolu**
[LinkedIn](https://www.linkedin.com/in/ayyan-bikkavolu-33a32b291/) | [GitHub](https://github.com/23P31A0506)

---
