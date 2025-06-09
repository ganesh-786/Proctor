# Online Exam Proctoring System

A modular, microservices-based solution for secure, automated online exam proctoring.

---

## Table of Contents

1. [Architecture & Code Structure](#architecture--code-structure)
2. [Features & 80/20 Focus](#features--8020-focus)
3. [Installation & Setup](#installation--setup)
4. [Usage](#usage)
5. [Methodology & Workflow](#methodology--workflow)
6. [Research & References](#research--references)
7. [YouTube Tutorials](#youtube-tutorials)
8. [Contributing](#contributing)
9. [License](#license)
10. [Collaborative Project Plan & 4-Week Accelerated Challenges](#collaborative-project-plan-4-week-accelerated-challenges)

---

## Architecture & Code Structure

```
proctor-system/
├── frontend/                  # React app (WebRTC video, dashboard)
│   ├── src/
│   │   ├── components/        # UI components: Dashboard, Alerts, VideoFeed
│   │   ├── services/          # API wrappers: Auth, Recording, Alerts
│   │   └── utils/             # Helpers: formatters, validators
│   └── package.json
├── backend/                   # Node.js / Express (or Django / Flask)
│   ├── src/
│   │   ├── controllers/       # REST endpoints
│   │   ├── middleware/        # Auth, rate-limit, error handling
│   │   ├── models/            # DB schemas: User, Session, Violation
│   │   ├── services/          # Business logic: ExamSession, ViolationDetector
│   │   └── utils/             # Logging, config, email
│   └── package.json
├── ai-services/               # Python microservices (Dockerized)
│   ├── face_recognition/      # Real-time face detection & liveness
│   ├── gaze_detection/        # Eye-gaze anomaly detection
│   ├── screen_monitor/        # Screenshot diff & tab-focus tracking
│   └── requirements.txt       # Python dependencies
├── infra/                     # Kubernetes / Terraform configs
│   ├── k8s/
│   └── terraform/
└── docs/
    ├── architecture.md
    ├── api_spec.md
    └── dev_guide.md
```

---

## Features & 80/20 Focus

> Focus on the 20% of features that mitigate 80% of cheating:

1. **Face & Liveness Detection**
2. **Simple Gaze-Away Flags**
3. **Tab-Switch / Screen Capture Monitoring**
4. **Session Recording & Suspicion Scoring**
5. **Reviewer Dashboard**

Once these are solid, extend to emotion detection, keystroke logging, multi-camera support, etc.

---

## Installation & Setup

### Prerequisites

* Node.js >=14
* Python 3.8+
* Docker & Docker Compose
* Kubernetes CLI (kubectl) & Terraform

### Clone & Install

```bash
# Clone repository
git clone https://github.com/your-org/proctor-system.git
cd proctor-system

# Frontend
tcd frontend && npm install

# Backend
cd ../backend && npm install

# AI Services
cd ../ai-services && pip install -r requirements.txt
```

### Running Locally (Docker)

```bash
docker-compose up --build
```

### Deploy to Kubernetes

```bash
cd infra/terraform
terraform init
terraform apply
```

---

## Usage

1. **Register**: Student signs up with email/password + ID photo
2. **Schedule Exam**: Instructor creates an exam session
3. **Start Exam**: Browser-lockdown and WebRTC stream initialize
4. **Monitoring**: AI services analyze face, gaze, and screen in real time
5. **Review**: Export flagged events report (PDF/CSV) and manual review

---

## Methodology & Workflow

1. **Authentication & Enrollment**

   * Multi-factor: password + ID verification snapshot
2. **Session Initialization**

   * Browser lockdown extension
   * WebRTC video + screen share
3. **Real-Time Monitoring**

   * Face detection (spoofing, mask, multiple)
   * Gaze tracking (off-screen glance flags)
   * Screen capture analysis (tab switches)
4. **Post-Exam Analysis**

   * Replay video with overlayed flags
   * Generate suspicion-score timeline
5. **Reporting & Review**

   * PDF/CSV exports
   * Manual override dashboard

---

## Research & References

* Xu et al., *iExam: Face Detection & Recognition System* (2021). Lightweight real-time Zoom monitoring with 90.4% accuracy. <br> [Article1](https://www.researchgate.net/publication/369814086_Online_Exam_Proctoring_System),  [Article2](https://www.mdpi.com/2079-3197/11/6/120?utm_source=chatgpt.com)
* Shih et al., *AI-assisted Gaze Detection* (2024). Reduces proctor review time by >50%. <br>[Article1](https://arxiv.org/abs/2206.13356?utm_source=chatgpt.com)
* Coghlan et al., *Ethics of AI Proctoring* (2020). Privacy, fairness, transparency guidelines.<br> [Article1](https://arxiv.org/abs/2011.07647?utm_source=chatgpt.com)
* Balash et al., *Educator Adoption of Remote Proctoring* (2023). 35% plan to continue post-pandemic.

---

## YouTube Tutorials

* [AI Automated Exam Proctoring Solution](https://youtu.be/example1)
* [Building Facial Recognition in Python](https://youtu.be/example2)
* [Project Clear Check: Proctoring UI Deep Dive](https://youtu.be/example3)
* [Real-Time Gaze Tracking with OpenCV](https://youtu.be/example4)

---
## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -m 'Add feature'`)
4. Push to your branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

---

## License

Distributed under the MIT License. See [LICENSE](LICENSE) for details.

---

# Collaborative Project Plan & 4-Week Accelerated Challenges

A condensed 4-week roadmap to build the core Online Exam Proctoring System collaboratively, focusing on the essential 20% of features that deliver 80% of value.

---

## 🗓️ 4-Week Timeline

| Week | Sprint Focus                   | Key Deliverables                           |
| ---- | ------------------------------ | ------------------------------------------ |
| 1    | Kickoff, Auth & Frontend Setup | - Project kickoff & backlog prioritization |

* JWT auth + ID-photo upload endpoint
* React app skeleton + WebRTC demo                 |
  \| 2    | Face Recognition & Gaze Detection| - Dockerized face\_recognition service with `/detect`
* Gaze detection microservice & frontend stub       |
  \| 3    | Screen Monitoring & Alerts       | - Chrome extension for tab-switch & screenshots
* Backend rule-engine & real-time alerts via WebSockets|
  \| 4    | Recording, Reporting & Review    | - Session recording pipeline + S3 storage integration
* Suspicion-score reports (PDF/CSV)
* Reviewer dashboard MVP                            |

---

## 🚀 Weekly Challenges & Tasks

### Week 1: Kickoff, Auth & Frontend Setup

* **Tasks**:

  * Define MVP scope, roles, GitHub Projects board
  * Implement JWT authentication & ID-photo upload in backend
  * Scaffold React app and integrate a simple WebRTC peer connection
* **Tips**:

  * Use Passport.js (Node) or DRF JWT for auth flows
  * Leverage `simple-peer` library for quick WebRTC setup

### Week 2: Face Recognition & Gaze Detection

* **Tasks**:

  * Containerize FastAPI face\_recognition service; preload models
  * Build gaze\_detection service using OpenCV’s `solvePnP`
  * Create a frontend stub to call both AI endpoints and log responses
* **Tips**:

  * Preload models at service startup to reduce latency
  * Structure AI services as lightweight Docker containers

### Week 3: Screen Monitoring & Real-Time Alerts

* **Tasks**:

  * Develop Chrome extension for tab visibility and periodic screenshots
  * Implement backend rule-engine that consumes AI flags and tab events
  * Push alerts to frontend via `socket.io` and display in an Alerts panel
* **Tips**:

  * Use `chrome.tabs.onActivated` and `chrome.desktopCapture` APIs
  * Keep rule logic configurable (e.g., JSON-based thresholds)

### Week 4: Recording, Reporting & Reviewer Dashboard

* **Tasks**:

  * Stream-record video + screen into 5-minute chunks; upload to S3
  * Compute suspicion-score timeline and generate PDF/CSV reports
  * Build a minimal Reviewer Dashboard for flag review and overrides
* **Tips**:

  * Use chunked uploads to avoid memory bloat
  * Template PDF reports with PDFKit or LaTeX for consistent styling

---

## 🛠️ Methodology & Collaboration Tips

* **Version Control**: Trunk-based with feature branches; enforce PR reviews.
* **Code Quality**: ESLint/Prettier (JS), Flake8/Black (Python) in CI.
* **Testing**: Unit tests (Jest, PyTest), integration (Supertest, FastAPI TestClient).
* **CI/CD**: GitHub Actions for linting, tests, and Docker image builds.
* **Communication**: Daily 15-min stand-ups, GitHub Issues for each task, Slack channels.

---

*This accelerated plan targets a functional MVP in 4 weeks by concentrating on the highest-impact features first.*


