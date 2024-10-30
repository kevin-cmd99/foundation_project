## Test Case 3: Moon Addition

**Use Case Id:** 3

**Description:** Verify that a user can successfully add a moon to a planet.

**Actors:**
- Existing User

**Requirements:**
* Moons should be "owned" by the user that added them.
* Moons should have unique names.
* Moons should be associated with a valid planet.
* Moons longer than 30 characters are not allowed.

**Precondition:** User is logged in and on the main page.

**Steps:**
1. Click the "Add Moon" button.
2. Enter a valid moon name.
3. Enter ID of a planet from the planet list.
4. Optionally, select an image for the moon.
5. Click the "Submit" button.

**Expected Result:**
* The moon is successfully added to the planet.
* The planet's details page displays the newly added moon.
* The moon's name and image (if provided) are displayed correctly.

**Test Data:**
| Moon Name | Planet ID | Expected Result |
|---|---|---|
| Luna | 1 (Earth) | Moon addition fails due to duplicate name |
| Phobos | 2 (Mars) | Moon successfully added |
| A very long moon name that exceeds 30 characters | 1 (Earth) | Moon addition fails due to invalid name length |
| Moon#123! | 1 (Earth) | Moon successfully added |
| ExistingMoonName | 1 (Earth) | Moon addition fails due to duplicate name |
| (0 characters) | 1 (Earth) | Moon addition fails due to missing name |

**Acceptance Criteria:**
* The moon addition feature should be accessible from the planet's details page.
* The moon name should be validated for length and special characters.
* The moon should be associated with a valid planet.
* The moon should be owned by the current user.
* The moon's image should be displayed correctly if provided.
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

### Decision Table For Moon Name Validation

| Moon Name | Name Length | Contains Special Characters | Expected Result |
|---|---|---|---|
| Luna | 4 | No | Moon addition fails due to duplicate name |
| Phobos | 5 | No | Moon successfully added |
| A very long moon name that exceeds 30 characters | 31+ | No | Moon addition fails due to invalid name length |
| Moon#123! | 9 | Yes | Moon successfully added |
| Moon@ | 4 | Yes | Moon successfully added |
| (0 characters) | 0 | No | Moon addition fails due to missing name |

### Parameterized Test Scenario for Moon Addition

| Step | Actor | Data | Result |
|---|---|---|---|
| Given the user is on the planet details page of {planetId} | Existing User | URL of planet details page | |
| When the user clicks the "Add Moon" button | Existing User | | |
| When the user enters a moon name {moonName} | Existing User | {moonName} | |
| And the user clicks the "Submit" button | Existing User | | Moon is added successfully or an error message is displayed |
| Then the {expectedResult} | Existing User | | {expectedResult} |

**Example Data for Parameterized Test Scenario:**

| Test Case ID | Moon Name | Planet ID | Expected Result |
|---|---|---|---|
| TC01 | Luna | 1 | Moon addition fails due to duplicate name |
| TC02 | Phobos | 2 | Moon successfully added |
| TC03 | A very long moon name that exceeds 30 characters | 1 | Moon addition fails due to invalid name length |
| TC04 | Moon#123! | 1 | Moon successfully added |
| TC05 | Moon@ | 1 | Moon successfully added |
| TC06 | (0 characters) | 1 | Moon addition fails due to missing name |