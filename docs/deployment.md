# Vuka Deployment & Production Environment

The Vuka platform is deployed across multiple environments that work together to provide the complete Vuka experience.

The deployment structure separates the user-facing applications, backend services, database, external APIs, and AI services. This allows each part of the platform to perform a specific role while contributing to the overall functionality of Vuka.

---

## Deployment Architecture

The Vuka platform consists of the following major components:

* **Vercel** - Hosting platform for the Vuka Informational Website and Dashboard
* **Heroku** - Hosting platform for the Vuka Backend API
* **Database** - Persistent storage for Vuka application data
* **Serper API** - External search and content discovery service
* **YouTube API** - External video content service
* **Google Gemini** - Artificial intelligence service used by Vuka
* **GitHub** - Source code repository and version control platform



---

## Frontend Deployment

### Informational Website

The Vuka Informational Website is deployed through Vercel.

Its purpose is to provide visitors with information about:

* Vuka and its purpose
* How Vuka works
* The problem Vuka addresses
* The founders and team
* How users can contact the team
* How users can get started with the platform

The informational website acts as the public-facing entry point into the Vuka ecosystem.

### Production Website

The informational website is publicly accessible through its deployed Vercel URL.




---

### Dashboard

The Vuka Dashboard is also deployed through Vercel.

The dashboard provides the web interface through which users interact with the main functionality of the Vuka platform.

The dashboard communicates with the backend through HTTP API requests rather than storing application data directly in the frontend.

The dashboard provides access to functionality including:

* User information
* Personalized content
* Missions
* Assessments
* Progress tracking
* Opportunities
* Profile information
* Settings

<div class="feature-card">

<img src="../images/dashboard.png" alt="Vuka Dashboard">

</div>


---

## Backend Deployment

### Heroku

The Vuka Backend API is deployed using Heroku.

The backend provides the REST API consumed by the Vuka frontend applications.

The backend is responsible for:

* User authentication
* User registration
* User data management
* Onboarding
* Content management
* Learning and mission-related functionality
* Assessment-related API operations
* Progress tracking
* Watched content
* Opportunities
* AI integration
* Communication between frontend applications and external services

The backend acts as the central application layer of the Vuka platform.

---

## Backend API

The Vuka frontend applications communicate with the backend through REST API requests.

The backend receives requests from the frontend, processes the required application logic, communicates with the database or external services, and returns the appropriate response.

```text
        Vuka Frontend

        Informational Website
                +
            Dashboard
                |
                |
            REST API
                |
                |
                v

            Vuka Backend

            Authentication
            Registration
            Onboarding
            Content
            Missions
            Assessments
            Progress
            Opportunities
                |
                |
                v

        Application Data
```

The frontend is responsible for presentation and user interaction, while the backend handles application processing and data operations.

---

## API Configuration

The frontend applications use the deployed backend API as their API base URL.

The API base URL is configured through environment settings rather than being repeatedly hard-coded throughout individual screens or services.

This allows the frontend applications to communicate with the deployed backend while keeping API configuration centralized.

Example:

```env
API_BASE_URL=https://[VUKA-BACKEND-URL]
```

The actual production backend URL should be added to the production environment configuration.


---

## Environment Variables and Secrets

Environment variables are used for configuration values and credentials that should not be included directly in source code.

The Vuka platform uses environment variables including:

```text
SERPER_API_KEY
YOUTUBE_API_KEY
GEMINI_API_KEY
API_BASE_URL
DATABASE_URL
```

These values allow the application to communicate with external services and the production database without embedding sensitive credentials directly into the source code.

---

## Local Development Environment

During local development, environment variables can be stored in a `.env` file.

Example:

```env
SERPER_API_KEY=api_key
YOUTUBE_API_KEY=api_key
GEMINI_API_KEY=api_key
API_BASE_URL=backend_url
DATABASE_URL=database_url
```

The `.env` file should be excluded from version control.

Example `.gitignore` configuration:

```gitignore
.env
.env.local
.env.production
```

Sensitive credentials should never be committed to GitHub.

---

## Production Environment Variables

Production environments should provide their own environment variables through the configuration mechanisms provided by the hosting platform.

The production environment includes configuration values such as:

| Variable          | Purpose                              |
| ----------------- | ------------------------------------ |
| `API_BASE_URL`    | Address of the deployed Vuka backend |
| `DATABASE_URL`    | Production database connection       |
| `SERPER_API_KEY`  | Authentication for Serper API        |
| `YOUTUBE_API_KEY` | Authentication for YouTube API       |
| `GEMINI_API_KEY`  | Authentication for Gemini API        |

---

## External Services

The Vuka backend communicates with external services to provide content retrieval, search, video content, and artificial intelligence functionality.

### Serper API

The Serper API is used for search and content discovery.

The backend uses the configured Serper API credentials to retrieve relevant search results that can be processed by the Vuka platform.

### YouTube API

The YouTube API provides video content used by Vuka.

Retrieved video content can be processed and matched against the user's interests to support the personalized learning experience.

### Google Gemini

Google Gemini provides AI functionality within the Vuka platform.

Gemini supports functionality such as:

* Content matching
* Content analysis
* Assessment generation
* Personalized recommendations
* AI-supported processing


---

## Database Deployment

The Vuka backend communicates with a persistent database used to store application data.

The database contains information associated with:

* User registration
* User profiles
* Authentication
* Onboarding
* User interests
* Career aspirations
* Content
* Missions
* Assessments
* Progress
* Watched content
* Opportunities

---

## Source Code and Version Control

The Vuka source code is maintained using Git and hosted through GitHub.

GitHub provides:

* Source code management
* Version control
* Collaboration
* Change tracking
* Repository organization
* Deployment integration

The repository contains the source code required to build and deploy the Vuka platform.

Sensitive credentials are excluded from the repository.

---

## Deployment Process

The Vuka deployment process moves the application from development into the production environment.

```text
Development
     |
     v
  GitHub
     |
     +----------------+
     |                |
     v                v
  Vercel           Heroku
     |                |
     v                v
 Frontend          Backend
     |                |
     +--------+-------+
              |
              v
       Vuka Production
```

The frontend and backend are deployed independently while communicating through the configured API.

---

## Deployment Verification

After deployment, the applications are checked to confirm that the production environment is functioning correctly.

### Frontend Verification

The following are verified:

* Vuka website loads successfully
* Navigation between pages works
* Images and assets load correctly
* Forms work correctly
* Interactive elements work correctly
* Dashboard loads successfully
* Dashboard API requests reach the backend
* Authentication flows work correctly
* Personalized content loads correctly
* Missions load correctly
* Opportunities load correctly
* Progress information loads correctly

### Backend Verification

The following are verified:

* Backend application starts successfully
* API endpoints are accessible
* Authentication endpoints respond correctly
* API requests return expected status codes
* Database operations work correctly
* Registration operations work correctly
* Onboarding operations work correctly
* Content endpoints work correctly
* Mission endpoints work correctly
* Progress endpoints work correctly
* Assessment endpoints work correctly
* AI integration works correctly
* External API integrations work correctly

---

## Production Validation Checklist

| Category          | Verification                    | Status |
| ----------------- | ------------------------------- | ------ |
| Website           | Website loads successfully      | ☐      |
| Website           | Navigation works                | ☐      |
| Website           | Images load                     | ☐      |
| Dashboard         | Dashboard loads                 | ☐      |
| Dashboard         | Authentication works            | ☐      |
| Dashboard         | API requests work               | ☐      |
| Dashboard         | Personalized content loads      | ☐      |
| Dashboard         | Missions load                   | ☐      |
| Dashboard         | Opportunities load              | ☐      |
| Backend           | Application starts              | ☐      |
| Backend           | API endpoints work              | ☐      |
| Backend           | Authentication works            | ☐      |
| Backend           | Database connection works       | ☐      |
| Backend           | Content APIs work               | ☐      |
| Backend           | Assessment APIs work            | ☐      |
| Backend           | AI integration works            | ☐      |
| External Services | Serper API works                | ☐      |
| External Services | YouTube API works               | ☐      |
| External Services | Gemini API works                | ☐      |
| Security          | Secrets excluded from GitHub    | ☐      |
| Configuration     | Production variables configured | ☐      |

---

## Production URLs

The production URLs for the Vuka platform should be documented in one location.

| Application           | Production URL                                 |
| --------------------- | ---------------------------------------------- |
| Informational Website | `https://beta-informational-website.` |
| Backend API           | `https://vuka-cfc18f5fb.herokuapp.com/docs`                  |


---


## Deployment Completion

The Vuka deployment is considered complete when:

* The informational website is publicly accessible.
* The dashboard is publicly accessible.
* The backend API is operational.
* The frontend communicates successfully with the backend.
* Authentication operates correctly.
* Database operations work correctly.
* External APIs are accessible.
* Gemini AI integration works correctly.
* Production environment variables are configured.
* Sensitive credentials are excluded from GitHub.
* Core user workflows have been successfully verified.

---

## Deployment Summary

The Vuka production environment separates the platform into several major layers.

The **Vercel environment** provides the user-facing applications, including the informational website and dashboard.

The **Heroku environment** provides the backend API and application logic.

The **database layer** provides persistent storage for platform data.

The **external service layer** provides search, video content, and AI functionality through Serper, YouTube, and Gemini.

Together, these components form the complete deployed Vuka platform.

```text
VUKA PLATFORM

┌──────────────────────────────────┐
│        USER EXPERIENCE           │
│                                  │
│   Informational Website          │
│   Dashboard                      │
│                                  │
│            Vercel                │
└──────────────────────────────────┘

┌──────────────────────────────────┐
│        APPLICATION LAYER         │
│                                  │
│          Backend API             │
│                                  │
│            Heroku                │
└──────────────────────────────────┘

┌──────────────────────────────────┐
│           DATA LAYER             │
│                                  │
│            Database              │
└──────────────────────────────────┘

┌──────────────────────────────────┐
│     EXTERNAL SERVICES            │
│                                  │
│    Serper   YouTube   Gemini     │
└──────────────────────────────────┘

┌──────────────────────────────────┐
│       SOURCE CONTROL             │
│                                  │
│            GitHub                │
└──────────────────────────────────┘
```
