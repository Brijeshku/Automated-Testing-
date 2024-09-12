# Automated-Testing- Problem Statement 1:
Write a simple test script (using a tool of your choice) to verify the integration between the frontend and backend services. ● The test should check that the frontend correctly displays the message returned by the backend.
To automate the testing of the integration between the frontend (https://www.veripark.com/) and backend (https://github.com/) services, we can use Postman to set up the required test scripts. The goal is to ensure that the frontend correctly displays a message returned by the backend.
Step 1: Set Up Postman Requests
Create a New Request for the Backend:
Method: GET
URL: https://github.com/
Save the response for later comparison.
Create a New Request for the Frontend:
Method: GET
URL: https://www.veripark.com/
Step 2: Add Test Scripts
Backend Request Test Script
In the "Tests" tab of the backend request, add the following script:
----------------------------------------------------------------
// Test to verify backend response
pm.test("Backend response is successful", function () {
    pm.response.to.have.status(200);
});

// Extract the expected message from the backend response
const expectedMessage = "Intelligent Customer Experience Suite"; // Replace with actual message
pm.environment.set("expectedMessage", expectedMessage);
________________________
Frontend Request Test Script
// Test to verify frontend response
pm.test("Frontend response is successful", function () {
    pm.response.to.have.status(200);
});

// Retrieve the expected message set from the backend request
const expectedMessage = pm.environment.get("expectedMessage");

// Check if the frontend response contains the expected message
pm.test("Frontend displays expected message", function () {
    const responseBody = pm.response.text();
    pm.expect(responseBody).to.include(expectedMessage);
});
------------------------------
Step 3: Run the Tests
Run the Backend Request first to set the expected message in the environment variable.
Run the Frontend Request next to verify that it displays the expected message.
Step 4:Run the collection:
