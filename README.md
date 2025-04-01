# AI Resume Screener

## Overview
AI Resume Screener is an AI-powered tool that automates resume screening by leveraging Natural Language Processing (NLP) to extract key skills, match them with job descriptions, and rank candidates based on relevance. The system allows recruiters to upload multiple resumes, evaluate candidates efficiently, and provide AI-driven feedback to job applicants.

## Features

### User Management
- User Authentication & Authorization (JWT/OAuth)
- Role-based access control (Admin, HR/Recruiter, Candidate)
- Profile management

### Resume Processing & AI Analysis
- Multi-file resume upload (PDF, DOCX)
- NLP-powered resume parsing (Extract skills, experience, education, and contact details)
- AI-based skill matching against job descriptions
- Job-specific scoring (Relevance ranking of candidates per job posting)
- AI-generated feedback to candidates for resume improvement

### Job & Application Tracking System
- Job posting and management (HR can post jobs with skill requirements)
- Candidate application tracking (Applied, Shortlisted, Interview, Hired)
- Interview scheduling and notifications

### Dashboard & Reporting
- Recruiter dashboard (View jobs, applicants, AI-ranked candidates)
- Candidate dashboard (Track job applications, receive AI feedback)
- Analytics & reports (Hiring trends, candidate scores, skill gaps)

### Integrations & Miscellaneous
- Email notifications (Application updates, interview invites)
- Export & download reports (CSV, PDF)
- API integrations (Connect with HR systems like Workday, Greenhouse)

---

## Tech Stack

### Backend
- **Python (Flask/FastAPI)** – API development
- **OpenAI API** – AI-driven resume parsing and feedback
- **MongoDB/PostgreSQL** – Database storage

### Frontend
- **React** – User interface
- **Tailwind CSS** – Styling framework

### Additional Tools
- **Celery & Redis** – Asynchronous task processing (if needed)
- **Docker** – Containerization
- **Nginx** – Reverse proxy
- **JWT/OAuth** – Authentication
- **Cloud Storage (AWS S3/GCP Bucket)** – Storing uploaded resumes

---

## Project Structure

```
AI-Resume-Screener/
│── backend/                  # Flask/FastAPI backend
│   ├── app/
│   │   ├── models/           # Database models (SQLAlchemy for PostgreSQL or ODM for MongoDB)
│   │   ├── routes/           # API routes
│   │   ├── services/         # Business logic (NLP, AI ranking, Resume parsing)
│   │   ├── utils/            # Helper functions
│   │   ├── config.py         # Configuration settings
│   │   ├── main.py           # Entry point (FastAPI/Flask)
│   │   ├── requirements.txt  # Backend dependencies
│   ├── Dockerfile            # Docker configuration
│
│── frontend/                 # React frontend
│   ├── src/
│   │   ├── components/       # Reusable UI components
│   │   ├── pages/            # Different pages (Dashboard, Job Listings, Resume Upload)
│   │   ├── services/         # API calls
│   │   ├── App.js            # Main React component
│   │   ├── index.js          # React entry point
│   │   ├── tailwind.config.js# Tailwind configuration
│   ├── package.json          # Frontend dependencies
│   ├── Dockerfile            # Frontend Docker configuration
│
│── database/                 # Database scripts/migrations
│── docs/                     # Documentation files
│── .env                      # Environment variables
│── docker-compose.yml        # Container orchestration
│── README.md                 # Project documentation
```

---

## Installation & Setup

### Prerequisites
- Python 3.9+
- Node.js 16+
- PostgreSQL or MongoDB
- Docker (Optional, for containerized deployment)

### Backend Setup (Flask/FastAPI)

```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload  # For FastAPI
# OR
flask run  # For Flask
```

### Frontend Setup (React)

```bash
cd frontend
npm install
npm start
```

---

## API Endpoints

### Authentication
| Method | Endpoint            | Description               |
|--------|--------------------|--------------------------|
| POST   | /auth/register     | Register a new user      |
| POST   | /auth/login        | Login user               |

### Resume Upload & Processing
| Method | Endpoint              | Description                      |
|--------|----------------------|---------------------------------|
| POST   | /resume/upload       | Upload a resume                 |
| GET    | /resume/{id}         | Get processed resume data       |
| GET    | /resume/score/{id}   | Get AI relevance score          |

### Jobs & Applications
| Method | Endpoint              | Description                      |
|--------|----------------------|---------------------------------|
| POST   | /jobs/create         | Create a new job posting       |
| GET    | /jobs/list           | List all job postings          |
| POST   | /applications/apply  | Apply to a job                 |
| GET    | /applications/status | Check application status       |

---

## Deployment

### Docker (Production)

```bash
docker-compose up --build
```

### Nginx + Gunicorn (For Flask/FastAPI)

1. Install Gunicorn:
```bash
pip install gunicorn
```
2. Run the server:
```bash
gunicorn -w 4 -k uvicorn.workers.UvicornWorker app.main:app
```

---

## Future Enhancements
- Machine Learning model for improved candidate ranking
- AI-based interview question generator
- Resume formatting improvement suggestions

---

## License
This project is licensed under the MIT License.

---

## Contributors
- **Benjamin Mweri Baya** – Founder & Lead Developer
- Open to contributions! Submit a pull request.

For inquiries, contact: **b3njaminbaya@gmail.com**

