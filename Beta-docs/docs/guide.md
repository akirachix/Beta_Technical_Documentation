# Developer Guide

Vuka consists of multiple application components, including the Flutter mobile application, web applications, backend API, AI services, and external API integrations.

Each component follows conventions appropriate to its technology while maintaining consistent development principles across the platform.

---

## General Principles

Developers should:

* Write readable, maintainable, and reusable code.
* Use descriptive names for variables, functions, classes, components, and files.
* Keep individual functions and components focused on a single responsibility.
* Avoid duplication of code.
* Separate presentation, business logic, data handling, and API communication.
* Handle errors and provide meaningful error messages.
* Keep sensitive information such as API keys and credentials out of source control.
* Add comments when explaining non-obvious logic.
* Follow the existing structure of the component being modified.

---

# Git Workflow

GitHub is used for version control and collaboration across the Vuka project.

The team uses branches to isolate individual pieces of work before they are reviewed and merged.

## Branch Strategy

Developers should avoid making feature changes directly on the `main` branch.

The general workflow is represented below:

```text
main
│
├── feature/assessment-generation
│
├── feature/mobile-progress
│
├── feature/dashboard-testing
│
└── fix/api-validation
```

A developer should:

1. Start from the latest version of `main`.
2. Create a branch for the task.
3. Implement the changes.
4. Test the changes locally.
5. Commit the changes.
6. Push the branch to GitHub.
7. Open a Pull Request.
8. Address review comments.
9. Merge the approved Pull Request into `main`.

---

## Creating a Branch

Before creating a new branch, update the local `main` branch:

```bash
git checkout main
git pull origin main
```

Create a feature branch:

```bash
git checkout -b feature/feature-name
```

Example:

```bash
git checkout -b feature/assessment-generation
```

---

## Branch Naming

Branches should clearly describe the work being performed.

Recommended formats:

```text
feature/<feature-name>
fix/<issue-name>
docs/<documentation-name>
test/<testing-area>
refactor/<component-name>
```

Examples:

```text
feature/assessment-generation
feature/opportunities
feature/mobile-progress
fix/api-validation
docs/backend-documentation
test/dashboard-testing
refactor/authentication
```

---

# Commit Messages

Commit messages should be short, descriptive, and explain the change being introduced.

Recommended format:

```text
<description>
```

Examples:

```text
add assessment generation
```

```text
resolve login validation error
```

```text
update mobile progress screen
```

```text
fix opportunity recommendation endpoint
```

```text
add dashboard API integration
```

```text
update backend documentation
```

Commit messages should describe the actual change rather than using generic descriptions such as:

```text
changes
```

```text
updates
```

```text
final
```

---

# Committing Changes

Check the files that have been modified:

```bash
git status
```

Add the required files:

```bash
git add .
```

Create a commit:

```bash
git commit -m "add assessment generation"
```

Push the branch:

```bash
git push origin feature/assessment-generation
```

---

# Pull Request Workflow

Changes should be submitted through Pull Requests rather than being merged directly into `main` without review.

A Pull Request provides an opportunity for the team to review the implementation, identify potential issues, and verify that the change meets the required functionality.

---

## Pull Request Structure

Each Pull Request should explain the following:

### What does this PR do?

Describe the change introduced.

Example:

```text
This PR adds personalized assessment generation based on the
content selected for the user.
```

### Why is this change needed?

Explain the problem, requirement, or functionality being addressed.

Example:

```text
The feature is required to validate whether users have understood
the learning content provided through the Missions section.
```

### How was it implemented?

Summarize the technical changes made.

Example:

```text
The implementation adds an assessment generation service,
connects the service to the Gemini integration, and exposes
the functionality through the assessment API routes.
```

### How was it tested?

Mention the testing performed.

Examples:

* Tested API endpoints using Postman.
* Tested dashboard user flows using Playwright.
* Tested mobile navigation and assessment flow using Flutter.
* Tested authentication using valid and invalid credentials.
* Tested API validation with missing and invalid fields.
* Tested database operations locally.

---

# Type of Change

The Pull Request should identify the type of change being introduced.

Available categories include:

* Bug fix
* New feature
* Documentation
* Optimization
* Improvement
* Refactoring
* Testing

Example:

```text
Type of Change

[x] New feature
[ ] Bug fix
[ ] Documentation
[ ] Optimization
[ ] Improvement
[ ] Refactoring
[ ] Testing
```

---

# Code Review

Before submitting a Pull Request, developers should verify that:

* The implementation follows the existing project structure.
* Naming conventions are consistent.
* Unnecessary duplication has been avoided.
* Error handling has been implemented.
* Sensitive credentials have not been committed.
* Existing functionality has not been unnecessarily affected.
* Tests have been performed.
* Documentation has been updated where necessary.
* The application runs successfully in the local environment.

---



# Working With the Frontend

Frontend development should separate:

* User interface
* Components
* API communication
* State management
* Validation
* Business logic

API requests should use the centralized API configuration rather than hard-coded URLs throughout individual screens.

---

# Working With the Mobile Application

Flutter development should maintain separation between:

* Screens
* Widgets
* Services
* API communication
* Models
* Application state

Reusable widgets should be preferred where the same interface component appears in multiple screens.

---

# Environment and Secrets

Sensitive configuration should never be committed to GitHub.

Examples include:

```text
DATABASE_URL
GEMINI_API_KEY
SERPER_API_KEY
YOUTUBE_API_KEY
API_BASE_URL
```

Local development values should be stored in environment configuration files where appropriate.

Example:

```env
DATABASE_URL=database_url
GEMINI_API_KEY=api_key
SERPER_API_KEY=api_key
YOUTUBE_API_KEY=api_key
API_BASE_URL=backend_url
```

Environment files containing secrets should be excluded through `.gitignore`.

---

# Testing Before Pull Request

Before opening a Pull Request, developers should perform the appropriate tests for the component being modified.

## Backend

```text
API Tests
Database Tests
Authentication Tests
Validation Tests
Integration Tests
```

## Web

```text
Component Testing
API Integration Testing
User Flow Testing
Responsive Layout Testing
Authentication Testing
```

## Mobile

```text
Widget Testing
Navigation Testing
API Integration Testing
Authentication Testing
Device Testing
```

---

# Final Development Checklist

Before submitting changes:

```text
[ ] Branch created from latest main
[ ] Feature or fix implemented
[ ] Code follows existing project structure
[ ] Error handling implemented
[ ] Sensitive information protected
[ ] Local testing completed
[ ] Relevant API tests completed
[ ] Documentation updated
[ ] Changes committed
[ ] Branch pushed to GitHub
[ ] Pull Request created
[ ] Review comments addressed
[ ] Pull Request approved
[ ] Changes merged into main
```

---

# Development Standard

The Vuka development process is designed to keep the platform maintainable as the system grows.

Every contribution should prioritize:

* Maintainability
* Security
* Reusability
* Reliability
* Testability
* Consistency
* Clear documentation
* Controlled collaboration
