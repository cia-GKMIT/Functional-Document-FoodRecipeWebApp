# Manual Test Cases - Food Recipe Web Application

**Project Name:** Food Recipe Management Web Application  
**Document Version:** 1.0  
**Date:** 21 November 2025
**Prepared For:** QA Testing Team  

---

## Test Case Template Legend

| Field | Description |
|-------|-------------|
| **TC ID** | Unique Test Case Identifier |
| **Module** | Feature/Module being tested |
| **Priority** | P1 (Critical), P2 (High), P3 (Medium) |
| **Type** | Functional, UI/UX, Security |
| **Preconditions** | Required state before test execution |
| **Test Steps** | Detailed step-by-step instructions |
| **Expected Result** | What should happen |
| **Actual Result** | To be filled by tester |
| **Status** | Pass / Fail / Blocked / Not Executed |

---

## Module 1: User Registration

### TC-001: Successful User Registration
- **Module:** User Registration
- **Priority:** P1
- **Type:** Functional
- **Preconditions:** 
  - Application is accessible
  - User is not logged in
  - Valid email address not already registered
- **Test Steps:**
  1. Navigate to the registration page
  3. Enter a valid email address (e.g., "test@gmail.com")
  4. Enter a valid password 
  5. Click on "Login\Sign Up" button
- **Expected Result:** 
  - User account is created successfully
  - Success message is displayed
  - User is redirected to login page
  - User data is stored in MongoDB with hashed password
- **Actual Result:** redirected to login page
- **Status:** Pass 


---

### TC-002: Registration with Duplicate Email
- **Module:** User Registration
- **Priority:** P1
- **Type:** Functional
- **Preconditions:** 
  - Application is accessible
  - A user account with email "test@example.com" already exists
- **Test Steps:**
  1. Navigate to the registration page
  2. Enter a valid name
  3. Enter email "test@gmail.com" (email already exist)
  4. Enter a valid password
  5. Click on "Sign in" button
- **Expected Result:** 
  - Error message displayed: "Email already exists" 
  - User account is not created
  - User remains on registration page
- **Actual Result:** Email already exists
- **Status:** Pass 

---

### TC-003: Registration with Missing Required Fields
- **Module:** User Registration
- **Priority:** P2
- **Type:** Functional
- **Preconditions:** 
  - Application is accessible
  - User is on registration page
- **Test Steps:**
  1. Leave email field empty
  2. Leave password field empty
  3. Click on "login/Signin" button
- **Expected Result:** 
  - Validation error messages displayed for each empty field
  - Registration form does not submit
  - User remains on registration page
- **Actual Result:** fill out this field
- **Status:**  Pass 

---

## Module 2: User Login

### TC-004: Successful User Login
- **Module:** User Login
- **Priority:** P1
- **Type:** Functional
- **Preconditions:** 
  - Application is accessible
  - A valid user account exists (email: "test@gmail.com", password: "12345")
  - User is not logged in
- **Test Steps:**
  1. Navigate to the login page
  2. Enter valid email address
  3. Enter valid password
  4. Click on "Login" button
- **Expected Result:** 
  - User is authenticated successfully
  - JWT token is generated and stored
  - User is redirected to dashboard/homepage
  - User session is established
- **Actual Result:** Same as expected
- **Status:** pass

---

### TC-005: Login with Incorrect Credentials
- **Module:** User Login
- **Priority:** P1
- **Type:** Functional
- **Preconditions:** 
  - Application is accessible
  - A valid user account exists
  - User is not logged in
- **Test Steps:**
  1. Navigate to the login page
  2. Enter valid email address
  3. Enter incorrect password
  4. Click on "Login" button
- **Expected Result:** 
  - Error message displayed: "Invalid credentials" or "Wrong password"
  - User is not authenticated
  - JWT token is not generated
  - User remains on login page
- **Actual Result:** Error message displayed: "Invalid credentials"
- **Status:** pass
---

## Module 3: Authentication & Authorization

### TC-006: Access Protected Route Without Authentication
- **Module:** Authentication & Authorization
- **Priority:** P1
- **Type:** Security
- **Preconditions:** 
  - Application is accessible
  - User is not logged in
  - No JWT token in browser storage
- **Test Steps:**
  1. Try to access a protected route (e.g., create recipe page) directly via URL
  2. Observe the application behavior
- **Expected Result:** 
  - User is redirected to login page
  - Error message: "Unauthorized" or "Please login to continue"
  - Protected content is not accessible
- **Actual Result:** Got a login/sigup pop up
- **Status:** pass

---

### TC-007: Access Protected Route with Valid JWT Token
- **Module:** Authentication & Authorization
- **Priority:** P1
- **Type:** Security
- **Preconditions:** 
  - User is logged in successfully
  - Valid JWT token exists in browser storage
- **Test Steps:**
  1. Navigate to a protected route (e.g., create recipe page)
  2. Observe the application behavior
- **Expected Result:** 
  - Protected route is accessible
  - User can view and interact with protected content
  - No redirect to login page
- **Actual Result:** Protected route accessed successfully, user can create recipes
- **Status:** pass

---

## Module 4: Recipe CRUD Operations

### TC-008: Create Recipe with All Required Fields
- **Module:** Recipe Management
- **Priority:** P1
- **Type:** Functional
- **Preconditions:** 
  - User is logged in successfully
  - User is on the create recipe page
- **Test Steps:**
  1. Enter recipe title (e.g., "Chocolate Cake")
  2. Enter ingredients (e.g., "Flour, Sugar, Cocoa Powder")
  3. Enter cooking instructions (e.g., "Mix all ingredients...")
  4. Enter cooking time (e.g., "45 minutes")
  5. Upload a recipe image (valid image file)
  6. Click on "Create Recipe" or "Save" button
- **Expected Result:** 
  - Recipe is created successfully
  - Success message is displayed
  - Recipe appears in the recipe list
  - Image is uploaded to S3 bucket
  - Recipe data is stored in MongoDB with createdById field
- **Actual Result:** Recipe created successfully, success message displayed, recipe appears in list with image
- **Status:** pass

---

### TC-009: Create Recipe with Missing Required Fields
- **Module:** Recipe Management
- **Priority:** P2
- **Type:** Functional
- **Preconditions:** 
  - User is logged in successfully
  - User is on the create recipe page
- **Test Steps:**
  1. Leave title field empty
  2. Enter other required fields
  3. Click on "Create Recipe" button
- **Expected Result:** 
  - Validation error message displayed for missing title
  - Recipe is not created
  - User remains on create recipe page
- **Actual Result:** Validation error "Title is required" displayed, recipe not created
- **Status:** pass

---

### TC-010: View All Recipes (Guest User)
- **Module:** Recipe Management
- **Priority:** P1
- **Type:** Functional
- **Preconditions:** 
  - Application is accessible
  - At least one recipe exists in the database
  - User is not logged in (Guest user)
- **Test Steps:**
  1. Navigate to the recipes listing page
  2. Observe the displayed recipes
- **Expected Result:** 
  - All available recipes are displayed
  - Each recipe shows: title, image, author name
  - Recipes are displayed in a list or grid format
  - Guest user can view recipes but cannot edit/delete
- **Actual Result:** All recipes displayed with title, image, and author. Edit/delete buttons not visible for guest user
- **Status:** pass

---

### TC-011: View Recipe Details
- **Module:** Recipe Management
- **Priority:** P1
- **Type:** Functional
- **Preconditions:** 
  - Application is accessible
  - At least one recipe exists in the database
- **Test Steps:**
  1. Navigate to the recipes listing page
  2. Click on a recipe card or "View Details" button
- **Expected Result:** 
  - Recipe details page is displayed
  - Full recipe information is shown: title, image, ingredients, instructions, cooking time, author
  - Recipe details are accurate and complete
- **Actual Result:** Recipe details page displayed with all information: title, image, ingredients, instructions, time, and author
- **Status:** pass

---

### TC-012: Edit Own Recipe (Authorized User)
- **Module:** Recipe Management
- **Priority:** P1
- **Type:** Functional
- **Preconditions:** 
  - User is logged in successfully
  - User has created at least one recipe
  - User is viewing their own recipe
- **Test Steps:**
  1. Navigate to a recipe created by the logged-in user
  2. Click on "Edit" button
  3. Modify recipe title (e.g., change "Chocolate Cake" to "Chocolate Cake Deluxe")
  4. Update ingredients or instructions
  5. Click on "Save" or "Update" button
- **Expected Result:** 
  - Recipe is updated successfully
  - Success message is displayed
  - Updated recipe information is reflected in the recipe list and details page
  - Changes are saved in MongoDB
- **Actual Result:** Recipe updated successfully, success message shown, changes reflected in recipe list and details page
- **Status:** pass

---

### TC-013: Edit Recipe as Non-Owner (Unauthorized User)
- **Module:** Recipe Management
- **Priority:** P1
- **Type:** Security
- **Preconditions:** 
  - User A is logged in successfully
  - User B has created a recipe
  - User A is viewing User B's recipe
- **Test Steps:**
  1. Navigate to a recipe created by another user
  2. Try to access edit functionality (via URL or button)
  3. Observe the application behavior
- **Expected Result:** 
  - Edit button is not visible OR
  - Error message: "403 Forbidden" or "You are not authorized to edit this recipe"
  - Recipe is not editable
  - User cannot modify the recipe
- **Actual Result:** Edit button not visible for non-owner recipes, access denied when trying to edit via URL
- **Status:** pass

---

### TC-014: Delete Own Recipe (Authorized User)
- **Module:** Recipe Management
- **Priority:** P1
- **Type:** Functional
- **Preconditions:** 
  - User is logged in successfully
  - User has created at least one recipe
  - User is viewing their own recipe
- **Test Steps:**
  1. Navigate to a recipe created by the logged-in user
  2. Click on "Delete" button
  3. Confirm deletion in the confirmation dialog
- **Expected Result:** 
  - Confirmation dialog is displayed
  - Recipe is deleted successfully after confirmation
  - Success message is displayed
  - Recipe is removed from the recipe list
  - Recipe is soft-deleted in MongoDB (deletedAt field set)
- **Actual Result:** Confirmation dialog displayed, recipe deleted after confirmation, success message shown, recipe removed from list
- **Status:** pass

---

### TC-015: Delete Recipe as Non-Owner (Unauthorized User)
- **Module:** Recipe Management
- **Priority:** P1
- **Type:** Security
- **Preconditions:** 
  - User A is logged in successfully
  - User B has created a recipe
  - User A is viewing User B's recipe
- **Test Steps:**
  1. Navigate to a recipe created by another user
  2. Try to access delete functionality (via URL or button)
  3. Observe the application behavior
- **Expected Result:** 
  - Delete button is not visible OR
  - Error message: "403 Forbidden" or "You are not authorized to delete this recipe"
  - Recipe is not deletable
  - User cannot delete the recipe
- **Actual Result:** Delete button not visible for non-owner recipes, access denied when trying to delete via URL
- **Status:** pass

---

## Module 5: Favorite Recipes

### TC-016: Add Recipe to Favorites
- **Module:** Favorite Recipes
- **Priority:** P2
- **Type:** Functional
- **Preconditions:** 
  - User is logged in successfully
  - At least one recipe exists in the database
  - User is viewing a recipe
- **Test Steps:**
  1. Navigate to a recipe details page
  2. Click on "Add to Favorites" or heart icon
  3. Navigate to the Favorites page
- **Expected Result:** 
  - Recipe is marked as favorite
  - Favorite icon changes state (e.g., filled heart)
  - Recipe appears in the Favorites list
  - Favorite status is stored in browser localStorage
- **Actual Result:** Recipe marked as favorite, heart icon filled, recipe appears in Favorites list
- **Status:** pass

---

### TC-017: Remove Recipe from Favorites
- **Module:** Favorite Recipes
- **Priority:** P2
- **Type:** Functional
- **Preconditions:** 
  - User is logged in successfully
  - User has at least one recipe marked as favorite
  - User is viewing a favorited recipe
- **Test Steps:**
  1. Navigate to a recipe that is already in favorites
  2. Click on "Remove from Favorites" or heart icon
  3. Navigate to the Favorites page
- **Expected Result:** 
  - Recipe is removed from favorites
  - Favorite icon changes state (e.g., empty heart)
  - Recipe no longer appears in the Favorites list
  - Favorite status is updated in browser localStorage
- **Actual Result:** Recipe removed from favorites, heart icon empty, recipe no longer in Favorites list
- **Status:** pass

---

### TC-018: View Favorites Page
- **Module:** Favorite Recipes
- **Priority:** P2
- **Type:** Functional
- **Preconditions:** 
  - User is logged in successfully
  - User has at least one recipe marked as favorite
- **Test Steps:**
  1. Navigate to the Favorites page
  2. Observe the displayed recipes
- **Expected Result:** 
  - Only favorited recipes are displayed
  - Favorites list shows: title, image, ingredients, time
  - All favorited recipes are visible
  - Non-favorited recipes are not shown
- **Actual Result:** Only favorited recipes displayed with title, image, ingredients, and time. Non-favorited recipes not shown
- **Status:** pass

---

## Module 6: Search Functionality

### TC-019: Search Recipe by Title (Exact Match)
- **Module:** Search
- **Priority:** P1
- **Type:** Functional
- **Preconditions:** 
  - Application is accessible
  - At least one recipe exists with title "Chocolate Cake"
- **Test Steps:**
  1. Navigate to the search page or use search bar
  2. Enter search keyword: "Chocolate Cake"
  3. Click on "Search" button or press Enter
- **Expected Result:** 
  - Search results page displays recipes matching "Chocolate Cake"
  - Matching recipe(s) are shown with: title, image, ingredients, time
  - Exact match recipe appears in results
- **Actual Result:** Search results displayed with matching "Chocolate Cake" recipe showing title, image, ingredients, and time
- **Status:** pass

---

### TC-020: Search Recipe by Partial Title
- **Module:** Search
- **Priority:** P2
- **Type:** Functional
- **Preconditions:** 
  - Application is accessible
  - At least one recipe exists with title containing "Chocolate"
- **Test Steps:**
  1. Navigate to the search page or use search bar
  2. Enter search keyword: "Choco"
  3. Click on "Search" button or press Enter
- **Expected Result:** 
  - Search results page displays all recipes containing "Chocolate" in the title
  - Matching recipes are shown with: title, image, ingredients, time
  - Partial matches are included in results
- **Actual Result:** Search results displayed with all recipes containing "Chocolate" in title, showing title, image, ingredients, and time
- **Status:** pass

---

### TC-021: Search with No Matching Results
- **Module:** Search
- **Priority:** P2
- **Type:** Functional
- **Preconditions:** 
  - Application is accessible
  - No recipe exists with title "NonExistentRecipe123"
- **Test Steps:**
  1. Navigate to the search page or use search bar
  2. Enter search keyword: "NonExistentRecipe123"
  3. Click on "Search" button or press Enter
- **Expected Result:** 
  - Message displayed: "No recipes found" or "No matching results"
  - Empty state is shown
  - User-friendly message is displayed
- **Actual Result:** Empty state is shown
- **Status:** pass

---

## Module 7: Progressive Web App (PWA)

### TC-022: PWA Offline Access - View Cached Pages
- **Module:** PWA
- **Priority:** P2
- **Type:** Functional
- **Preconditions:** 
  - Application is installed as PWA
  - User has visited homepage and recipe listing page while online
  - Service worker has cached assets
- **Test Steps:**
  1. Disable internet connection (airplane mode or disconnect WiFi)
  2. Open the PWA application
  3. Navigate to previously visited pages (homepage, recipe list)
- **Expected Result:** 
  - Cached pages are accessible offline
  - Previously loaded recipes are displayed from cache
  - Application works without internet connection
  - Offline indicator may be shown
- **Actual Result:** Cached pages accessible offline, previously loaded recipes displayed from cache, offline indicator shown
- **Status:** pass

---

## Module 8: UI/UX Testing

### TC-023: Responsive Design - Mobile View
- **Module:** UI/UX
- **Priority:** P2
- **Type:** UI/UX
- **Preconditions:** 
  - Application is accessible
  - Browser developer tools available
- **Test Steps:**
  1. Open application in browser
  2. Open developer tools (F12)
  3. Switch to mobile view (responsive design mode)
  4. Select a mobile device (e.g., iPhone 12, Samsung Galaxy)
  5. Navigate through different pages (home, recipes, create recipe)
- **Expected Result:** 
  - Application layout adapts to mobile screen size
  - All elements are visible and accessible
  - Navigation menu works properly (hamburger menu if applicable)
  - Text is readable without zooming
  - Buttons and links are easily tappable
- **Actual Result:** Layout adapts perfectly till specific resolution but on mobiles doesn't that much
- **Status:** Fail

---

### TC-024: Image Upload - Valid Image Format
- **Module:** Recipe Management
- **Priority:** P2
- **Type:** Functional
- **Preconditions:** 
  - User is logged in successfully
  - User is on the create recipe page
- **Test Steps:**
  1. Click on "Choose File" or image upload button
  2. Select a valid image file (JPG, PNG, or other supported format)
  3. Observe image preview (if available)
  4. Complete recipe creation
- **Expected Result:** 
  - Image file is selected successfully
  - Image preview is displayed (if feature exists)
  - Image uploads successfully to S3 bucket
  - Image is displayed in recipe details
- **Actual Result:** Image file selected successfully, preview displayed, image uploaded to S3, image displayed in recipe details
- **Status:** pass

---

## Module 9: Security Testing

### TC-025: Password Security - Password Hashing
- **Module:** Security
- **Priority:** P1
- **Type:** Security
- **Preconditions:** 
  - Database access available (for verification)
  - User registration functionality works
- **Test Steps:**
  1. Register a new user with password "12345"
  2. Check the database to view stored password
- **Expected Result:** 
  - Password is stored as hashed value (bcrypt hash)
  - Plain text password is not visible in database
  - Password hash starts with "$2b$" or similar bcrypt identifier
- **Actual Result:** Password stored as bcrypt hash starting with "$2b$", plain text password not visible in database
- **Status:** pass

---

## Test Execution Summary

### Test Execution Log

| TC ID | Module | Priority | Status | 
|-------|--------|----------|--------|
| TC-001 | User Registration | P1 | Pass | 
| TC-002 | User Registration | P1 | Pass | 
| TC-003 | User Registration | P2 | Pass |
| TC-004 | User Login | P1 | Pass | 
| TC-005 | User Login | P1 | Pass | 
| TC-006 | Authentication | P1 | Pass | 
| TC-007 | Authentication | P1 | Pass |  
| TC-008 | Recipe CRUD | P1 | Pass | 
| TC-009 | Recipe CRUD | P2 | Pass | 
| TC-010 | Recipe CRUD | P1 | Pass | 
| TC-011 | Recipe CRUD | P1 | Pass | 
| TC-012 | Recipe CRUD | P1 | Pass | 
| TC-013 | Recipe CRUD | P1 | Pass | 
| TC-014 | Recipe CRUD | P1 | Pass | 
| TC-015 | Recipe CRUD | P1 | Pass | 
| TC-016 | Favorites | P2 | Pass | 
| TC-017 | Favorites | P2 | Pass | 
| TC-018 | Favorites | P2 | Pass | 
| TC-019 | Search | P1 | Pass | 
| TC-020 | Search | P2 | Pass | 
| TC-021 | Search | P2 | Pass | 
| TC-022 | PWA | P2 | Pass | 
| TC-023 | UI/UX | P2 | Fail | 
| TC-024 | Recipe Management | P2 | Pass | 
| TC-025 | Security | P1 | Pass | 

---

## Test Environment Details

- **Application URL:** https://food-recipe-webapp-frontend.vercel.app
- **Browser:** Chrome / Safari 
- **Operating System:** macOS / Mobile
- **Device:** Desktop / Mobile
- **Network:** WiFi / Mobile Data / Offline

---

**End of Test Case Document**
