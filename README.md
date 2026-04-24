# 🚀 ApexStack: Premium Full-Stack Enterprise Template

![SaanviStack Hero](/home/raven/.gemini/antigravity/brain/0e34cd78-0977-463f-ad0b-5adbc09a1bac/saanvistack_hero_banner_1777060665416.png)

ApexStack is a high-performance, production-ready full-stack template designed for modern enterprise applications. It combines the speed of **FastAPI**, the robustness of **PostgreSQL**, and the elegance of **React** with a dark-mode first design system.

## 🌐 Live Demo
- **Live Project Showcase**: [https://saanvirajput.github.io/apex-stack-fastapi/](https://saanvirajput.github.io/apex-stack-fastapi/)


## 🏗️ Architectural Overview

```mermaid
graph TD
    User((User)) -->|HTTPS| Traefik[Traefik Reverse Proxy]
    Traefik -->|Routing| Frontend[React SPA]
    Traefik -->|API Calls| Backend[FastAPI Server]
    Backend -->|Auth/Data| DB[(PostgreSQL)]
    Backend -->|Async Tasks| Celery[Celery Worker]
    Celery -->|Queue| Redis[(Redis)]
    Backend -->|Monitoring| Sentry[Sentry SDK]
```

## ⚡ Tech Stack & Features

- **Backend**: FastAPI (Python 3.12+)
  - **ORM**: SQLModel for seamless Type Hinting & DB operations.
  - **Auth**: Secure JWT-based authentication with OAuth2.
  - **Async**: Built-in support for background tasks and web sockets.
- **Frontend**: React (Vite + TypeScript)
  - **Styling**: Tailwind CSS + shadcn/ui.
  - **State**: TanStack Query for robust data fetching.
- **Infrastructure**: Docker Compose (Dev & Prod)
  - **Proxy**: Traefik with automatic Let's Encrypt SSL.
  - **Testing**: End-to-End testing with Playwright.

## 🛠️ User Experience Flow

```mermaid
sequenceDiagram
    participant U as User
    participant F as Frontend
    participant B as Backend
    participant D as Database

    U->>F: Enter Credentials
    F->>B: POST /api/v1/login/access-token
    B->>D: Verify User
    D-->>B: User Data
    B-->>F: JWT Access Token
    F->>U: Redirect to Dashboard
    U->>F: Click "Create Item"
    F->>B: POST /api/v1/items/ (with JWT)
    B->>D: Save Item
    B-->>F: Item Created (201)
    F-->>U: Success Notification
```

## 🚀 Getting Started

### 1. Initialize the Stack
```bash
docker compose up -d
```

### 2. Configure Environment
Update the `.env` file with your secret keys:
```env
PROJECT_NAME="ApexStack"
STACK_NAME="apex-stack"
SECRET_KEY="your_generated_secret"
```

### 3. Generate Secret Keys
```bash
python -c "import secrets; print(secrets.token_urlsafe(32))"
```

## 📦 Deployment

This project is optimized for deployment via **Docker Compose** on any VPS or using cloud-native platforms like **DigitalOcean App Platform** or **AWS App Runner**.

Refer to [deployment.md](./deployment.md) for detailed production setup.

---
*Architected and maintained by Saanvi Rajput.*
