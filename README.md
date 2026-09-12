# mediflow-AI
AI-Powered Hospital Triage, OPD Queue &amp; Longitudinal Patient Journey Platform
🏥 MediFlow AI

AI-Assisted Smart Hospital Workflow & Longitudinal Patient Record System

«From fragmented hospital intake to a structured patient journey.»

MediFlow AI is an AI-assisted healthcare workflow platform designed to connect multiple stages of the hospital journey into a single digital workflow — from patient registration and medical-document digitization to AI-assisted history collection, triage support, OPD routing, queue management, doctor consultation, digital prescriptions, pharmacy processing, and longitudinal patient records.

The platform combines React, FastAPI, Supabase, docTR OCR, and Gemini AI to reduce repetitive data entry, improve information flow between hospital departments, and provide doctors with structured patient information before consultation.

---

🚨 Problem Statement

Hospital workflows are often fragmented across registration counters, paper documents, consultation rooms, queues, and pharmacies.

Patients may have to:

- Register repeatedly during different visits
- Carry physical prescriptions and medical reports
- Repeat the same medical history to different staff members
- Wait without knowing their queue position
- Manually carry prescriptions to the pharmacy
- Navigate different departments without clear guidance

At the same time, doctors may spend valuable consultation time collecting basic patient history and reviewing unstructured documents.

The core problem

«Healthcare information exists, but it is fragmented across different stages of the hospital workflow.»

MediFlow AI aims to connect these stages into one structured patient journey.

---

💡 Our Solution

MediFlow AI provides an integrated workflow:

Patient Registration
        ↓
Secure QR Session
        ↓
Medical Document Upload
        ↓
docTR OCR
        ↓
Gemini AI Structuring
        ↓
AI-Assisted Medical History
        ↓
Safety Triage Support
        ↓
OPD Routing
        ↓
Queue / Token Management
        ↓
Doctor Consultation
        ↓
Digital Prescription
        ↓
Pharmacy Order
        ↓
Longitudinal Patient Record

MediFlow AI is not simply a medical chatbot.

The conversational AI is one component of a larger hospital workflow platform.

---

✨ Key Features

👤 Patient Registration

Supports:

- New patient registration
- Returning patient identification
- Patient profile management
- Creation of a separate visit for each hospital encounter

Patient vs Visit

MediFlow AI maintains a distinction between a patient's permanent identity and individual hospital visits.

Patient
 ├── Visit 1
 ├── Visit 2
 ├── Visit 3
 └── Visit 4

This allows the system to maintain a longitudinal patient history.

---

📱 Secure QR-Based Patient Session

After registration at the hospital kiosk, the patient can continue the process on their own phone.

Hospital Kiosk
      ↓
Short-Lived QR Session
      ↓
Patient Smartphone
      ↓
Patient Web Application

The QR session uses a temporary token associated with the current patient visit.

The system is designed so that the QR does not directly expose medical information.

---

📄 Medical Document Digitization

Patients can upload documents such as:

- Prescriptions
- Laboratory reports
- Discharge summaries
- Previous medical documents

Processing pipeline

Document
    ↓
Supabase Storage
    ↓
docTR OCR
    ↓
Extracted Text
    ↓
Gemini AI
    ↓
Structured Medical Information
    ↓
Validation
    ↓
Patient Verification
    ↓
Database

Why docTR + Gemini?

The two technologies have different responsibilities.

docTR performs Optical Character Recognition (OCR) and extracts text from the document.

Gemini interprets the extracted text and converts it into structured information.

Example:

OCR Text:

Paracetamol 500 mg twice daily

can be structured as:

{
  "medicine": "Paracetamol",
  "dosage": "500 mg",
  "frequency": "twice daily"
}

This separation makes the architecture modular and easier to maintain.

---

🗣️ AI-Assisted Medical History

Instead of forcing patients to fill long medical forms, MediFlow AI can collect information conversationally.

Example

Patient:

«I have stomach pain since yesterday.»

AI:

«When did the pain start?»

Patient:

«Yesterday.»

AI:

«Where exactly is the pain?»

Patient:

«Upper abdomen.»

AI:

«Do you have vomiting?»

Patient:

«Yes.»

The system converts the conversation into structured information:

Chief Complaint:
Stomach pain

Duration:
1 day

Location:
Upper abdomen

Associated Symptoms:
Vomiting

The purpose of the AI conversation is to structure patient-provided information for clinical review, not to replace a medical professional.

---

🚨 Safety Triage Support

MediFlow AI does not rely solely on generative AI for emergency decisions.

The architecture combines:

Patient Symptoms
       │
       ├───────────────┐
       ↓               ↓
Deterministic      Gemini AI
Safety Rules       Contextual Analysis
       │               │
       └───────┬───────┘
               ↓
        Triage Support

Hospital-configurable rules can identify critical symptoms and trigger escalation.

Examples may include:

- Severe breathing difficulty
- Chest pain
- Stroke-like symptoms
- Severe bleeding

Safety principle

«AI assists. Clinical professionals remain the final authority.»

MediFlow AI is designed as a workflow and decision-support system, not an autonomous diagnostic system.

---

🏥 OPD Routing

After history collection and triage support, MediFlow AI helps route patients through the hospital.

Patient Information
       ↓
OPD Recommendation
       ↓
Department
       ↓
Room
       ↓
Floor
       ↓
Navigation

For example:

Department: General Medicine
Room: 204
Floor: 2
Token: M-042

OPD routing is intended as hospital navigation and workflow support, not medical diagnosis.

Hospital staff can override or modify recommendations when required.

---

🎫 Queue Management

MediFlow AI provides digital queue information.

Example:

Department: General Medicine

Token: M-042
Position: 7
Estimated Wait: 28 minutes
Room: 204
Floor: 2

Queue information can be made available to:

- Patients
- Reception staff
- Nurses
- Doctors
- Hospital administrators

This helps reduce unnecessary physical waiting and repeated inquiries at counters.

---

👨‍⚕️ Doctor Dashboard

The doctor can access relevant information before beginning the consultation.

Patient
   ↓
Current Complaint
   ↓
Structured History
   ↓
Previous Documents
   ↓
Relevant Medical History
   ↓
Triage Flags
   ↓
AI Summary
   ↓
Doctor Review

The doctor remains responsible for:

- Clinical examination
- Diagnosis
- Treatment decisions
- Prescription
- Follow-up decisions

Human-in-the-loop principle

«MediFlow prepares information; the doctor makes the clinical decision.»

---

💊 Digital Prescription & Pharmacy Automation

MediFlow AI connects the doctor's prescription directly with the pharmacy workflow.

Traditional workflow

Doctor
  ↓
Paper Prescription
  ↓
Patient
  ↓
Pharmacy
  ↓
Manual Entry
  ↓
Medicine Preparation

MediFlow workflow

Doctor
  ↓
Digital Prescription
  ↓
Pharmacy Order
  ↓
Pharmacy Dashboard
  ↓
Preparing
  ↓
Ready
  ↓
Collected

Example:

Pharmacy Order: P1042

Paracetamol 500 mg
Pantoprazole 40 mg
Amoxicillin 500 mg

Status:
READY

This reduces manual prescription entry and allows pharmacy preparation to begin earlier.

---

🗂️ Longitudinal Patient Record

The system maintains a relationship between a permanent patient profile and individual hospital visits.

PATIENT
   │
   ├── VISITS
   │      │
   │      ├── History
   │      ├── Documents
   │      ├── Triage
   │      ├── Queue
   │      ├── Consultation
   │      └── Prescription
   │                    │
   │                    ↓
   │              Pharmacy Order
   │
   ├── Conditions
   ├── Allergies
   ├── Medications
   ├── Surgeries
   └── Family History

This creates a continuous medical history instead of treating every hospital visit as an isolated event.

---

🏗️ System Architecture

                         USERS
              Patient / Doctor / Staff
                         │
                         ▼
                ┌─────────────────┐
                │ React Frontend  │
                │ Vite + Tailwind │
                └────────┬────────┘
                         │
                    HTTPS / REST
                         │
                         ▼
                ┌─────────────────┐
                │ FastAPI Backend │
                └────────┬────────┘
                         │
                ┌────────▼────────┐
                │  Service Layer  │
                │                 │
                │ History         │
                │ OCR             │
                │ Triage          │
                │ Queue           │
                │ Pharmacy        │
                │ Navigation      │
                └────────┬────────┘
                         │
                ┌────────▼────────┐
                │Repository Layer │
                └───────┬─┬───────┘
                        │ │
              ┌─────────┘ └─────────┐
              ▼                     ▼
       ┌──────────────┐      ┌──────────────┐
       │   Supabase   │      │   AI Layer   │
       │              │      │              │
       │ PostgreSQL   │      │ docTR        │
       │ Auth         │      │ Gemini       │
       │ Storage      │      │              │
       │ RLS          │      │              │
       └──────────────┘      └──────────────┘

---

🔧 Technology Stack

Layer| Technology| Purpose
Frontend| React 19| User interfaces
Build Tool| Vite| Frontend development/build
Styling| Tailwind CSS| Responsive UI
Icons| Lucide React| UI icons
Routing| React Router| Application navigation
QR| react-qr-code| QR session generation
Backend| FastAPI| REST APIs
Server| Uvicorn| FastAPI server
Validation| Pydantic| Data and AI output validation
Database| Supabase PostgreSQL| Persistent data
Authentication| Supabase Auth + JWT| Authentication
Security| Row Level Security| Database-level access control
Storage| Supabase Storage| Medical documents
OCR| docTR| Document text extraction
AI| Gemini| Language understanding and structuring
Image Processing| Pillow| Image preparation
PDF| pypdf / ReportLab| PDF processing
Async| asyncio| Asynchronous operations
Testing| pytest / pytest-asyncio| Backend testing

---

🧠 AI Architecture

MediFlow AI uses specialized AI functions rather than one large AI component.

                         AI Layer
                            │
             ┌──────────────┼──────────────┐
             ↓              ↓              ↓
        History         Summarization    Routing
        Structuring
             │              │              │
             └──────────────┼──────────────┘
                            ↓
                     Structured Output

For documents:

Medical Document
       ↓
     docTR
       ↓
   OCR Text
       ↓
    Gemini
       ↓
Structured Information

---

🔐 Security & Privacy

Healthcare information requires strong access control.

MediFlow AI incorporates security at multiple layers.

Patient / Staff
       ↓
     HTTPS
       ↓
    FastAPI
       ↓
 Authentication
       ↓
 Authorization
       ↓
 Supabase RLS
       ↓
 PostgreSQL

Security mechanisms

- HTTPS communication
- Authentication
- JWT-based authorization
- Role-based access
- Supabase Row Level Security
- Private medical document storage
- Short-lived QR sessions
- Backend request validation
- Patient-specific data access

User roles

PATIENT
RECEPTIONIST
NURSE
DOCTOR
PHARMACIST
ADMIN

Access should be restricted according to the user's role and permissions.

---

🧩 Backend Architecture

The backend follows a layered architecture:

API Layer
    ↓
Service Layer
    ↓
Repository Layer
    ↓
Supabase

API Layer

Handles HTTP requests and responses.

Service Layer

Contains business logic such as:

- History processing
- OCR
- AI processing
- Triage
- Navigation
- Queue management
- Pharmacy workflow

Repository Layer

Handles database operations and separates database logic from business logic.

This architecture improves:

- Maintainability
- Testability
- Separation of concerns
- Scalability
- Component replacement

---

📁 Project Structure

A typical project structure is:

MediFlow-AI/
│
├── frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── vite.config.js
│
├── backend/
│   ├── app/
│   │   ├── api/
│   │   ├── services/
│   │   ├── repositories/
│   │   ├── models/
│   │   └── main.py
│   │
│   ├── requirements.txt
│   └── tests/
│
├── README.md
└── .gitignore

«Update this structure to match the actual repository before publishing.»

---

⚙️ Installation & Setup

Prerequisites

Make sure the following are installed:

- Node.js
- npm
- Python 3.10+
- Git
- Supabase account
- Gemini API key

---

1. Clone the repository

git clone https://github.com/YOUR_USERNAME/MediFlow-AI.git
cd MediFlow-AI

Replace "YOUR_USERNAME" with your GitHub username.

---

2. Frontend Setup

cd frontend
npm install

Create the frontend environment file:

.env

Example:

VITE_API_BASE_URL=http://localhost:8000

Run the frontend:

npm run dev

---

3. Backend Setup

Open a new terminal:

cd backend

Create a virtual environment:

Windows

python -m venv venv
venv\Scripts\activate

Linux / macOS

python3 -m venv venv
source venv/bin/activate

Install dependencies:

pip install -r requirements.txt

---

4. Environment Variables

Create:

backend/.env

Example:

SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_key
GEMINI_API_KEY=your_gemini_api_key

Do not commit your ".env" file to GitHub.

Add it to ".gitignore":

.env
venv/
__pycache__/
node_modules/

---

5. Run the Backend

From the backend directory:

uvicorn app.main:app --reload

The backend will normally be available at:

http://localhost:8000

FastAPI API documentation can be accessed through:

http://localhost:8000/docs

---

🗄️ Database

MediFlow AI uses Supabase PostgreSQL for persistent storage.

The database manages entities such as:

Patients
Visits
History Sessions
History Answers
Structured Histories
Documents
Triage
Queues
Consultations
Prescriptions
Prescription Items
Pharmacy Orders
QR Sessions

The exact schema should be kept synchronized with the backend models and migrations used by the project.

---

🔄 Complete Workflow

                    PATIENT
                       │
                       ▼
              ┌────────────────┐
              │    KIOSK       │
              │ Registration   │
              └───────┬────────┘
                      │
                  Secure QR
                      │
                      ▼
              ┌────────────────┐
              │ Patient Phone  │
              └───────┬────────┘
                      │
              ┌───────┴────────┐
              │                │
              ▼                ▼
        Document Upload   AI History
              │                │
              ▼                ▼
            docTR           Gemini
              │                │
              └───────┬────────┘
                      ▼
                 Triage Support
                      │
                      ▼
                  OPD Routing
                      │
                      ▼
                    Queue
                      │
                      ▼
                    Doctor
                      │
                      ▼
             Digital Prescription
                      │
                      ▼
                  Pharmacy
                      │
                      ▼
              Patient Record

---

🎯 Key Differentiators

1. End-to-End Workflow

Instead of solving only registration, chatbot interaction or OCR, MediFlow connects multiple hospital processes.

2. OCR + AI Separation

docTR handles document text extraction while Gemini handles language understanding and structuring.

3. Human-in-the-Loop Healthcare AI

The system assists healthcare professionals rather than attempting to replace them.

4. Longitudinal Records

Patient and Visit are separated so multiple encounters can form one continuous patient history.

5. Pharmacy Automation

Digital prescriptions can directly initiate pharmacy workflow.

6. Hospital Navigation

Patients receive department, room, floor and queue information.

7. Configurable Safety Rules

Critical triage logic can be configured rather than depending entirely on generative AI.

---

📊 Expected Impact

For Patients

- Reduced repetitive registration
- Easier document sharing
- Better hospital navigation
- Queue visibility
- Faster pharmacy processing
- Better continuity of medical information

For Doctors

- Structured history before consultation
- Easier access to previous documents
- AI-assisted summaries
- Reduced repetitive information collection

For Hospitals

- Reduced manual data entry
- Connected departmental workflow
- Better queue visibility
- Digital prescription processing
- Centralized longitudinal records

---

🚀 Future Scope

Potential future improvements include:

- Multilingual voice-based patient interaction
- More regional Indian languages
- Hospital Information System integration
- Laboratory integration
- Appointment scheduling
- Wearable/device integration
- Advanced hospital analytics
- Real-time notifications
- Interoperability with external healthcare systems
- Improved document classification
- Clinical validation and real-world deployment studies

---

⚠️ Medical Safety & Disclaimer

MediFlow AI is designed as an AI-assisted healthcare workflow and information-management platform.

It is not intended to:

- Replace doctors
- Provide autonomous medical diagnosis
- Make independent treatment decisions
- Replace emergency medical services

AI-generated information should be reviewed and verified by qualified healthcare professionals before being used for clinical decision-making.

For real-world deployment, additional requirements such as clinical validation, healthcare regulations, privacy compliance, security audits, monitoring, and integration with hospital systems would need to be addressed.

---

🏆 Hackathon Value Proposition

MediFlow AI addresses a practical problem by connecting:

AI
+
OCR
+
Patient Interaction
+
Hospital Workflow
+
Queue Management
+
Doctor Workflow
+
Pharmacy Automation
+
Longitudinal Records

The core idea is simple:

«Don't build another healthcare chatbot. Connect intelligence to the hospital workflow.»

---

👥 Team

Name| Role
Team Member 1| Frontend / UI
Team Member 2| Backend / API
Team Member 3| AI / OCR
Team Member 4| Database / Integration

«Replace the placeholders with your actual team members and responsibilities.»

---

📌 Project Status

MediFlow AI — Hackathon Prototype

The current implementation focuses on demonstrating the core patient workflow and technical feasibility.

Features marked as future scope are not represented as production-ready capabilities.

---

📄 License

This project is developed as a hackathon/academic project.

Add your preferred open-source license here if you intend to make the repository open source.
