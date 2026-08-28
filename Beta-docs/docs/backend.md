#  VUKA Backend

<div class="page-hero">

<div class="hero-content">

<h1>VUKA Backend</h1>

<p class="hero-subtitle">
The intelligent application layer powering authentication, personalization, learning, assessments, progress tracking, opportunities, and graduate verification.
</p>

<div class="hero-badges">

<span class="badge badge-primary">Python</span> <span class="badge badge-secondary">FastAPI</span> <span class="badge badge-success">PostgreSQL</span> <span class="badge badge-info">SQLAlchemy</span> <span class="badge badge-ai">Google Gemini</span>

</div>

</div>

</div>

---

##  Backend Overview

The **VUKA backend** is the central application layer responsible for processing requests from the frontend, enforcing business rules, managing application data, and integrating external services.

It is implemented using **Python** and **FastAPI** and provides RESTful APIs consumed by the VUKA frontend.

<div class="feature-grid">

<div class="feature-card">

<h3> Authentication</h3>

<p>
Handles registration, login, JWT authentication, MFA, password recovery, account security, and user management.
</p>

</div>

<div class="feature-card">

<h3> Personalization</h3>

<p>
Uses onboarding information such as interests, goals, and career aspirations to personalize learning and opportunities.
</p>

</div>

<div class="feature-card">

<h3> Learning</h3>

<p>
Discovers educational resources and organizes them into personalized content pathways.
</p>

</div>

<div class="feature-card">

<h3> AI Assessments</h3>

<p>
Uses Google Gemini to generate educational assessments based on learning content.
</p>

</div>

<div class="feature-card">

<h3> Progress</h3>

<p>
Tracks assessment performance, learning activity, streaks, completed assessments, and category performance.
</p>

</div>

<div class="feature-card">

<h3> Opportunities</h3>

<p>
Discovers scholarships, internships, bootcamps, and other career-development opportunities.
</p>

</div>

</div>

---

#  Backend Architecture

The VUKA backend follows a **layered architecture**.

Each layer has a specific responsibility, which makes the system easier to maintain, test, scale, and extend.

<div class="architecture-diagram">

</div>

---

##  Architecture Layers

<div class="feature-grid">

<div class="feature-card">

<h3> Router Layer</h3>

<p>
Handles HTTP requests and responses and provides the REST API endpoints used by the frontend.
</p>

<ul>
<li>Receives requests</li>
<li>Validates request data</li>
<li>Calls services</li>
<li>Returns API responses</li>
</ul>

</div>

<div class="feature-card">

<h3>Service Layer</h3>

<p>
Contains the application's business and application logic.
</p>

<ul>
<li>Authentication</li>
<li>Personalization</li>
<li>Content processing</li>
<li>Assessment generation</li>
<li>Progress calculations</li>
</ul>

</div>

<div class="feature-card">

<h3> Repository Layer</h3>

<p>
Provides the database access layer and handles database queries and persistence.
</p>

<ul>
<li>Create records</li>
<li>Retrieve records</li>
<li>Update records</li>
<li>Delete records</li>
</ul>

</div>

<div class="feature-card">

<h3> Model Layer</h3>

<p>
Defines database entities and relationships using SQLAlchemy.
</p>

<ul>
<li>Users</li>
<li>Content</li>
<li>Assessments</li>
<li>Progress</li>
</ul>

</div>

<div class="feature-card">

<h3> Schema Layer</h3>

<p>
Defines request and response structures using Pydantic.
</p>

<ul>
<li>Validation</li>
<li>Serialization</li>
<li>Type checking</li>
<li>API consistency</li>
</ul>

</div>

<div class="feature-card">

<h3> Integration Layer</h3>

<p>
Provides isolated clients for communicating with external services.
</p>

<ul>
<li>Google Gemini</li>
<li>YouTube API</li>
<li>Google Serper</li>
<li>SMTP</li>
</ul>

</div>

</div>

---

#  Backend Project Structure
The VUKA backend is organized into separate modules according to their responsibilities.
```text
            vuka/
            │
            ├── integrations/
            │   ├── gemini_client.py
            │   ├── serper_client.py
            │   ├── trivia_client.py
            │   └── youtube_client.py
            │
            ├── models/
            │   ├── registration.py
            │   ├── onboarding.py
            │   ├── contents.py
            │   ├── content_pathway.py
            │   ├── generated_assessment.py
            │   ├── verifiedassessment.py
            │   ├── userprogress.py
            │   ├── opportunity_recommendation.py
            │   └── security.py
            │
            ├── repositories/
            │   ├── auth.py
            │   ├── registration.py
            │   ├── onboarding.py
            │   ├── contents.py
            │   ├── content_pathway.py
            │   ├── generated_assessment.py
            │   ├── verifiedassessment.py
            │   ├── userprogress.py
            │   └── opportunity_recomendation.py
            │
            ├── routers/
            │   ├── registration.py
            │   ├── onboarding.py
            │   ├── contents.py
            │   ├── content_pathway.py
            │   ├── generated_assessment.py
            │   ├── verifiedassessment.py
            │   ├── userprogress.py
            │   ├── opportunity_recommendation.py
            │   ├── verification.py
            │   └── admin.py
            │
            ├── schemas/
            │   ├── auth.py
            │   ├── registration.py
            │   ├── onboarding.py
            │   ├── contents.py
            │   ├── generated_assessment.py
            │   ├── mfa.py
            │   ├── opportunity_recommendation.py
            │   ├── userprogress.py
            │   ├── verification.py
            │   └── verifiedassessment.py
            │
            ├── security/
            │   ├── audit.py
            │   ├── crypto.py
            │   └── password.py
            │
            ├── services/
            │   ├── auth.py
            │   ├── mfa.py
            │   ├── security.py
            │   ├── email.py
            │   ├── registration.py
            │   ├── onboarding.py
            │   ├── contents.py
            │   ├── content_pathway.py
            │   ├── generated_assessment.py
            │   ├── verifiedassessment.py
            │   ├── userprogress.py
            │   └── opportunity_recommendation.py
            │
            ├── ingestion/
            │   └── opportunity.py
            │
            └── scripts/
                └── fetch_opportunities.py
```

---

#  Authentication & User Management

The authentication module manages user identity and account security throughout VUKA.

<div class="feature-grid">

<div class="feature-card">

<h3> Registration</h3>

<p>
Creates and manages user accounts and profile information.
</p>

</div>

<div class="feature-card">

<h3> Login</h3>

<p>
Authenticates users and provides secure access to protected resources.
</p>

</div>

<div class="feature-card">

<h3> MFA</h3>

<p>
Provides multi-factor authentication to strengthen account security.
</p>

</div>

<div class="feature-card">

<h3> Account Security</h3>

<p>
Tracks login attempts, supports account lockout, password recovery, and security events.
</p>

</div>

</div>

### Authentication Features

* Registration
* Login
* JWT access tokens
* Refresh tokens
* Logout
* Password reset
* Multi-factor authentication (MFA)
* Account lockout
* Login-attempt tracking
* User profile management

---

#  Onboarding & Personalization

The **Onboarding Module** establishes the user's learning and career profile.

Information captured includes:

* Career aspirations
* Personal goals
* Interests
* Preferred social platforms

The onboarding information becomes the foundation for VUKA's personalization system.


The information captured during onboarding is subsequently used by the content and opportunity recommendation components.

---

#  Content Management

The VUKA backend retrieves educational content from external platforms and organizes relevant resources for users.

### Supported Sources

* YouTube
* TikTok
* Instagram
* Web search

The backend manages the content discovery process so that the frontend does not need to communicate directly with third-party content providers.

Relevant content metadata is stored in the database.

---

##  Content Pathways

**Content Pathways** connect educational content to the user's interests and learning journey.

A content pathway establishes relationships between:

* User onboarding information
* User interests
* Educational content
* External media resources

The pathway also provides the external media URL required to access the learning resource.

```text
User Interests
      │
      ▼
Content Discovery
      │
      ▼
Relevant Content
      │
      ▼
Content Pathway
      │
      ▼
Learning Resource
```

---

#  AI Assessment Generation

VUKA integrates **Google Gemini** to generate educational assessments based on learning content.

The assessment generation system creates questions from educational resources and organizes them into assessment categories.

### Assessment Categories

<div class="feature-grid">

<div class="feature-card">

<h3> Technical Skills</h3>

<p>Assesses technical knowledge and practical skills.</p>

</div>

<div class="feature-card">

<h3> Soft Skills</h3>

<p>Evaluates communication, collaboration, and interpersonal abilities.</p>

</div>

<div class="feature-card">

<h3> Career Readiness</h3>

<p>Evaluates preparation for professional environments and career development.</p>

</div>

<div class="feature-card">

<h3> Digital Literacy</h3>

<p>Assesses knowledge and understanding of digital tools and environments.</p>

</div>

</div>

### Generated Question Structure

Each generated question contains:

* Question text
* Answer options
* Correct answer
* Explanation

```text
Educational Content
        │
        ▼
   Google Gemini
        │
        ▼
Generated Assessment
        │
 ┌──────┼─────────┐
 ▼      ▼         ▼
Question Options Explanation
        │
        ▼
      User
```

---

#  Progress Tracking

The **Progress Tracking Module** records and calculates the user's learning performance.

### Tracked Information

| Metric                    | Description                               |
| ------------------------- | ----------------------------------------- |
| **Assessment Scores**     | Records assessment results                |
| **Average Performance**   | Calculates overall performance            |
| **Learning Streaks**      | Tracks continued learning activity        |
| **Weekly Activity**       | Measures learning activity over time      |
| **Category Performance**  | Tracks performance by assessment category |
| **Completed Assessments** | Records assessments completed by the user |

The resulting progress information is exposed through the backend API and presented through the VUKA dashboard.

                Learning Activity
                        │
                        ▼
                Progress Tracking
                        │
                ┌──────┼──────────────┐
                │      │              │
                ▼      ▼              ▼
                Scores Streaks      Activity
                │      │              │
                └──────┼──────────────┘
                        │
                        ▼
                Category Performance
                        │
                        ▼
                    Dashboard

---

#  Opportunity Recommendation

The **Opportunity Recommendation Module** discovers and organizes career-development opportunities.

### Opportunity Types

<div class="feature-grid">

<div class="feature-card">

<h3> Scholarships</h3>

<p>Funding and educational opportunities for learners and graduates.</p>

</div>

<div class="feature-card">

<h3> Internships</h3>

<p>Professional development and workplace opportunities.</p>

</div>

<div class="feature-card">

<h3> Bootcamps</h3>

<p>Intensive learning and skills-development programs.</p>

</div>

</div>

### Opportunity Categories

Opportunities can be categorized according to fields such as:

* Technology
* Fintech
* Engineering
* Business
* Healthcare
* Creative Arts

### Opportunity Discovery Flow

```text
User Profile
     │
     ▼
Interests & Career Goals
     │
     ▼
Opportunity Discovery
     │
     ▼
Google Serper
     │
     ▼
Relevant Opportunities
     │
     ▼
VUKA Backend
     │
     ▼
Frontend
```

---

#  Graduate Verification

The **Graduate Verification Module** manages documents submitted by graduates for verification.

### Supported Document Formats

<div class="feature-grid">

<div class="feature-card">

<h3> PDF</h3>

<p>Portable document format files.</p>

</div>

<div class="feature-card">

<h3> JPEG</h3>

<p>JPEG image documents.</p>

</div>

<div class="feature-card">

<h3> PNG</h3>

<p>PNG image documents.</p>

</div>

</div>

The verification module manages the submission and processing of verification documents within the VUKA backend.

---

#  Database

VUKA uses **PostgreSQL** as its primary relational database.

**SQLAlchemy** is used as the Object-Relational Mapper (ORM).

The database stores:

* User accounts
* Learning information
* Content
* Content pathways
* Assessments
* Assessment results
* User progress
* Opportunities
* Verification information
* Authentication records
* Security records
* Audit activity

---

##  Main Database Entities

| Entity                         | Purpose                                                       |
| ------------------------------ | ------------------------------------------------------------- |
| **Registration**               | User account information                                      |
| **Onboarding**                 | User career and learning profile                              |
| **Content**                    | Educational resources                                         |
| **Content Pathway**            | Structured learning resources                                 |
| **Generated Assessment**       | AI-generated assessment questions                             |
| **Verified Assessment**        | User assessment results                                       |
| **User Progress**              | Learning performance                                          |
| **Opportunity Recommendation** | Scholarships, internships, bootcamps, and other opportunities |
| **Verification Document**      | Graduate verification information                             |
| **Login Attempt**              | Authentication activity                                       |
| **Audit Log**                  | System activity                                               |
| **Security Event**             | Security activity                                             |
| **Roles**                      | User access roles                                             |
| **Permissions**                | Access permissions                                            |

---

#  External Integrations

VUKA communicates with external services through dedicated integration clients.

| Service                  | Purpose                               |
| ------------------------ | ------------------------------------- |
| **Google Gemini**        | AI-generated assessments              |
| **YouTube Data API**     | Educational video discovery           |
| **Google Serper**        | Opportunity and web-content discovery |
| **Open Trivia Database** | Quiz content                          |
| **SMTP**                 | Email notifications                   |

---

##  Integration Architecture

External integrations are isolated from the main application through dedicated integration clients.

```text
                         VUKA BACKEND
                              │
                       Integration Layer
                              │
       ┌──────────────────────┼──────────────────────┐
       │                      │                      │
       ▼                      ▼                      ▼
 Google Gemini          YouTube API          Google Serper
       │                      │                      │
       ▼                      ▼                      ▼
 Assessments              Content            Opportunities


       ┌──────────────────────┴──────────────────────┐
       │                                             │
       ▼                                             ▼
Open Trivia Database                               SMTP
       │                                             │
       ▼                                             ▼
 Quiz Content                               Email Notifications
```

This architecture ensures that third-party API implementation details remain isolated from the core application.

### Benefits

* Clear separation of responsibilities
* Easier testing
* Easier maintenance
* Reduced coupling
* External services can be replaced independently
* Third-party implementation details remain isolated

---

#  Backend Request Flow

A typical VUKA request follows the layered architecture.

```text
                    FRONTEND
                       │
                       │ HTTP Request
                       ▼
                ┌──────────────┐
                │    ROUTER    │
                └──────┬───────┘
                       │
                       ▼
                ┌──────────────┐
                │   SERVICE    │
                └──────┬───────┘
                       │
             ┌─────────┴─────────┐
             │                   │
             ▼                   ▼
       REPOSITORY          INTEGRATIONS
             │                   │
             ▼                   ▼
          MODELS           EXTERNAL APIs
             │
             ▼
        POSTGRESQL
             │
             ▼
        API RESPONSE
             │
             ▼
          FRONTEND
```

This architecture ensures that each layer performs a clearly defined responsibility.

---

#  VUKA Backend Intelligence

The backend brings together the major components of the VUKA platform.

<div class="feature-grid">

<div class="feature-card">

<h3> User</h3>

<p>
Provides the identity and profile information used throughout the platform.
</p>

</div>

<div class="feature-card">

<h3> Personalization</h3>

<p>
Transforms onboarding information into personalized learning and opportunity recommendations.
</p>

</div>

<div class="feature-card">

<h3> Content</h3>

<p>
Discovers and organizes educational resources from external platforms.
</p>

</div>

<div class="feature-card">

<h3> AI</h3>

<p>
Uses Gemini to transform educational content into assessments.
</p>

</div>

<div class="feature-card">

<h3> Progress</h3>

<p>
Measures learning performance and activity.
</p>

</div>

<div class="feature-card">

<h3> Opportunities</h3>

<p>
Connects users with relevant career-development opportunities.
</p>

</div>

</div>




---

#  End-to-End Backend Flow

The complete VUKA backend workflow can be summarized as:

<div class="feature-card">
<img src="../images/dataflow.png" alt="Vuka Home Dashboard" >
</div>

---

<div class="final-callout">

<h2> The VUKA Backend</h2>

<p>
The VUKA backend provides the intelligence and application infrastructure behind the platform. It connects authentication, onboarding, personalized learning, AI-generated assessments, progress tracking, career opportunities, verification, databases, and external services into a single coordinated system.
</p>

</div>
