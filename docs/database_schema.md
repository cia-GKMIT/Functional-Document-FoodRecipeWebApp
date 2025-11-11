# Database Schema

This section documents the database schema exactly as implemented in the project’s model files.  
The database uses **MongoDB** with **Mongoose**, and all models include `{ timestamps: true }`  
to automatically add `createdAt` and `updatedAt` fields.

---

## 1. Overview

The Food Recipe Web App database consists of three main collections:

| Collection | Description |
|-------------|--------------|
| **Admin** | Manages user accounts and oversees app activity |
| **User** | Regular users who create, update, and manage recipes |
| **Recipes** | Stores recipe details and links to their creators |
<!-- 
Each collection is connected through **ObjectId references**, creating logical relationships (similar to SQL joins). -->

---

## 2. Collections and Fields

### 🧩 Admin Collection

| Field | Type | Description |
|--------|------|-------------|
| `email` | String | Unique admin email |
| `password` | String | Hashed password |
| `role` | String | References the Role collection|
| `createdAt` | Date | Added automatically by timestamps |
| `updatedAt` | Date | Added automatically by timestamps |

### Example Document

```json
{
  "_id": "673013a91234567890abcd11",
  "email": "admin@example.com",
  "password": "$2b$10$abc123hashedpassword",
  "role": "admin",
  "createdAt": "2025-11-10T09:45:00Z",
  "updatedAt": "2025-11-10T09:45:00Z"
}

```

---

## 3. Database-Diagram

```mermaid
erDiagram
 

    FAVORITE {
        ObjectId _id PK 
        ObjectId user FK "ref: USERS"
        ObjectId recipe FK "ref: RECIPES"
        Date createdAt
        Date updatedAt
        Date deletedat
    }

    USERS {
        ObjectId _id PK 
        String email "required,unique"
        String password "required"
        ObjectId role 
        Date createdAt
        Date updatedAt
        Date deletedat
    }

    RECIPES {
        ObjectId _id PK 
        String title "required"
        Array ingredients "required"
        String instructions "required"
        String time
        String coverImage
        ObjectId createdBy FK "ref: USERS"
        Date createdAt
        Date updatedAt
        Date deletedat
    }

    RECIPES }o--|| USERS : "createdBy"
    FAVORITE }o--|| USERS : "user"
    FAVORITE }o--|| RECIPES : "recipe"


```

###  Compound Index (Title + CreatedBy)

To prevent duplicate recipe titles for the same user, a **compound unique index** is added:

```js
recipeSchema.index({ title: 1, createdBy: 1 }, { unique: true });
```