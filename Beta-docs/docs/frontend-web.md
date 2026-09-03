#  Dashboard

<div class="page-hero">

<div class="hero-content">

<h1>VUKA Dashboard</h1>

<p class="hero-subtitle">
An overview of the user's personalized Vuka experience, activity, and progress.
</p>

</div>

</div>

---

##  Overview

The dashboard provides users with an overview of their personalized Vuka experience.

<div class="feature-grid">

<div class="feature-card">

<h3> Mission Activity</h3>

<p>
Displays information about the user's mission activity.
</p>

</div>

<div class="feature-card">

<h3> Assessment Progress</h3>

<p>
Displays information about the user's assessment progress.
</p>

</div>

<div class="feature-card">

<h3> User Progress</h3>

<p>
Provides information about the user's progress.
</p>

</div>

<div class="feature-card">

<h3> Personalized Information</h3>

<p>
Displays information based on the user's personalized Vuka experience.
</p>

</div>

</div>

---

##  Dashboard Data

Dashboard information is retrieved from the backend rather than being permanently hardcoded in the frontend.

The dashboard depends on the user's onboarding information when requesting personalized progress data.

               
                                 User
                                   │
                                   ▼
                              Onboarding Information
                                   │
                                   ▼
                                 Backend
                                   │
                                   ▼
                              Personalized Progress Data
                                   │
                                   ▼
                               Dashboard
                                   

---

#  Website Pages

The website contains several major application areas.

---

##  Dashboard

The home page acts as the user's primary dashboard.

It provides an overview of the user's current activity and progress.

<div class="feature-card">
<img src="../images/dashboard.png" alt="Vuka Home Dashboard" >

<p>
The primary location where users view their current activity and progress.
</p>

</div>

---

##  Navigation

The navigation interface allows users to move between the major sections of the application.

The navigation provides access to:

<div class="feature-grid">

<div class="feature-card">

<h3>  Home</h3>

<p>
The user's primary dashboard.
</p>

</div>

<div class="feature-card">

<h3> Missions</h3>

<p>
Access to personalized missions and content.
</p>

</div>

<div class="feature-card">

<h3>Progress</h3>

<p>
Access to user activity and completed learning activities.
</p>

</div>

<div class="feature-card">

<h3> Opportunities</h3>

<p>
Access to available opportunities.
</p>

</div>

<div class="feature-card">

<h3> Settings</h3>

<p>
Access to available account and application settings.
</p>

</div>

</div>

---

##  Login

The login page provides the authentication interface.

Users provide their credentials and complete MFA verification where required.

<div class="feature-card">
<img src="../images/login.png" alt="Vuka Home Dashboard" >



</div>

---

##  Signup

The signup page allows new users to create accounts.

Registration information is submitted to the backend registration service.

<div class="feature-card">
<img src="../images/signin.png" alt="Vuka Home Dashboard" >



</div>

---

##  Onboarding

The onboarding page collects the information required to personalize the user's Vuka experience.
<div class="feature-card">
<img src="../images/onboarding.png" alt="Vuka Home Dashboard" >



</div>

---

##  Missions

The Missions page displays AI-matched personalized content.

Users can:

* Search available content.
* Filter available content.
* Interact with available content.

Clicking a mission video automatically records the mission as completed/watched.

<div class="feature-card">
<img src="../images/missions.png" alt="Vuka Home Dashboard" >



</div>

---

##  Progress

The Progress page displays information about the user's activity and completed learning activities.

<div class="feature-card">
<img src="../images/progress.png" alt="Vuka Home Dashboard" >



</div>


---

##  Settings

The Settings page provides access to available user account and application settings.

<div class="feature-card">
<img src="../images/settings.png" alt="Vuka Home Dashboard" >



</div>


---

#  Error Handling

The website handles errors returned by the backend and other services.

Common HTTP responses include:

| **Status** | **Meaning**                        |
| ---------: | ---------------------------------- |
|    **200** | Request successful                 |
|    **201** | Resource successfully created      |
|    **400** | Invalid request                    |
|    **401** | Authentication required or invalid |
|    **403** | Access denied                      |
|    **404** | Resource not found                 |
|    **500** | Server-side error                  |

The frontend should provide understandable feedback to users rather than exposing technical backend errors directly.

---

<div class="final-callout">

<h2>VUKA Dashboard & Website</h2>

<p>
The website provides users with access to their dashboard, navigation, authentication, onboarding, missions, progress, opportunities, and settings.
</p>

</div>
