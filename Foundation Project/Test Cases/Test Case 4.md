## Test Case 4: Planet Deletion

**Use Case Id:** 4

**Description:** Verify that a user can successfully delete a planet from the Planetarium.

**Actors:**
- Existing User

**Requirements:**
* Only the planet's owner can delete it.
* The planet should be permanently deleted from the system.

**Precondition:** User is logged in and on the main page.

**Steps:**
1. Select a planet from the planet list.
2. Click the "Delete Planet" button.
3. Confirm the deletion in the prompt.

**Expected Result:**
* The planet is successfully deleted from the Planetarium.
* The planet no longer appears in the user's profile or the main planet list.

**Test Data:**
| Planet Name | Expected Result |
|---|---|
| Earth | Planet deleted successfully |
| Planet#Earth! | Planet deletion fails due to invalid planet name |
| (0 characters) | Planet deletion fails due to missing name |

**Acceptance Criteria:**
* The delete planet feature should be accessible from the planet's details page.
* Only the planet's owner can delete it.
* The planet should be permanently deleted from the system.
* The user should receive a confirmation prompt before deleting the planet.

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

### Decision Table For Planet Ownership Validation

| Planet Name | Planet Ownership | Expected Result |
|---|---|---|
| Earth | Not owned by user | Planet deletion fails |
| Mars | Owned by user | Planet deleted successfully |

### Parameterized Test Scenario for Planet Deletion

| Step | Actor | Data | Result |
|---|---|---|---|
| Given the user is on the planet details page of {planetName} | Existing User | URL of planet details page | |
| When the user clicks the "Delete Planet" button | Existing User | | |
| And the user confirms the deletion | Existing User | | Planet is deleted successfully or an error message is displayed |
| Then the {expectedResult} | Existing User | | {expectedResult} |

**Example Data for Parameterized Test Scenario:**

| Test Case ID | Planet Name | Expected Result |
|---|---|---|
| TC01 | Earth | Planet deletion fails due to duplicate name |
| TC02 | Mars | Planet deleted successfully |
| TC03 | Planet#Earth! | Planet deletion fails due to invalid planet name |
| TC04 | (0 characters) | Planet deletion fails due to missing name |