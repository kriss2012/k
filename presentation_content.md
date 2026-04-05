# ASG Platform: Investor & Stakeholder Presentation Content

This document contains a slide-by-slide breakdown for the Apex Startup Group (ASG) platform pitch. It includes technical architecture, business logic, and UI mockups.

---

## Slide 1: Mission & Vision
**Title**: Apex Startup Group (ASG)  
**Subtitle**: Empowering the Next Generation of Founders  
**Visual**: ![ASG Logo Concept](https://apexstartupgroup.com/logo-concept.png)  
**Content**:
- Unified ecosystem for Students, Founders, and Mentors.
- Bridging the gap between institutional learning and startup success.
- Powered by Data, AI, and Community.

---

## Slide 2: The Problem we Solve
**Challenge**: Fragmentation in the startup support system.  
**Solution**: A single interface to manage innovation tracks, institutional records (NAAC), and professional networking.
- **Accessibility**: Mobile-first approach for 24/7 connectivity.
- **Data-Driven**: Structured repos for talent discovery.

---

## Slide 3: Core Technology Stack
**Architecture**: Cloud-Native Full-Stack Android Platform  
**Details**:
- **Mobile Foundation**: Native Android (Kotlin & Jetpack Compose).
- **Backend Architecture**: Node.js with Express and Prisma ORM.
- **Data Persistence**: Highly scalable PostgreSQL.
- **Infrastructure**: Render for hosting, Firebase for Auth and Push Notifications.

---

## Slide 4: User Onboarding (UX Highlight)
**Visual**: ![Onboarding Mockup](file:///C:/Users/krishna/.gemini/antigravity/brain/859ebe86-192d-482c-9e37-c2c61173f91f/asg_onboarding_mockup_1775314157639.png)  
**Key Features**:
- Mandatory 4-step registration: Identity, Role, Institution, Interests.
- Ensures a high-trust community by mapping users to specific cohorts (Student/Founder/Investor).

---

## Slide 5: Innovation Dashboard
**Visual**: ![Home Dashboard Mockup](file:///C:/Users/krishna/.gemini/antigravity/brain/859ebe86-192d-482c-9e37-c2c61173f91f/asg_home_dashboard_mockup_1775314178480.png)  
**Key Features**:
- **NAAC/NEP Integration**: Direct logging of institutional innovation milestones.
- **Ecosystem Map**: Interactive visualization of local startup density.
- **Hackathon Portal**: End-to-end event management from registration to demo.

---

## Slide 6: Student Repository & Networking
**Visual**: ![Networking Mockup](file:///C:/Users/krishna/.gemini/antigravity/brain/859ebe86-192d-482c-9e37-c2c61173f91f/asg_networking_repo_mockup_1775314201185.png)  
**Key Features**:
- Talent search by skills, college, or role.
- One-click 'Connect' logic for mentoring or co-founding requests.

---

## Slide 7: Database Architecture (Technical Schema)
**Model ERD**:
```mermaid
erDiagram
    USER ||--o{ EVENT : creates
    USER ||--o{ CONNECTION : sends
    USER ||--o{ CONNECTION : receives
    USER ||--o{ MESSAGE : sends
    USER ||--o{ MESSAGE : receives

    USER {
        string id PK "Firebase UID"
        string name
        string email
        string role "USER | ADMIN"
        string skills
        string college
    }

    EVENT {
        string id PK
        string title
        string description
        datetime date
        string category
    }

    CONNECTION {
        string id PK
        string senderId FK
        string receiverId FK
        string status "PENDING|ACCEPTED|REJECTED"
    }

    MESSAGE {
        string id PK
        string content
        string senderId FK
        string receiverId FK
        datetime timestamp
    }
```

---

## Slide 8: Development Budget (MVP Phase)

> [!NOTE]
> Estimated figures for a 12-week development cycle for 2026.

| Item | Estimated Cost | Details |
| :--- | :--- | :--- |
| **UI/UX Design** | $9,000 | Branding, Component Library, Figma Prototypes |
| **Android Dev** | $18,000 | Kotlin/Compose App Development |
| **Backend & Cloud** | $12,000 | Node.js API, PostgreSQL DB, CI/CD Setup |
| **QA & Security** | $4,500 | functional testing & pen-testing |
| **Cloud Ops (Y1)** | $1,500 | Render, Firebase, and Managed DB costs |
| **TOTAL** | **$45,000** | Initial Launch Phase |

---

## Slide 9: Future Roadmap
- **ASG AI Agent**: Voice-activated startup advisor.
- **Global Networking**: Cross-institutional hub for collaborative hacking.
- **Investment Portal**: Direct pipeline from MVP repo to Seed funding.

---

### Speaker Notes
1. **Slide 1**: Emphasize that ASG is not just an app, it's a movement to systematize entrepreneurship in colleges.
2. **Slide 8**: The budget focuses purely on technical delivery. Marketing and Ops are excluded from the Dev budget.
