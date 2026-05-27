# ai-cv-generator-system
AI Resume Intelligence System is a full-stack Python Streamlit app that analyzes resumes against job descriptions. It extracts resume data, calculates ATS and job-match scores using NLP and TF-IDF, detects missing skills, generates improvement suggestions, highlights keywords, and stores reports in SQLite.
AI Resume Intelligence System
A semester-level full-stack Python project for analyzing resumes against job descriptions. It rebuilds the best ideas from resume analyzers, resume matchers, and pyresparser-style extraction into a clean offline Streamlit application.
Features
Upload PDF or DOCX resumes.
Extract clean text locally.
Parse structured data: name, email, phone, LinkedIn, GitHub, skills, education, experience, and sections.
Compute resume-to-job match percentage with TF-IDF cosine similarity plus skill coverage.
Detect matched and missing skills.
Score resume quality out of 100 with ATS and section-wise scoring.
Generate smart offline improvement suggestions.
Highlight job-description keywords inside the resume.
Download a PDF analysis report.
Store analysis history in SQLite.
Advanced add-ons in `enhancements/`: job matching, ATS interview probability, cover letters, interview prep, resume rewriting, and progress trends.
Run locally on `http://localhost:8501`.
Project Structure
```text
resume_ai_system/
├── app.py
├── backend/
│   ├── parser/
│   │   ├── resume_parser.py
│   │   └── skill_extractor.py
│   ├── matcher/
│   │   ├── matcher.py
│   │   └── similarity.py
│   ├── scoring/
│   │   └── scorer.py
│   ├── suggestions/
│   │   └── suggestion_engine.py
│   ├── models/
│   │   └── resume_model.py
│   ├── database/
│   │   └── db.py
│   └── utils/
│       ├── file_handler.py
│       └── text_cleaner.py
├── frontend/
│   ├── dashboard.py
│   ├── components.py
│   └── styles.css
├── enhancements/
│   ├── matcher/
│   ├── ats/
│   ├── parser/
│   ├── cover_letter/
│   ├── interview/
│   ├── rewriter/
│   ├── dashboard/
│   └── database/
├── assets/
├── data/
├── requirements.txt
└── README.md
```
Installation
```bash
cd resume_ai_system
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```
On macOS or Linux:
```bash
source .venv/bin/activate
```
Run Locally
```bash
streamlit run app.py
```
Open:
```text
http://localhost:8501
```
Module Purpose
`app.py`: thin controller that starts the Streamlit dashboard.
`backend/parser/resume_parser.py`: extracts structured resume fields using NLP-inspired rules and section heuristics.
`backend/parser/skill_extractor.py`: detects known technical and professional skills from resumes and job descriptions.
`backend/matcher/similarity.py`: offline TF-IDF cosine similarity engine.
`backend/matcher/matcher.py`: combines semantic similarity and skill coverage into the match percentage.
`backend/scoring/scorer.py`: calculates ATS, overall, and section-wise scores.
`backend/suggestions/suggestion_engine.py`: creates offline recommendations and keyword highlights.
`backend/database/db.py`: stores local analysis history in SQLite.
`backend/utils/file_handler.py`: reads PDF/DOCX files and creates downloadable PDF reports.
`frontend/dashboard.py`: main Streamlit view with metrics, cards, charts, skill gaps, suggestions, and history.
`frontend/components.py`: reusable dashboard UI helpers.
`frontend/styles.css`: custom dashboard styling.
`enhancements/matcher/job_matcher.py`: wrapper around existing matching logic for match score, matched skills, and missing skills.
`enhancements/ats/ats_engine.py`: extended ATS score, interview probability, strengths, red flags, and improvements.
`enhancements/parser/advanced_extractor.py`: extracts college, degree, designations, and company names without replacing the base parser.
`enhancements/cover_letter/cover_letter_generator.py`: generates ATS-ready cover letters in formal, professional, and enthusiastic tones.
`enhancements/interview/interview_prep.py`: creates technical, behavioral, and situational prep questions.
`enhancements/rewriter/resume_rewriter.py`: suggests job-targeted rewrites and general resume improvements.
`enhancements/database/history_db.py`: stores score, match, and skill-gap trend snapshots.
Notes
The app is offline-first. No resume text is sent to external AI services. A future provider layer can be added for OpenAI, Gemini, or other LLM-based suggestions if required.
