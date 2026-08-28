# VUKA PLATFORM ARCHITECTURE


<div class="hero">

<div class="hero-content">



<p class="hero-description">
A personalized digital platform connecting users with relevant learning
content, assessments, and opportunities through intelligent personalization.
</p>

<div class="hero-meta">

<span>Production System</span> <span>Technical Documentation</span> <span>Version: 0.1</span>

</div>

</div>

</div>

---

## Table of Contents

1. [Architecture Overview](#1-architecture-overview)
2. [Product Design Foundation](#2-product-design-foundation)
3. [Vuka Product Interface](#3-vuka-product-interface)
4. [Frontend Architecture](#4-frontend-architecture)
5. [Frontend API Communication](#5-frontend-api-communication)
6. [Backend Architecture](#6-backend-architecture)
7. [Database Architecture](#7-database-architecture)
8. [Registration Architecture](#8-registration-architecture)
9. [Authentication and MFA](#9-authentication-and-mfa)
10. [Onboarding Architecture](#10-onboarding-architecture)
11. [Personalization Architecture](#11-personalization-architecture)
12. [AI Integration](#12-ai-integration)
13. [Content Retrieval Architecture](#13-content-retrieval-architecture)
14. [Content Matching](#14-content-matching)
15. [Missions Architecture](#15-missions-architecture)
16. [Watched History and Progress](#16-watched-history-and-progress)
17. [Assessment Architecture](#17-assessment-architecture)
18. [Opportunity Recommendation](#18-opportunity-recommendation)
19. [API Architecture](#19-api-architecture)
20. [API Request Architecture](#20-api-request-architecture)
21. [Data Architecture](#21-data-architecture)
22. [Security Architecture](#22-security-architecture)
23. [Testing Architecture](#23-testing-architecture)
24. [Deployment Architecture](#24-deployment-architecture)
25. [Environment Configuration](#25-environment-configuration)
26. [Production Request Lifecycle](#26-production-request-lifecycle)
27. [Error Handling and Troubleshooting](#27-error-handling-and-troubleshooting)
28. [From Development to Final Product](#28-from-development-to-final-product)
29. [Final Platform Architecture](#29-final-platform-architecture)
30. [Architecture Summary](#30-architecture-summary)
31. [Architecture Principles](#31-architecture-principles)
32. [Final Architecture Statement](#32-final-architecture-statement)
33. [Architecture Assets](#33-architecture-assets)

---

# 1. Architecture Overview

Vuka is a personalized digital platform designed to connect users with
relevant digital content, learning missions, assessments, and opportunities
based on information collected during registration and onboarding.

The platform combines a user-facing application layer, backend API,
relational database, authentication services, artificial intelligence,
and external content and search services.

Rather than treating these components as isolated applications, Vuka
was designed as an integrated platform in which every major component
has a defined responsibility.

<div class="architecture-card">

<img src="../images/Group Beta System Diagram.png" alt="Vuka Deployment Architecture">

</div>


## Architecture Philosophy

Vuka follows several architectural principles.

### Separation of Responsibilities

Each layer performs a defined function instead of placing all application
logic inside a single component.

### API-First Communication

Frontend applications communicate with the backend through HTTP APIs
rather than directly accessing the database.

### Service-Oriented Backend

Business operations are organized into services that can be maintained
and tested independently.

### Data-Driven Personalization

Information collected during onboarding provides the foundation for
personalized content and recommendations.

### Production-Oriented Security

Authentication, MFA, protected endpoints, environment variables,
and controlled access are treated as core platform requirements.

---

# 2. Product Design Foundation

The Vuka architecture begins with the product experience.

Before implementation, the system was structured around the journey of
the user rather than around individual technical components.

## Core User Experience

| Stage         | User Experience                         |
| ------------- | --------------------------------------- |
| Registration  | User creates an account                 |
| Verification  | Account identity is verified            |
| MFA           | Additional authentication protection    |
| Onboarding    | User provides interests and aspirations |
| Home          | Personalized dashboard                  |
| Missions      | Relevant video-based content            |
| Assessments   | Learning evaluation                     |
| Opportunities | Relevant external opportunities         |
| Progress      | System-generated progress information   |
| Settings      | Account and preference management       |

## User Journey

<div class="feature-card">
<img src="../images/userflow.png" alt="Vuka Home Dashboard" >
</div>




# 3. Vuka Product Interface

The Vuka platform uses a consistent visual identity across its web, mobile, and supporting digital experiences.

The visual system establishes the foundation for how Vuka communicates its identity through its logos, colors, typography, interface components, spacing, imagery, and interaction patterns.

---




---

## 3.3 Brand Colors


### Vuka Color System

| Vuka Navy                                                   | Vuka Green                                                  | Vuka Blue                                                   |                                                 |                                                |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |  |  |
| ![#072540](https://dummyimage.com/120x60/072540/072540.png) | ![#009450](https://dummyimage.com/120x60/009450/009450.png) | ![#0977E5](https://dummyimage.com/120x60/0977E5/0977E5.png) | !
| `#072540`                                                   | `#009450`                                                   | `#0977E5`                                                                                                                                                     

---

<div class="feature-card">
<img src="../images/styleguide.png" alt="Vuka Home Dashboard" >
</div>


---

## 3.12 Responsive Design

Vuka is designed to provide a consistent experience across desktop, tablet, and mobile devices.

| Device       | Design Consideration                         |
| ------------ | -------------------------------------------- |
| Desktop      | Multi-column layouts and expanded navigation |
| Tablet       | Adaptive content grids                       |
| Mobile       | Single-column layouts and compact navigation |
| Small Mobile | Optimized controls and reduced spacing       |


---


---

## 3.14 Final Visual Identity

The Vuka visual system brings together the major elements of the product's interface.

| Design Element        | Purpose                          |
| --------------------- | -------------------------------- |
| **Brand Logos**       | Establish Vuka identity          |
| **Color System**      | Establish visual recognition     |
| **Typography**        | Create hierarchy and readability |
| **Buttons**           | Communicate actions              |
| **Cards**             | Organize content                 |
| **Icons**             | Support navigation and actions   |
| **Imagery**           | Improve content discovery        |
| **Spacing**           | Maintain visual rhythm           |
| **Responsive Design** | Support multiple devices         |

The combination of these elements establishes a consistent visual language across the Vuka platform.


---

## 3.16 Design Asset Checklist

Before completing this section, ensure that the following assets have been added:

* [ ] Primary Vuka logo
* [ ] Secondary Vuka logo
* [ ] Official Vuka style guide
* [ ] Typography specification
* [ ] Spacing specification
* [ ] Icon system
* [ ] Imagery guidelines
* [ ] Dashboard screenshot
* [ ] Onboarding screenshots
* [ ] Missions screenshot
* [ ] Opportunities screenshot
* [ ] Responsive design screenshot

---

## Application Structure

```text
Home
├── Dashboard
├── Personalized information
├── Progress
└── Recommended activity

Missions
├── Personalized videos
├── Search
├── Filtering
└── Watched content

Opportunities
├── Recommended opportunities
└── External resources

Settings
├── Profile
├── Preferences
└── Account controls
```


---

# 4. Frontend Architecture

The frontend is responsible for presentation, navigation, user interaction,
authentication state, API communication, and rendering information returned
by the backend.

The frontend does **not** directly communicate with PostgreSQL.

## Frontend Responsibilities

* Interface rendering
* Navigation
* User interaction
* Authentication state
* API requests
* Personalized content
* Missions
* Assessments
* Opportunities
* Progress
* Error handling

## Frontend Structure

```text
app/
├── home/
├── login/
├── signup/
├── onboarding/
├── missions/
├── opportunities/
├── progress/
├── settings/
└── navigation/

lib/
└── api/

components/
└── shared UI components

styles/
└── application styles

public/
└── static assets
```

---

# 5. Frontend API Communication

The frontend communicates with the backend through a centralized API utility.

A simplified implementation is:

```javascript
const BASE_URL = process.env.NEXT_PUBLIC_API_URL;

async function request(path, options = {}) {
    const token = localStorage.getItem("access_token");

    const response = await fetch(
        `${BASE_URL}${path}`,
        {
            ...options,
            headers: {
                "Content-Type": "application/json",
                ...(token
                    ? {
                        Authorization:
                            `Bearer ${token}`
                    }
                    : {})
            }
        }
    );

    if (!response.ok) {
        throw new Error(
            `Request failed: ${response.status}`
        );
    }

    return response.json();
}
```

## API Functions

```javascript
export async function getCurrentUser() {
    return request("/registration/me");
}

export async function getDashboard(onboardingId) {
    return request(
        `/user-progress/summary/${onboardingId}`
    );
}

export async function getWatchedHistory(userId) {
    return request(
        `/watched-history/${userId}`
    );
}
```

Centralizing API communication provides a consistent location for:

* Authentication headers
* Request configuration
* Response handling
* Error processing
* API URL configuration

---

# 6. Backend Architecture

The Vuka backend provides the application's main services.

It is implemented using FastAPI and Python.

## Backend Responsibilities

* HTTP request handling
* Authentication
* Authorization
* Validation
* Business logic
* Database operations
* AI integration
* Content retrieval
* Progress tracking
* Assessment generation
* Opportunity retrieval

## Backend Structure

```text
backend/
│
├── routers/
│
├── services/
│
├── models/
│
├── schemas/
│
├── database/
│
├── authentication/
│
├── ai/
│
└── configuration/
```

## Router Layer

Routers define HTTP endpoints.

```python
router = APIRouter(
    prefix="/content_pathway",
    tags=["Content Pathways"]
)
```

## Service Layer

Business logic is placed inside services.

```python
class ContentPathwayService:

    def __init__(self, db):
        self.db = db

    def get_pathway(self, pathway_id):
        return (
            self.db
            .query(ContentPathway)
            .filter(
                ContentPathway.id == pathway_id
            )
            .first()
        )
```

This separation improves maintainability and testability.

---

# 7. Database Architecture

PostgreSQL provides persistent storage for Vuka.

SQLAlchemy provides the application's database abstraction layer.

The database stores information related to:

* Users
* Registration
* Onboarding
* Interests
* Content
* Missions
* Assessments
* Progress
* Watched history
* Opportunities

## Registration Entity

```text
Registration
────────────────────────────
user_id
first_name
last_name
username
email
pass_hash
preferred_language
country
is_verified
is_active
user_type
```

## Onboarding Entity

```text
Onboarding
────────────────────────────
onboarding_id
user_id
user_interests
social_platforms
user_goal
career_aspirations
```

## Content Entity

```text
Content
────────────────────────────
content_id
external_media_url
source_platform
media_description
datetime
```


---

# 8. Registration Architecture

Registration establishes the user's identity within Vuka.

The process creates the account and stores the required user information
in the database.

Sensitive credentials are not stored as plain-text passwords.

## Registration Data

```json
{
    "first_name": "...",
    "last_name": "...",
    "username": "...",
    "email": "...",
    "preferred_language": "...",
    "country": "...",
    "user_type": "..."
}
```

Registration also supports account verification and authentication controls.

---

# 9. Authentication and MFA

Authentication protects access to personalized user information and
protected API resources.

The authentication system includes:

* Registration
* Verification
* MFA
* Login
* Access tokens
* Protected API requests

## Protected Request

```http
GET /registration/me

Authorization: Bearer <ACCESS_TOKEN>
```

Authentication information should never be hard-coded into source files.

## Security Configuration

```text
SECRET_KEY
DATABASE_URL
GEMINI_API_KEY
SERPER_API_KEY
YOUTUBE_API_KEY
```

These values must be supplied through secure environment configuration.

---

# 10. Onboarding Architecture

Onboarding transforms a newly registered account into a personalized
user profile.

The platform collects information that can help understand the user's:

* Interests
* Goals
* Social platforms
* Career aspirations

## Onboarding Data

```text
User Interests

Social Platforms

User Goals

Career Aspirations
```

These values are stored within the user's onboarding record.


---

# 11. Personalization Architecture

Personalization is one of Vuka's central capabilities.

The system uses information collected during onboarding to identify
content relevant to individual users.

## Personalization Inputs

### User Profile

```text
Interests
Goals
Career Aspirations
Preferred Platforms
```

### Content Pool

```text
Video Information
Description
Platform
URL
Metadata
```

These inputs are processed through the content and AI services.


---

# 12. AI Integration

Vuka uses Gemini as part of its AI functionality.

The AI layer supports functionality including:

* Content analysis
* Personalized matching
* Assessment generation
* Recommendation processing

## AI Configuration

```python
GEMINI_MODEL = "gemini-3.5-flash"
```

The API key is loaded from environment configuration.

## AI Architecture

The AI service receives controlled information from the application.

The application determines:

* What information is provided
* What content is retrieved
* What output format is expected
* How generated information is stored
* How generated results are presented

This provides a controlled boundary between Vuka and the external
AI service.

---

# 13. Content Retrieval Architecture

Vuka retrieves external content through third-party services.

## Serper

Used for search-based content discovery.

## YouTube API

Used for video-related content discovery.

## Content Service

```python
class ContentService:

    def __init__(self):
        self.serper_api_key = os.getenv(
            "SERPER_API_KEY"
        )

        self.youtube_api_key = os.getenv(
            "YOUTUBE_API_KEY"
        )
```

## Environment Configuration

```text
SERPER_API_KEY
SERPER_SEARCH_URL
YOUTUBE_API_KEY
```

Actual production values must never be included in documentation.

---

# 14. Content Matching

Retrieved content is not simply presented to every user.

Vuka uses onboarding information to identify content relevant to the
individual user's interests and goals.

## Matching Information

```text
User Interests
Career Aspirations
User Goals
Content Description
Content Source
```

The resulting content becomes part of the personalized user experience.

### Architectural distinction

| System            | Main question                          |
| ----------------- | -------------------------------------- |
| Content Retrieval | What content is available?             |
| Personalization   | What content is relevant to this user? |

Keeping these responsibilities separate allows both systems to evolve
independently.

---

# 15. Missions Architecture

Missions are personalized activities presented to users.

A mission may contain an external media resource such as a YouTube or
TikTok video.

## Mission Features

* Personalized content
* Search
* Filtering
* Video links
* Watched history
* Progress information

## Mission Interaction

The user does not manually mark a mission as completed.

The system records the relevant interaction when the user clicks
the video.

```javascript
async function openMission(mission) {

    await addWatchedMission(
        mission,
        userId
    );

    window.open(
        mission.external_media_url,
        "_blank"
    );
}
```

---

# 16. Watched History and Progress

Watched history provides a persistent record of content interactions.

## Create Watched Record

```http
POST /watched-history/{user_id}
```

## Retrieve Watched History

```http
GET /watched-history/{user_id}
```

## Progress Representation

```text
USER ACTIVITY

Watched History

Progress Summary

Dashboard
```

The progress system reflects recorded system activity rather than
requiring the user to manually report completion.

---

# 17. Assessment Architecture

Assessments provide an evaluation layer around the learning experience.

Vuka can use AI-generated assessment content based on relevant
learning material.

## Assessment Components

```text
Content

Assessment

Questions

User Responses

Evaluation

Score

Completion
```

## Assessment API Example

```http
GET /assessments/completed/{onboarding_id}
```


---

# 18. Opportunity Recommendation

Opportunities extend Vuka beyond content consumption.

The recommendation process can use:

```text
Interests
Career Aspirations
Goals
User Profile
```



---

# 19. API Architecture

The Vuka backend exposes RESTful API endpoints grouped around platform
functionality.

## API Resources

| Resource         | Responsibility              |
| ---------------- | --------------------------- |
| Registration     | User identity               |
| Onboarding       | Personalization profile     |
| Content          | External and stored content |
| Content Pathways | Structured content          |
| Missions         | Personalized activities     |
| Watched History  | User interaction            |
| Assessments      | Learning evaluation         |
| Progress         | User progress               |
| Opportunities    | External opportunities      |

## Example

```http
GET /registration/me
```

**Purpose**

Retrieve the currently authenticated user's information.

## Dashboard Example

```javascript
const dashboard = await getDashboard(
    onboardingId
);
```

The frontend uses the onboarding identifier to retrieve personalized
progress information.

---

# 20. API Request Architecture

The backend separates request handling from application logic.

```text
┌─────────────────────────────┐
│ Frontend API Utility        │
│ Request preparation         │
└─────────────────────────────┘

┌─────────────────────────────┐
│ FastAPI Router              │
│ Endpoint handling           │
└─────────────────────────────┘

┌─────────────────────────────┐
│ Schema Validation           │
│ Input validation            │
└─────────────────────────────┘

┌─────────────────────────────┐
│ Service Layer               │
│ Business logic              │
└─────────────────────────────┘

┌─────────────────────────────┐
│ Database / External Service │
│ Data operation              │
└─────────────────────────────┘

┌─────────────────────────────┐
│ Response Schema             │
│ Structured response         │
└─────────────────────────────┘
```

This card-based representation is intentionally preferred over
a diagram containing numerous arrows.

---

# 21. Data Architecture

Vuka's data can be understood through four major domains.

## Identity

```text
Registration
MFA
Authentication
User Profile
```

## Personalization

```text
Onboarding
Interests
Goals
Career Aspirations
```

## Learning

```text
Content
Missions
Watched History
Assessments
Progress
```

## Discovery

```text
Search
Content Retrieval
Opportunities
Recommendations
```

---

# 22. Security Architecture

Security is implemented across multiple platform layers.

| Layer          | Protection                       |
| -------------- | -------------------------------- |
| Account        | Password hashing                 |
| Verification   | Account verification             |
| Authentication | Access tokens                    |
| MFA            | Additional authentication factor |
| API            | Protected endpoints              |
| Configuration  | Environment variables            |
| Database       | Controlled application access    |
| Frontend       | Authenticated API requests       |

## Sensitive Configuration

The following must never be committed to GitHub:

```text
DATABASE_URL
SECRET_KEY
GEMINI_API_KEY
SERPER_API_KEY
YOUTUBE_API_KEY
```

Development environments may use:

```bash
export GEMINI_API_KEY="..."
export SERPER_API_KEY="..."
export YOUTUBE_API_KEY="..."
```

Production environments should use the hosting provider's secure
environment-variable management system.

---

# 23. Testing Architecture

Testing is organized around the API resources and expected
application behavior.

## Testing Categories

```text
Registration
Onboarding
Content
Content Pathways
Missions
Assessments
Progress
Opportunities
Authentication
```

Tests include:

* Happy-path tests
* Validation tests
* Missing-resource tests
* Authentication tests
* Invalid-input tests
* Error-response tests

## Postman Example

```javascript
pm.test(
    "Status code is 200 or 201 Success",
    function () {

        pm.expect(
            pm.response.code
        ).to.be.oneOf([200, 201]);

    }
);
```

## Validation Example

```javascript
const progressId =
    pm.variables.get("progress_id");

if (
    !progressId ||
    String(progressId).trim() === ""
) {
    throw new Error(
        "progress_id is required and cannot be empty"
    );
}
```

---

# 24. Deployment Architecture

The development and production environments are treated separately.

## Development Environment

```text
Developer Machine

Frontend
Backend
Database
API Integrations
```

## Production Environment

```text
Production Frontend

Production API

Production Database

External Services

Gemini
Serper
YouTube
```

---

# 25. Environment Configuration

Environment variables separate deployment configuration from source code.

## Frontend

```env
NEXT_PUBLIC_API_URL=[INSERT_API_URL]
```

## Backend

```env
DATABASE_URL=[INSERT_DATABASE_URL]

SECRET_KEY=[INSERT_SECRET]

GEMINI_API_KEY=[INSERT_KEY]

SERPER_API_KEY=[INSERT_KEY]

SERPER_SEARCH_URL=[INSERT_URL]

YOUTUBE_API_KEY=[INSERT_KEY]
```

Actual secrets must never be included in the documentation.

---

# 26. Production Request Lifecycle

The production request lifecycle can be represented as a set of
responsibility layers.

```text
┌────────────────────────────┐
│ USER INTERACTION           │
└────────────────────────────┘

┌────────────────────────────┐
│ FRONTEND                   │
└────────────────────────────┘

┌────────────────────────────┐
│ FASTAPI                    │
└────────────────────────────┘

┌────────────────────────────┐
│ VALIDATION                 │
└────────────────────────────┘

┌────────────────────────────┐
│ SERVICE LOGIC              │
└────────────────────────────┘

┌────────────────────────────┐
│ DATA / AI / EXTERNAL APIs  │
└────────────────────────────┘

┌────────────────────────────┐
│ STRUCTURED RESPONSE        │
└────────────────────────────┘
```

This layout emphasizes architectural responsibility without turning
the documentation into an arrow diagram.

---

# 27. Error Handling and Troubleshooting

Production reliability requires the ability to identify where failures
occur.

| Problem                   | Likely Area             |
| ------------------------- | ----------------------- |
| Failed to fetch           | Frontend/API connection |
| 401 Unauthorized          | Authentication          |
| 404 Not Found             | Resource or route       |
| 422 Validation Error      | Request schema          |
| 500 Internal Server Error | Backend                 |
| Application crashed       | Deployment/runtime      |
| Missing onboarding ID     | User/profile state      |
| AI failure                | Gemini integration      |
| Search failure            | Serper integration      |
| Video retrieval failure   | YouTube integration     |

## Development Debugging

Useful development information includes:

```text
BASE_URL: [API BASE URL]

REQUEST PATH: /registration/me

FULL URL: [FULL REQUEST URL]

AUTH TOKEN EXISTS: true / false
```

Sensitive token values must never be printed.

---

# 28. From Development to Final Product

The completed Vuka system represents several integrated development
stages.

<div class="architecture-grid">

<div class="architecture-card">

### Product Layer

* User needs
* UX design
* Interface design
* Feature definition

</div>

<div class="architecture-card">

### Engineering Layer

* Frontend
* Backend
* Database
* Authentication
* AI
* External APIs

</div>

<div class="architecture-card">

### Validation Layer

* API testing
* Integration testing
* Error handling
* Security testing

</div>

<div class="architecture-card">

### Production Layer

* Deployment
* Environment configuration
* Monitoring
* Maintenance

</div>

</div>


---

# 30. Architecture Summary

| Component          | Responsibility                 | Technology                 |
| ------------------ | ------------------------------ | -------------------------- |
| Web Frontend       | User interface                 | Next.js / React            |
| Mobile Application | Mobile experience              | Flutter / Dart             |
| API                | Application services           | FastAPI                    |
| ORM                | Database interaction           | SQLAlchemy                 |
| Database           | Persistent storage             | PostgreSQL                 |
| Authentication     | Identity protection            | MFA + token authentication |
| AI                 | Personalization and generation | Gemini                     |
| Search             | Content/opportunity discovery  | Serper                     |
| Video Discovery    | Video content                  | YouTube API                |
| Deployment         | Production hosting             | [INSERT PLATFORM]          |

---

# 31. Architecture Principles

## Separation

Presentation, business logic, data, and external integrations have
separate responsibilities.

## Security

Authentication and sensitive configuration are fundamental
platform requirements.

## Personalization

The user experience is influenced by information collected during
onboarding.

## Extensibility

Individual services can evolve without requiring the entire platform
to be redesigned.

## Testability

API functionality is organized into independently testable resources.

## Maintainability

Routers, services, schemas, models, and frontend API utilities are
separated to make the codebase easier to understand and maintain.

## Production Readiness

The system is designed to operate beyond local development through
hosting, environment configuration, API integrations, and production
database infrastructure.

---

# 32. Final Architecture Statement

Vuka is not simply a frontend application connected to a database.

It is a multi-layer platform combining:

<div class="architecture-grid">

<div class="architecture-card">User Experience</div>

<div class="architecture-card">Authentication</div>

<div class="architecture-card">Onboarding</div>

<div class="architecture-card">Personalization</div>

<div class="architecture-card">Artificial Intelligence</div>

<div class="architecture-card">Content Retrieval</div>

<div class="architecture-card">Missions</div>

<div class="architecture-card">Assessments</div>

<div class="architecture-card">Opportunities</div>

<div class="architecture-card">Progress Tracking</div>

<div class="architecture-card">Security</div>

<div class="architecture-card">Production Infrastructure</div>

</div>

These components form a unified platform in which user information,
content, intelligence, and application services work together to
produce a personalized experience.


---

