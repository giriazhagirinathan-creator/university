# Lab 3: University Database (MongoDB)

This project demonstrates the basics of MongoDB document-oriented data modeling, data insertion, and document querying using a sample `universityDB` database.

---

## 📁 Repository Contents

| File | Description |
| :--- | :--- |
| [`university.js`](file:///c:/Users/User/OneDrive/Desktop/lab3/university.js) | Main runnable MongoDB script (handles DB selection, reset, insertion, and query display). |
| [`README.md`](file:///c:/Users/User/OneDrive/Desktop/lab3/README.md) | Project overview and execution instructions. |

---

## 🗄️ Database Schema & Data Modeling

### 1. Database
- **Name:** `universityDB`

### 2. `courses` Collection
Stores individual course information:
```json
{
  "courseId": "CS101",
  "title": "Data Structures",
  "credits": 4,
  "department": "Computer Science"
}
```

### 3. `students` Collection
Stores student profiles with embedded academic records (`enrolledCourses`):
```json
{
  "studentId": "STU001",
  "name": "Alice Smith",
  "email": "alice@university.edu",
  "major": "Computer Science",
  "enrolledCourses": [
    { "courseId": "CS101", "semester": "Fall 2026", "grade": "A" },
    { "courseId": "DB201", "semester": "Fall 2026", "grade: "A-" }
  ],
  "gpa": 3.8
}
```

---

## 🚀 How to Run

### Option 1: Run directly from the Terminal (Recommended)

Run the script directly via `mongosh`:

```bash
mongosh university.js
```

### Option 2: Interactive MongoDB Shell (`mongosh`)

1. Open `mongosh`:
   ```bash
   mongosh
   ```
2. Run the script:
   ```javascript
   load("university.js");
   ```

### Option 3: Using MongoDB Compass

1. Connect to `mongodb://localhost:27017`.
2. Open the **_MONGOSH** tab at the bottom.
3. Paste the code from [`university.js`](file:///c:/Users/User/OneDrive/Desktop/lab3/university.js) and press Enter.

---

## 🔍 Queries Included

1. **Retrieve Student Profile and Enrolled Courses:**
   ```javascript
   db.students.find({ studentId: "STU001" }).forEach(printjson);
   ```

2. **Query High-Achieving Students (GPA > 3.5) with Projection:**
   ```javascript
   db.students.find(
     { gpa: { $gt: 3.5 } },
     { name: 1, major: 1, gpa: 1, _id: 0 }
   ).forEach(printjson);
   ```
