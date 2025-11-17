# Test Plan

## 1. Document Details
**Project Name:** Food Recipe Management Web Application  
**Document Version:** 1.1  
**Date:** 17/11/24  
**Reviewed By:** Rashmi  

---

## 2. Objective
The objective of this test plan is to validate all functional and non-functional requirements of the Recipe Management Web Application. The goal is to ensure correctness, reliability, usability, security, and stability across all modules including authentication, recipe CRUD, search, favorites, and PWA offline features.

---

## 3. Scope

### 3.1 In Scope
- User Registration & Login  
- Authentication & Authorization (JWT)  
- Recipe CRUD (Create, View, Edit, Delete)  
- Add/Remove Favorites  
- Search functionality  
- PWA offline support  
- UI Responsiveness  
- API testing using Postman  
- Basic error-handling validation  

### 3.2 Functional Items Present in the Project but Out of Scope

- Soft delete internal behavior in MongoDB (only UI delete flow will be tested)  
- Advanced form validations (max image size, password strength, special character rules)  
- Deep PWA caching, cache versioning, background sync  
- Detailed JWT token scenarios (expiry, token refresh, tampered token handling)  
- Full responsiveness testing on all screen sizes (only basic mobile & desktop covered)  
- Image upload edge cases (large file sizes, unsupported formats, high-resolution images)  
- Search accuracy, relevancy scoring, and fuzzy search behavior  


---

## 4. Test Strategy / Approach

### 4.1 Manual Testing
Manual functional testing will be performed on UI screens, validating workflow, usability, and response accuracy.

#### Manual Testing Scenarios & Expected Results

| **Scenario** | **Expected Result** |
|--------------|----------------------|
| Register with valid details | User account created successfully |
| Register with an existing email | Duplicate email error displayed |
| Login with correct credentials | User redirected to dashboard |
| Login with incorrect credentials | Error message shown |
| Create recipe with all required fields | Recipe successfully created |
| Create recipe with missing fields | Validation error shown |
| Edit recipe as owner | Recipe updated successfully |
| Edit recipe as non-owner | Access denied |
| Delete recipe as owner | Recipe removed |
| Add recipe to favorites | Recipe added to favorites list |
| Remove recipe from favorites | Recipe removed from favorites |
| Search by keyword | Matching recipes displayed |
| Search with no match | “No recipes found” message |
| PWA offline mode | Cached pages accessible offline |

---

### 4.2 API Testing (Postman & Thunder Client)
All backend endpoints will be validated for status codes, response bodies, error handling, and authentication behavior.

#### API Test Cases (Elaborated)

##### Users API
| **API** | **Description** | **Expected Result** |
|---------|------------------|----------------------|
| POST `/users/register` | Register a new user | 201 Created |
| POST `/users/login` | Authenticate user | 200 OK + JWT |
| POST `/users/login` (invalid) | Wrong password/email | 401 Unauthorized |

##### Recipes API
| **API** | **Description** | **Expected Result** |
|---------|------------------|----------------------|
| GET `/recipes` | Fetch all recipes | 200 OK + list |
| POST `/recipes` | Create recipe | 201 Created |
| PUT `/recipes/:id` | Update recipe | 200 OK |
| DELETE `/recipes/:id` | Delete recipe | 200 OK |

##### Favorites API
| **API** | **Description** | **Expected Result** |
|---------|------------------|----------------------|
| POST `/favorites/:id` | Add recipe to favorites | 200 OK |
| DELETE `/favorites/:id` | Remove favorite | 200 OK |

##### Search API
| **API** | **Expected Result** |
|---------|----------------------|
| GET `/recipes?search=keyword` | 200 OK + filtered results |

---

## 5. Features to Be Tested

### 5.1 Functional Requirements
- FR-01 User Registration  
- FR-02 User Login  
- FR-03 JWT Authentication  
- FR-04 Create Recipe  
- FR-05 View Recipes  
- FR-06 Edit Recipe  
- FR-07 Delete Recipe  
- FR-08 Favorite Recipes  
- FR-09 Search Recipes  
- FR-10 PWA Offline Support  

---

## 6. Entry Criteria
- Features developed & unit tested  
- API server running  
- Test data available  
- Stable test environment  

---

## 7. Exit Criteria
- All test cases executed  
- No critical/major defects open  
- Regression completed  
- QA approval received  

---

## 8. Risks & Mitigation

### 8.1 Risks
- Requirement changes  
- Deployment issues  
- Data inconsistency  
- Environment instability  

### 8.2 Mitigation
- Regular communication with developer  
- Early defect reporting  
- Stable test environment  
- Daily status sync  

---

## 9. Test Deliverables
- Test Case Document  
- Test Execution Report  
- Defect Report  
- Regression Summary  
- Final Test Summary Report  

---
