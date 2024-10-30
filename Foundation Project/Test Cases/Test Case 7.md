## Test Case 7: User Login

**Use Case Id:** 7

**Description:** Verify that a user can successfully log in to the Planetarium using their existing account.

**Actors:**
- Existing User

**Requirements:**
* The user should be able to log in with their existing account.
* Passwords should never be visible in plaintext.
* The system should limit the number of failed login attempts.

**Precondition:** User is not logged in.

**Environment Data:**
* Browser: Chrome
* Operating System: Windows 10
* Planetarium Version: 1.2.0
* Background Data:
    - Planetarium URL: http://localhost:8080
    - Test user credentials:
        - Username: Batman
        - Password: I am the night

**Steps:**
1. Navigate to the login page.
2. Enter a valid username and password.
3. Click the "Login" button.

**Expected Result:**
* The user is successfully logged in and redirected to their home page.
* The user's Planetarium content is displayed on their main page.

**Test Data:**

### Decision Table For Username/Password Character Length Requirement Testing

| Username | Password | Login Result | Redirect |
|---|---|---|---|
| Batman | I am the night | Login successful | Redirected to home page |
| (0 characters) | I am the night | Login failed | Remains on login page |
| BatmanAndRobinToTheRescue20202 | I am the night | Login failed | Remains on login page |

### Decision Table for Unique Username Requirement Testing

| Username | Password | Login Result | Redirect |
|---|---|---|---|
| Robin | I am the night | Login failed | Remains on login page |
| Batman | I am the night | Login successful | Redirected to home page |

### Parameterized Test Scenario for User Login

| Step | Actor | Data | Result |
|---|---|---|---|
| Given the user is on the login page | Existing User | URL of login page | |
| When the user enters a username {username} | Existing User | {username} | |
| And the user enters a password {password} | Existing User | {password} | |
| And the user clicks the "Login" button | Existing User | | User is logged in successfully or an error message is displayed |
| Then the {expectedResult} | Existing User | | {expectedResult} |

**Example Data for Parameterized Test Scenario:**

| Test Case ID | Username | Password | Expected Result |
|---|---|---|---|
| TC01 | Batman | I am the night | Login successful |
| TC02 | Robin | I am the night | Login failed |
| TC03 | (0 characters) | I am the night | Login failed |
| TC04 | BatmanAndRobinToTheRescue20202 | I am the night | Login failed |