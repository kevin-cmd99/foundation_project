## Test Case 6: User Logout

**Use Case Id:** 6

**Description:** Verify that a user can successfully log out of the Planetarium.

**Actors:**
- Existing User

**Requirements:**
* The user should be able to log out from the Planetarium.
* Upon logging out, the user should be redirected to the login page.
* All Planetarium-related information should be cleared upon logout.

**Precondition:** User is logged in and on the main page.

**Steps:**
1. Click the "Logout" button.

**Expected Result:**
* The user is redirected to the login page.
* All Planetarium-related information is cleared.

**Environment Data:**
* Browser: Chrome
* Operating System: Windows 10
* Planetarium Version: 1.2.0
* Background Data:
    - Planetarium URL: http://localhost:8080
    - Test user credentials:
        - Username: Batman
        - Password: I am the night

**Test Scenarios:**

### Parameterized Test Scenario for User Logout

| Step | Actor | Data | Result |
|---|---|---|---|
| Given the user is on the main page | Existing User | URL of main page | |
| When the user clicks the "Logout" button | Existing User | | User is redirected to the login page |
| Then the user should be on the login page | Existing User | | |
| And all Planetarium information should be cleared | Existing User | | |

**Additional Test Scenarios:**

* **Test Case 1: Logout Confirmation**
  - **Description:** Verify that the system displays a confirmation prompt before logging out.
  - **Steps:**
    1. Click the "Logout" button.
    2. Cancel the logout in the prompt.
  - **Expected Result:**
    - The user remains on the main page.
    - Planetarium information is not cleared.

* **Test Case 2: Logout After Closing Browser**
  - **Description:** Verify that the user is automatically logged out when closing the browser.
  - **Steps:**
    1. Open the Planetarium in a browser.
    2. Log in.
    3. Close the browser.
  - **Expected Result:**
    - Upon reopening the browser, the user is redirected to the login page.
    - All Planetarium information is cleared.