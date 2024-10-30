## Test Case 2: Planet Addition

**Use Case Id:** 2

**Description:** Verify that a user can successfully add a planet to the Planetarium.

**Actors:**
- Existing User

**Requirements:**
* Planets should be "owned" by the user that added them.
* Planets should have unique names.
* Planets longer than 30 characters are not allowed.

**Precondition:** User is logged in and on the main page.

**Steps:**
1. Click the "Add Planet" button.
2. Enter a valid planet name (e.g., "Earth").
3. Optionally, select an image for the planet.
4. Click the "Submit" button.

**Expected Result:**
* The planet is successfully added to the Planetarium.
* The user's profile page displays the newly added planet.
* The planet's name and image (if provided) are displayed correctly.

**Test Data:**
| Planet Name | Expected Result |
|---|---|
| Earth | Planet addition fails due to duplicate name |
| Fars | Planet successfully added |
| Fars! | Planet successfully added |
| A very long planet name that exceeds 30 characters | Planet addition fails due to invalid name length |
| (0 characters) | Planet addition fails due to missing name |

**Acceptance Criteria:**
* The planet addition feature should be accessible from the main page.
* The planet name should be validated for length and special characters.
* The planet should be associated with the correct user.
* The planet's image should be displayed correctly if provided.
* The user should receive appropriate error messages for invalid inputs.

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

### Decision Table For Planet Name Validation

| Planet Name | Name Length | Contains Special Characters | Expected Result |
|---|---|---|---|
| Earth | 5 | No | Planet addition fails due to duplicate name |
| Fars | 4 | No | Planet successfully added |
| Fars! | 5 | Yes | Planet successfully added |
| A very long planet name that exceeds 30 characters | 31+ | No | Planet addition fails due to invalid name length |
| (0 characters) | 0 | No | Planet addition fails due to missing name |

### Parameterized Test Scenario for Planet Addition

| Step | Actor | Data | Result |
|---|---|---|---|
| Given the user is on the planet addition page | Existing User | URL of planet addition page | |
| When the user selects planet | Existing User | | |
| When the user enters a planet name {planetName} | Existing User | {planetName} | |
| And the user clicks the "Submit" button | Existing User | | Planet is added successfully or an error message is displayed |
| Then the {expectedResult} | Existing User | | {expectedResult} |

**Example Data for Parameterized Test Scenario:**

| Test Case ID | Planet Name | Expected Result |
|---|---|---|
| TC01 | Earth | Planet addition fails due to duplicate name |
| TC02 | Mars | Planet successfully added |
| TC03 | A very long planet name that exceeds 30 characters | Planet addition fails due to invalid name length |
| TC04 | Planet#Earth! | Planet successfully added |
| TC06 | (0 characters) | Planet addition fails due to missing name |