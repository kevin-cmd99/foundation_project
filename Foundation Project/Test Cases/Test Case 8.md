## Test Case 8: Planetarium Display

**Use Case Id:** 8

**Description:** Verify that a user can successfully view planets and moons in the Planetarium.

**Actors:**
- Existing User

**Requirements:**
* Planets should display unique names.
* Associated planets and moons should display images.
* Planets should display any associated moons with corresponding images.
* The user's celestial bodies should be displayed in their Planetarium if associated with their ID.
* All UI elements should be loaded correctly.

**Precondition:** User is logged in and on the main page.

**Steps:**
1. Navigate to the main page.

**Expected Result:**
* The user's celestial bodies are displayed in the Planetarium table.
* Planets and moons display unique names.
* Planets and moons display associated images.
* All UI elements are loaded correctly.

**Test Data:**
| Planet Name | Expected Result |
|---|---|
| Earth | Planet displayed with moon Luna |
| Mars | Planet displayed with moon Phobos |
| Planet#Earth! | Planet not displayed |

**Acceptance Criteria:**
* Planets and moons should be displayed in the Planetarium table.
* Planets and moons should display unique names.
* Planets and moons should display associated images.
* All UI elements should be loaded correctly.

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

### Parameterized Test Scenario for Planetarium Display

| Step | Actor | Data | Result |
|---|---|---|---|
| Given the user is on the main page | Existing User | URL of main page | |
| Then the user's celestial bodies should be displayed in the Planetarium table | Existing User | | Celestial bodies displayed |
| And planets and moons should display unique names | Existing User | | Unique names displayed |
| And planets and moons should display associated images | Existing User | | Images displayed |
| And all UI elements should be loaded correctly | Existing User | | UI elements loaded |

**Example Data for Parameterized Test Scenario:**

| Test Case ID | Planet Name | Expected Result |
|---|---|---|
| TC01 | Earth | Planet displayed with moon Luna |
| TC02 | Mars | Planet displayed with moon Phobos |
| TC03 | Planet#Earth! | Planet not displayed |