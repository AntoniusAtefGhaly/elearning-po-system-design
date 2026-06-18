# E-Learning Website - UI Flow Map

## 1. Purpose

This document shows how users move between the main MVP screens.

## 2. Student Flow

```mermaid
flowchart TD
    Home["Home Page"] --> Catalog["Course Catalog"]
    Catalog --> Details["Course Details"]
    Details --> Auth{"Logged in?"}
    Auth -- No --> Register["Register / Login"]
    Auth -- Yes --> Balance{"Enough Balance?"}
    Register --> Balance
    Balance -- No --> Redeem["Redeem Code"]
    Redeem --> Balance
    Balance -- Yes --> Enroll["Enroll in Course"]
    Enroll --> MyCourses["My Courses"]
    MyCourses --> Lesson["Lesson Player"]
    Lesson --> Quiz["Assessment/Quiz"]
    Quiz --> Progress["Progress Page"]
```

## 3. Parent Flow

```mermaid
flowchart TD
    Login["Login"] --> Dashboard["Parent Dashboard"]
    Dashboard --> Link["Link Student by Student ID"]
    Dashboard --> Redeem["Redeem Code"]
    Redeem --> SelectStudent["Select Linked Student"]
    SelectStudent --> AddBalance["Add Balance to Student"]
    Dashboard --> Progress["Student Progress View"]
```

## 4. Teacher Flow

```mermaid
flowchart TD
    Login["Login"] --> Profile["Teacher Profile"]
    Profile --> CourseList["Course List"]
    CourseList --> Editor["Course Editor"]
    Editor --> Lessons["Lesson Management"]
    Lessons --> Assessment["Assessment Management"]
    Assessment --> Submit["Submit Course for Approval"]
    Submit --> Pending["Pending Admin Approval"]
```

## 5. Admin Flow

```mermaid
flowchart TD
    Login["Login"] --> AdminDashboard["Admin Dashboard"]
    AdminDashboard --> Curriculum["Curriculum Management"]
    AdminDashboard --> TeacherApproval["Teacher Approval"]
    AdminDashboard --> CourseApproval["Course Approval"]
    AdminDashboard --> Codes["Prepaid Code Management"]
    Codes --> Generate["Generate Codes"]
    Codes --> Cancel["Cancel Code"]
    AdminDashboard --> Balance["Student Balance Management"]
    AdminDashboard --> Reports["Reports"]
```

## 6. Story Reference Notes

- Student flow mainly supports US-CM-06, US-EM-01, US-EM-03, US-CM-07, US-AM-05, and US-SM-03.
- Parent flow mainly supports US-SM-04, US-AM-07, and US-GM-07.
- Teacher flow mainly supports US-TM-01, US-CM-01 to US-CM-05, and US-AM-01 to US-AM-04.
- Admin flow mainly supports US-IM-04, US-TM-03, US-TM-04, US-CM-05, Module 08 prepaid stories to add, and Module 11 report stories to add.

## 7. Notes

- These flows are MVP-level flows.
- Detailed wireframes can be created from these flows later.
