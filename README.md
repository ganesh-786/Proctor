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

