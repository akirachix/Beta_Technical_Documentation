# Security

<div class="page-hero">

<div class="hero-content">

<h1>VUKA Security</h1>

<p class="hero-subtitle">
Security is built into the VUKA platform to protect user accounts, application data, authentication flows, and sensitive system information.
</p>

<div class="hero-badges">

<span class="badge badge-primary">JWT Authentication</span> <span class="badge badge-success">MFA</span> <span class="badge badge-secondary">Secure APIs</span> <span class="badge badge-info">Input Validation</span> <span class="badge badge-ai">Protected Data</span>

</div>

</div>

</div>

---

## Security Overview

Security is an important part of the VUKA platform.

The system incorporates security mechanisms throughout the application to protect user accounts, authentication credentials, API access, personal information, and other sensitive system data.

One of the key security mechanisms implemented by VUKA is **Multi-Factor Authentication (MFA)**, which provides an additional layer of protection beyond the user's password.

Security is considered across:

<div class="feature-grid">

<div class="feature-card">

<h3> Authentication</h3>

<p>
User identities are protected through authentication mechanisms including JWT-based access tokens and Multi-Factor Authentication.
</p>

</div>

<div class="feature-card">

<h3> Authorization</h3>

<p>
Authenticated users must only be able to access information and resources for which they are authorized.
</p>

</div>

<div class="feature-card">

<h3> Credentials</h3>

<p>
Passwords, API keys, database credentials, and other secrets must not be exposed or committed to the repository.
</p>

</div>

<div class="feature-card">

<h3>Validation</h3>

<p>
User input and API requests should be validated before being processed by the application.
</p>

</div>

<div class="feature-card">

<h3> Monitoring</h3>

<p>
Authentication activity, login attempts, audit information, and security events are tracked by the system.
</p>

</div>

<div class="feature-card">

<h3> Production Security</h3>

<p>
Production credentials and sensitive configuration should be managed through secure environment configuration.
</p>

</div>

</div>

---

# Authentication Security

Authentication is responsible for establishing and protecting the identity of VUKA users.

The authentication system supports:

- User registration
- User login
- JWT access tokens
- Refresh tokens
- Logout
- Password reset
- Multi-Factor Authentication
- Account lockout
- Login-attempt tracking
- User profile management

The authentication flow provides multiple layers of protection around user accounts.

                                              USER
                                                │
                                                ▼
                                        ┌───────────────┐
                                        │    LOGIN      │
                                        └───────┬───────┘
                                                │
                                                ▼
                                        ┌───────────────┐
                                        │   PASSWORD    │
                                        │ VERIFICATION  │
                                        └───────┬───────┘
                                                │
                                                ▼
                                        ┌───────────────┐
                                        │      MFA      │
                                        │ VERIFICATION  │
                                        └───────┬───────┘
                                                │
                                                ▼
                                        ┌───────────────┐
                                        │ JWT ACCESS    │
                                        │    TOKEN      │
                                        └───────┬───────┘
                                                │
                                                ▼
                                        ┌───────────────┐
                                        │  PROTECTED    │
                                        │  API ACCESS   │
                                        └───────────────┘

---

# Multi-Factor Authentication

VUKA uses **Multi-Factor Authentication (MFA)** to provide an additional layer of account protection.

MFA reduces reliance on passwords alone by requiring an additional authentication factor during the authentication process.

<div class="feature-grid">

<div class="feature-card">

<h3> Primary Authentication</h3>

<p>
The user provides their normal login credentials.
</p>

</div>

<div class="feature-card">

<h3> Additional Verification</h3>

<p>
The system performs an additional verification step through the MFA mechanism.
</p>

</div>

<div class="feature-card">

<h3> Protected Access</h3>

<p>
Successful authentication allows the user to access protected VUKA resources.
</p>

</div>

</div>

### MFA Security Goal

                Password Alone
                    │
                    ▼
                NOT ENOUGH
                    │
                    ▼
                Additional Verification
                    │
                    ▼
                Authenticated User
                    │
                    ▼
                Protected Resources

MFA therefore provides an additional security boundary around user accounts.

---

# API Security

Authenticated API endpoints must be protected against unauthorized access.

The backend uses authentication and authorization mechanisms to ensure that protected resources are not freely accessible.

Security controls should be applied to API endpoints that handle:

- User information
- Onboarding information
- Learning progress
- Assessments
- Opportunities
- Verification information
- Account settings
- Administrative operations

                    API REQUEST
                        │
                        ▼
                ┌───────────────┐
                │ Authentication│
                │   Check       │
                └───────┬───────┘
                        │
                ┌──────┴──────┐
                │             │
            Valid         Invalid
                │             │
                ▼             ▼
            Authorization      Reject
                Check          Request
                │
            ┌──────┴──────┐
            │             │
        Allowed        Denied
            │             │
            ▼             ▼

  Process API Reject
  Request Access

---

# Authorization

Authentication determines **who the user is**.

Authorization determines **what the user is allowed to access**.

VUKA should ensure that users can only access information associated with their authorized account and permissions.

This is particularly important for resources containing:

- Personal information
- Learning progress
- Assessment results
- Verification information
- Account information
- Administrative resources

### Authorization Principle

The backend must verify that the authenticated user has permission to perform the requested operation.

---

# Credential Protection

Sensitive credentials must never be exposed through the repository or frontend application.

The following information must remain protected:

<div class="feature-grid">

<div class="feature-card">

<h3> Passwords</h3>

<p>
User passwords must never be stored in plain text or committed to source control.
</p>

</div>

<div class="feature-card">

<h3> API Keys</h3>

<p>
Private API keys for services such as Gemini, YouTube, and Serper must remain private.
</p>

</div>

<div class="feature-card">

<h3> Database Credentials</h3>

<p>
Database usernames, passwords, connection strings, and related secrets must not be exposed.
</p>

</div>

<div class="feature-card">

<h3> Environment Configuration</h3>

<p>
Production credentials should be managed through secure environment configuration.
</p>

</div>

</div>

---

# Secrets That Must Never Be Committed

The repository must not contain:

- Passwords
- Private API keys
- Database passwords
- JWT secrets
- SMTP passwords
- Private tokens
- Production credentials
- Encryption secrets

Sensitive configuration should instead be provided through environment variables or an appropriate secure configuration mechanism.

For example:

```text
GEMINI_API_KEY=********
YOUTUBE_API_KEY=********
SERPER_API_KEY=********
DATABASE_URL=********
JWT_SECRET=********
SMTP_PASSWORD=********
```

---

# Input Validation

User input must be validated before it is processed by the backend.

Input validation helps ensure that the application receives data in the expected format.

Validation should be applied to:

- Registration information
- Login information
- Onboarding information
- Assessment responses
- Opportunity information
- Verification submissions
- API parameters
- Request bodies

The VUKA backend uses **Pydantic schemas** to define and validate API request and response structures.

                User Input
                    │
                    ▼
                Pydantic Schema
                    │
                    ▼
                Validation
                    │
                ┌──┴───────┐
                │          │
            Valid     Invalid
                │          │
                ▼          ▼
             Service    Reject
                Layer      Request

---

# Authentication Failure Handling

Authentication failures should be handled securely.

The application should avoid exposing unnecessary information that could help an attacker understand internal authentication mechanisms.

Examples of authentication failures include:

- Invalid credentials
- Expired tokens
- Invalid tokens
- Failed MFA verification
- Locked accounts
- Unauthorized API requests
- Invalid refresh tokens

The system should return appropriate responses while avoiding the exposure of sensitive internal information.

---

# Login Attempt Tracking

VUKA tracks authentication activity through login-attempt information.

This supports security mechanisms such as:

- Monitoring failed login attempts
- Detecting repeated authentication failures
- Supporting account lockout
- Providing security audit information

Login attempts form part of the broader security architecture.

                Login Attempt
                    │
                    ▼
                Authentication
                    │
                ┌────┴─────┐
                │          │
             Success    Failure
                │          │
                ▼          ▼
            Access    Record Attempt
                            │
                            ▼
                    Security Controls
                            │
                      ┌─────┴─────┐
                      │           │
                    Continue     Lockout


---

# Account Lockout

Account lockout provides an additional defense against repeated unsuccessful authentication attempts.

When authentication failures reach the applicable security threshold, the system can restrict further access to protect the account.

Account lockout works together with:

- Login-attempt tracking
- Authentication
- MFA
- Security event tracking
- Audit logging

---

# Audit Logging

Security-related activity should be recorded through the application's audit mechanisms.

The backend contains a dedicated security module:

```text
security/
├── audit.py
├── crypto.py
└── password.py
```

Audit information can provide visibility into important system activities and support security monitoring and investigation.

---

# Security Architecture

Security is not implemented as a single isolated component.

Instead, it is distributed throughout the VUKA architecture.
<<<<<<< HEAD

                       VUKA APPLICATION
                              │
                ┌─────────────┴─────────────┐
                │                           │
                ▼                           ▼
        ┌───────────────┐           ┌───────────────┐
        │ Authentication│           │ Authorization │
        └───────┬───────┘           └───────┬───────┘
                │                           │
                └─────────────┬─────────────┘
                              │
                              ▼
                       ┌─────────────┐
                       │     MFA     │
                       └──────┬──────┘
                              │
                              ▼
                       ┌─────────────┐
                       │ API Security│
                       └──────┬──────┘
                              │
                ┌─────────────┼─────────────┐
                │             │             │
                ▼             ▼             ▼
          Input          Credential      Access
        Validation       Protection     Control
                │             │             │
                └─────────────┼─────────────┘
                              │
                              ▼
                       Audit & Security
                           Events

<div class="feature-card">
<img src="../images/security.png" alt="Vuka Home Dashboard" >
</div>

# Core Security Principles

The VUKA repository should follow the following security principles.

<div class="feature-grid">

<div class="feature-card">

<h3>1.  Protect Secrets</h3>

<p>
Never commit passwords, private API keys, database credentials, or production secrets.
</p>

</div>

<div class="feature-card">

<h3>2.  Protect APIs</h3>

<p>
Authenticated API endpoints must require appropriate authentication and authorization.
</p>

</div>

<div class="feature-card">

<h3>3. Validate Input</h3>

<p>
Validate user input before it reaches application or database logic.
</p>

</div>

<div class="feature-card">

<h3>4.  Verify Authorization</h3>

<p>
Users should only access information and operations they are authorized to use.
</p>

</div>

<div class="feature-card">

<h3>5.  Minimize Exposure</h3>

<p>
Avoid exposing sensitive information through browser logs, API responses, or error messages.
</p>

</div>

<div class="feature-card">

<h3>6.  Secure Configuration</h3>

<p>
Production credentials should be maintained through secure environment configuration.
</p>

</div>

</div>

---

# Sensitive Information in Browser Logs

Sensitive information should not be exposed through frontend browser logs.

Developers should avoid logging:

- Passwords
- Authentication tokens
- Private API keys
- Database credentials
- MFA secrets
- Personal sensitive information
- Internal security details

Development logging should also be reviewed before production deployment.

---

# Production Configuration

Production credentials must be stored using secure environment configuration.

The source repository should contain configuration templates or documentation where necessary, but not the actual production secrets.

Example:

                Development
                    │
                    ▼
                Environment Variables
                    │
                    ▼
                Application Configuration
                    │
                    ▼
                Backend Services

This allows the application to use different configuration values across development, testing, and production environments without exposing secrets in source control.

---

# Development & Maintenance

Although the VUKA website is **completed and deployed**, the repository should continue to be maintained.

Future development should follow the established architecture and preserve the existing security and application behavior.

When modifying the website or backend:

<div class="feature-grid">

<div class="feature-card">

<h3> Understand the API</h3>

<p>
Understand the existing API contract before changing frontend or backend behavior.
</p>

</div>

<div class="feature-card">

<h3> Reuse Existing Logic</h3>

<p>
Check whether reusable API functions and services already exist before creating new ones.
</p>

</div>

<div class="feature-card">

<h3> Preserve Authentication</h3>

<p>
Do not break the existing authentication and authorization flow.
</p>

</div>

<div class="feature-card">

<h3> Preserve MFA</h3>

<p>
Changes must maintain the existing Multi-Factor Authentication functionality.
</p>

</div>

<div class="feature-card">

<h3> Preserve Personalization</h3>

<p>
AI personalization behavior must continue to use onboarding information appropriately.
</p>

</div>

<div class="feature-card">

<h3> Test Changes</h3>

<p>
Test affected user journeys and the production build before deployment.
</p>

</div>

</div>

---

# Maintenance Checklist

Before deploying a significant change, verify the following:

- [ ] Existing API contracts have been reviewed.
- [ ] Existing reusable API functions have been checked.
- [ ] Duplicate API logic has been avoided.
- [ ] Authentication continues to work.
- [ ] MFA continues to work.
- [ ] Authorization remains intact.
- [ ] AI personalization continues to work.
- [ ] Mission completion continues to occur automatically.
- [ ] Sensitive information is not exposed in browser logs.
- [ ] Production credentials remain protected.
- [ ] Affected user journeys have been tested.
- [ ] The production build has been tested.
- [ ] Documentation has been updated where necessary.

---

# Important System Behaviors

The following behaviors are fundamental to the operation of VUKA.

## 1. Personalization Comes From Onboarding

The user's interests and goals are collected during onboarding and used to personalize the user's experience.

```text
                    Onboarding
                        │
                        ├── Interests
                        ├── Goals
                        └── Career Aspirations
                                │
                                ▼
                        Personalization
                                │
                        ┌─────┴─────┐
                        ▼           ▼
                    Content    Opportunities
```

---

## 2. Content Comes From External APIs

VUKA retrieves potential educational content from external services rather than relying entirely on manually entered content.

External services can include:

- YouTube
- TikTok
- Instagram
- Web search

The backend processes relevant information before presenting it to the frontend.

---

## 3. AI Determines Content Relevance

**Gemini Flash** is used to support the content personalization process.

The system uses information collected during onboarding and content retrieved through external APIs to determine which learning resources are relevant to the user.

```text
            User Interests
                │
                ▼
            External Content
                │
                ▼
            Gemini Flash
                │
                ▼
            Content Relevance
                │
                ▼
            Personalized Learning
```

---

## 4. Progress Is System-Driven

The backend records user activity and provides progress information to the frontend.

Progress can include:

- Assessment scores
- Average performance
- Learning streaks
- Weekly activity
- Category performance
- Completed assessments

The frontend uses this information to present the user's learning progress.

---

## 5. MFA Protects User Accounts

Multi-Factor Authentication provides an additional security mechanism beyond the user's primary authentication credentials.

MFA is therefore an important part of the VUKA account protection model.

---

# Security & System Protection Flow

The overall security model can be summarized as:

```text
                       USER
                         │
                         ▼
                  AUTHENTICATION
                         │
                         ▼
                       MFA
                         │
                         ▼
                  AUTHORIZED ACCESS
                         │
                         ▼
                  PROTECTED API
                         │
              ┌──────────┼──────────┐
              │          │          │
              ▼          ▼          ▼
          Validation  Business   Database
                      Rules       Access
              │          │          │
              └──────────┼──────────┘
                         │
                         ▼
                  AUDIT / SECURITY
                      EVENTS
                         │
                         ▼
                   USER RESPONSE
```

---

<div class="final-callout">

<h2> Security Is a System-Wide Responsibility</h2>

<p>
VUKA security extends beyond authentication. It includes MFA, authorization, input validation, credential protection, secure API access, account protection, audit activity, secure production configuration, and responsible system maintenance.
</p>

</div>
