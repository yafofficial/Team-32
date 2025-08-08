# AI-Powered Vulnerability Tracker

**Date: Aug-8-2025**

## Overview of the Project

AI-Powered Vulnerability Tracker is a smart cybersecurity tool designed to automatically scan systems for potential vulnerabilities and classify their risk levels using Artificial Intelligence (AI). With an interactive and modern dashboard, this tool empowers cybersecurity professionals to track threats, prioritize fixes, and generate detailed reports. It's built to assist ethical hackers, penetration testers, and red teamers in identifying and resolving system weaknesses.

## Main Features

### Vulnerability Scanning
- Detects open ports, weak/missing security headers, and default credentials
- Custom scripts perform lightweight reconnaissance

### AI-Based Risk Scoring
- Uses a machine learning model to classify each finding into Low, Medium, or High risk
- Suggests mitigation steps based on detected patterns

### Dashboard (React.js)
- Presents live scan results and allows filtering by type/severity
- Displays vulnerability trends over time
- Designed with usability and clarity in mind

### Exportable Reports
- Automatically generates comprehensive reports in PDF or HTML format
- Includes scan results, severity classification, and recommended actions

### (Optional) Learning Module
- The tool is designed to support future learning from past scans
- With enough data, it will adjust its scoring model for higher accuracy

## Technologies Used

- **Frontend**: React.js, Axios, Chart.js
- **Backend**: Python, Flask
- **Scanning Engine**: socket, nmap, custom Python scripts
- **AI/ML**: scikit-learn, pandas, joblib (Decision Tree Classifier)
- **Reporting**: Jinja2, html2pdf / WeasyPrint
- **API Layer**: REST API built with Flask
- **Database**: (Optional) SQLite or MongoDB for persistence

## AI Techniques Used

- **Model**: Decision Tree Classifier
- **Input Features**:
  - Open ports
  - Banner strings
  - Header checks
  - Credential usage
- **Output**:
  - Risk level: Low, Medium, or High
  - Recommended fix or CVE match
- The model is stored in .joblib format and is optimized for fast classification during live scans.

## User Interaction Flow

1. **User submits target** IP or domain through the dashboard.
2. The **backend scanner** begins the vulnerability assessment.
3. Collected data is **processed by the AI model**, which scores and classifies findings.
4. Results are displayed on the **React dashboard**, showing stats, charts, and tables.
5. User can **export the full report** as PDF or HTML.
6. (Optionally) Feedback can be used to **retrain the model** for better accuracy.

## Installation and Usage

### Backend Setup
```bash
git clone https://github.com/your-username/ai-vulnerability-tracker.git
cd ai-vulnerability-tracker
pip install -r requirements.txt
python app.py

### cd frontend
npm install
npm start

## Folder Structure
├── backend/
│   ├── app.py
│   ├── scanner.py
│   ├── ai_model.py
│   └── report_generator.py
├── frontend/
│   ├── public/
│   └── src/
│       ├── components/
│       └── App.jsx
├── data/
│   └── model.joblib
├── reports/
│   └── report_<timestamp>.pdf

## API Endpoints

| Endpoint                   | Method | Description                          |
|----------------------------|--------|--------------------------------------|
| `/api/scan`                | POST   | Submit a scan request                |
| `/api/scan/<id>`           | GET    | Get results of a specific scan       |
| `/api/vulnerabilities`     | GET    | List all detected vulnerabilities    |
| `/api/export/<id>`         | GET    | Export the report in PDF/HTML format |

All endpoints return structured JSON responses.

## Future Enhancements (Planned)

- Add brute-force attack detection
- Integrate CVE feeds from MITRE/NIST
- Build retraining module using past data
- Deploy using Docker for scalability
- Implement user authentication and role-based access

## Acknowledgments

Special thanks to:
- INSA Cybersecurity Summer Camp
- OWASP Foundation
- Open-source communities of Python, Flask, React, and scikit-learn
- The many ethical hackers and researchers who inspired this idea

**BY TEAM-32**
