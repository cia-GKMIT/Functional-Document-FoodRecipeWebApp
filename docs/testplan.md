# Test Plan

## 1. Document Details
**Project Name:** Food Recipe Management Web Application  
**Document Version:** 1.0    
**Date:** 13/11/24
**Reviewed By:** —  Rashmi

---

## 2. Objective
The objective of this test plan is to validate all functional and non-functional requirements of the Recipe Management Web Application. This includes ensuring the correctness, stability, usability, and reliability of all system features such as authentication, recipe CRUD operations, favorites, search, and PWA offline support.

---

## 3. Scope

### In Scope
- User Registration & Login  
- Authentication & Authorization (JWT)  
- Create, View, Edit, Delete Recipes  
- Favorite/Unfavorite Recipes  
- Search Recipes  
- PWA offline accessibility  
- Responsiveness and basic UI validation  
- API testing using Postman  

### Out of Scope
- Performance load testing  
- Penetration testing / security audit  
- Integration with third-party services  
- Multi-language support  

---

## 4. Test Strategy / Approach

### Manual Testing
- UI and functional flows tested manually in browser.
- Recipe CRUD, Favorites, Search, and Authentication validated using user flows.

### API Testing
- All API endpoints (e.g., `/recipes`, `/users`, `/favorites`) tested using Postman.
- Validate response codes, JSON structure, and errors.

### Unit Testing (Optional)
- Jest for backend logic.
- React Testing Library for UI components (if needed).

### Environment
- **Frontend:** Vercel  
- **Backend:** Node.js + Express  
- **Database:** MongoDB Atlas  
- **Browsers:** Chrome, Firefox, Edge  
- **Devices:** Desktop & Mobile  

---

## 5. Features to be Tested

### FR-01: User Registration
- Validate registration with valid/invalid data
- Check duplicate email handling

### FR-02: User Login
- Validate correct login
- Invalid password/email cases

### FR-03: JWT Authentication
- Access protected routes with valid token
- Ensure access denied without/invalid token

### FR-04: Create Recipe
- Add recipe with all required fields
- Upload image validation
- Missing fields error handling

### FR-05: View Recipes
- Display all recipes  
- Handle empty recipe list

### FR-06: Edit Recipe
- Only creator should edit  
- Validate updated fields

### FR-07: Delete Recipe
- Validate delete action by owner only  
- Soft delete (if applicable)

### FR-08: Favorite Recipes
- Add/remove favorite  
- Ensure no duplicate favorites

### FR-09: Search Recipes
- Search by keyword  
- No results scenario  
- Case-insensitive match

### FR-10: PWA
- App install prompt  
- Offline page accessibility  
- Asset caching validation  

---

## 6. Entry Criteria
- All required features developed  
- Backend & database running  
- Test data prepared  
- API endpoints accessible  

---

## 7. Exit Criteria
- All test cases executed  
- No critical or major bugs open  
- Regression completed  
- QA/Tester's approval  

---

## 8. Risks & Mitigation

### Risks
- Unclear requirements  
- Deployment failure  
- Inconsistent environments  
- Tight deadlines  

### Mitigation
- Frequent communication with developer/mentor  
- Maintain a stable testing environment  
- Early bug reporting  
- Daily sync updates  

---

## 9. Test Deliverables
- Test cases  
- Test execution report  
- Defect report  
- Regression report  
- Final test summary  

---
