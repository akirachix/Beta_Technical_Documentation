# QA Testing


The Vuka platform uses different testing tools for different parts of the system.
This allows each component to be tested according to the way it is used and the
type of behaviour that needs to be verified.


<div class="feature-grid">


<div class="feature-card">


<h3>API Testing</h3>


<p>
Postman is used to test the Vuka backend API endpoints. It verifies that requests
are correctly processed and that the API returns the expected responses.
</p>


</div>


<div class="feature-card">


<h3>Dashboard Testing</h3>


<p>
Playwright is used to test the Vuka dashboard from the user's perspective.
It verifies that users can navigate through the dashboard and successfully
complete supported interactions.
</p>


</div>


<div class="feature-card">


<h3>Validation Testing</h3>


<p>
Tests verify response status codes, response structures, required fields,
validation behaviour, and error handling.
</p>


</div>


</div>


---


## Testing Architecture


The testing approach separates API-level testing from user-interface testing.


<div class="flow-container">


<div class="flow-step">




<h3>API Request</h3>


<p>
A request is sent to the Vuka backend through Postman.
</p>


</div>


<div class="flow-arrow">↓</div>


<div class="flow-step">




<h3>Backend Processing</h3>


<p>
The backend processes the request and performs the required operation.
</p>


</div>


<div class="flow-arrow">↓</div>


<div class="flow-step">




<h3>Response</h3>


<p>
The backend returns a response to the client.
</p>


</div>


<div class="flow-arrow">↓</div>


<div class="flow-step">




<h3>Verification</h3>


<p>
The test verifies that the response matches the expected behaviour.
</p>


</div>


</div>


---


## API Testing with Postman


Postman is used to test the Vuka backend API endpoints.


The purpose of API testing is to verify that the backend correctly handles
requests and returns the expected responses before the functionality is
consumed by the frontend applications.


### What is Tested?


<div class="feature-grid">


<div class="feature-card">


<h3>Status Codes</h3>


<p>
Tests verify that endpoints return the appropriate HTTP status codes for
successful requests and error conditions.
</p>


</div>


<div class="feature-card">


<h3>Response Structure</h3>


<p>
Responses are checked to ensure that expected fields and data structures
are returned by the API.
</p>


</div>


<div class="feature-card">


<h3>Validation</h3>


<p>
Requests are tested with valid and invalid input to verify that the backend
handles validation correctly.
</p>


</div>


<div class="feature-card">


<h3>Error Handling</h3>


<p>
Error scenarios are tested to ensure that the API provides appropriate
responses when a request cannot be processed.
</p>


</div>


</div>


---


## Postman Testing Flow


                             Postman Request
                                  │
                                  ▼
                             Vuka API Endpoint
                                  │
                                  ▼
                             Backend Processing
                                  │
                                  ▼
                             API Response
                                  │
                                  ▼
                             Postman Test Assertions
                                   │
                                   ├── Status Code
                                   ├── Response Body
                                   ├── Required Fields
                                   ├── Validation
                                   └── Error Handling



