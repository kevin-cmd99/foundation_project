## Test Case 5: Moon Deletion

**Use Case Id:** 5

**Description:** Verify that a user can successfully delete a moon from the Planetarium.

**Actors:**
- Existing User

**Requirements:**
* Only the moon's owner can delete it.
* The moon should be permanently deleted from the system.

**Precondition:** User is logged in and on the main page.

**Steps:**
1. Navigate to the planet's details page.
2. Click the "Delete Moon" button.
3. Confirm the deletion in the prompt.

**Expected Result:**
* The moon is successfully deleted from the Planetarium.
* The planet's details page no longer displays the deleted moon.

**Test Data:**
| Moon Name | Planet ID | Expected Result |
|---|---|---|
| Luna | 1 (Earth) | Moon deleted successfully |
| Phobos | 2 (Mars) | Moon deletion fails due to duplicate name |

**Acceptance Criteria:**
* The delete moon feature should be accessible from the planet's details page.
* Only the moon's owner can delete it.
* The moon should be permanently deleted from the system.
* The user should receive a confirmation prompt before deleting the moon.

**Environment Data:**
* Browser: Chrome
* Operating System: Windows 10
* Planetarium Version: 1.2.0
* Background Data:
    - Planetarium URL: http://localhost:8080
    - Test user credentials:
        - Username: batman
        - Password: I am the night

**Test Scenarios:**

### Decision Table For Moon Ownership Validation

| Moon Name | Planet Ownership | Expected Result |
|---|---|---|
| Luna | Not owned by user | Moon deletion fails |
| Phobos | Owned by user | Moon deletion fails due to duplicate name |

### Parameterized Test Scenario for Moon Deletion

| Step | Actor | Data | Result |
|---|---|---|---|
| Given the user is on the planet details page of {planetId} | Existing User | URL of planet details page | |
| When the user clicks the "Delete Moon" button | Existing User | | |
| And the user confirms the deletion | Existing User | | Moon is deleted successfully or an error message is displayed |
| Then the {expectedResult} | Existing User | | {expectedResult} |

**Example Data for Parameterized Test Scenario:**

| Test Case ID | Moon Name | Planet ID | Expected Result |
|---|---|---|---|
| TC01 | Luna | 1 | Moon deleted successfully |
| TC02 | Phobos | 2 | Moon deletion fails due to duplicate name |