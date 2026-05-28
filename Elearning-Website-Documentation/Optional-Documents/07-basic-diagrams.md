# E-Learning Website - Basic Diagrams

## 1. Purpose

This document contains simple diagrams to help the software team understand the MVP.

## 2. System Context Diagram

```mermaid
flowchart LR
    Student["Student"] --> Platform["E-Learning Website"]
    Parent["Parent"] --> Platform
    Teacher["Teacher"] --> Platform
    Center["Education Center"] --> Platform
    Admin["Admin"] --> Platform
    Platform --> Video["Video Hosting"]
```

## 3. Use Case Diagram

```mermaid
flowchart TB
    Student["Student"]
    Parent["Parent"]
    Teacher["Teacher"]
    Center["Education Center"]
    Admin["Admin"]

    Browse["Browse Courses"]
    Redeem["Redeem Prepaid Code"]
    Enroll["Enroll in Course"]
    Watch["Watch Lessons"]
    Progress["View Progress"]
    CreateCourse["Create Course"]
    ApproveCourse["Approve Course"]
    GenerateCodes["Generate Codes"]
    ManageCurriculum["Manage Curriculum"]

    Student --> Browse
    Student --> Redeem
    Student --> Enroll
    Student --> Watch
    Student --> Progress

    Parent --> Redeem
    Parent --> Progress

    Teacher --> CreateCourse
    Teacher --> Progress

    Center --> CreateCourse
    Center --> Progress

    Admin --> ApproveCourse
    Admin --> GenerateCodes
    Admin --> ManageCurriculum
```

## 4. Student Course Purchase Flow

```mermaid
flowchart TD
    Start["Student opens website"] --> Browse["Browse courses"]
    Browse --> Details["View course details"]
    Details --> Login{"Logged in?"}
    Login -- No --> Register["Register / Log in"]
    Login -- Yes --> PayCheck["Check course access"]
    Register --> PayCheck
    PayCheck --> Balance{"Enough balance?"}
    Balance -- No --> Code["Redeem prepaid code"]
    Balance -- Yes --> Enroll["Enroll in course"]
    Code --> Valid{"Code valid?"}
    Valid -- No --> Error["Show error"]
    Valid -- Yes --> AddBalance["Add value to student balance"]
    AddBalance --> Enroll
    Enroll --> Watch["Watch lessons"]
    Watch --> Track["Track progress"]
```

## 5. Prepaid Code Flow

```mermaid
flowchart TD
    Admin["Admin"] --> Generate["Generate prepaid code"]
    Generate --> Active["Code status: Active"]
    User["Student or Parent"] --> Enter["Enter code"]
    Enter --> Check{"Valid active code?"}
    Check -- No --> Reject["Reject code"]
    Check -- Yes --> Redeem["Redeem code"]
    Redeem --> Used["Code status: Used"]
    Redeem --> Balance["Add value to student balance"]
    Balance --> Access["Use balance to buy course"]
```

## 6. Simple ERD

```mermaid
erDiagram
    USER ||--o| STUDENT : "may be"
    USER ||--o| PARENT : "may be"
    USER ||--o| TEACHER : "may be"
    EDUCATION_CENTER ||--o{ TEACHER : "has"
    PARENT ||--o{ STUDENT : "links to"
    TEACHER ||--o{ COURSE : "creates"
    COURSE ||--o{ LESSON : "contains"
    COURSE ||--o{ ENROLLMENT : "has"
    STUDENT ||--o{ ENROLLMENT : "enrolls"
    COURSE ||--o{ QUIZ : "has"
    STUDENT ||--o{ PROGRESS : "has"
    LESSON ||--o{ PROGRESS : "tracked by"
    PREPAID_CODE ||--o| CODE_REDEMPTION : "has"
    STUDENT ||--o{ CODE_REDEMPTION : "redeems"

    USER {
        int id
        string name
        string email
        string phone
        string role
    }

    STUDENT {
        int id
        int user_id
        string secondary_year
    }

    PARENT {
        int id
        int user_id
    }

    TEACHER {
        int id
        int user_id
        int education_center_id
        string approval_status
    }

    EDUCATION_CENTER {
        int id
        string name
        string approval_status
    }

    COURSE {
        int id
        int teacher_id
        string subject
        string term
        string chapter
        decimal price
        string approval_status
    }

    LESSON {
        int id
        int course_id
        string title
        string video_url
        int sort_order
    }

    ENROLLMENT {
        int id
        int student_id
        int course_id
        datetime enrolled_at
    }

    PREPAID_CODE {
        int id
        string code
        decimal value
        string status
    }

    CODE_REDEMPTION {
        int id
        int prepaid_code_id
        int student_id
        datetime redeemed_at
    }
```

## 7. Notes

These diagrams are basic and can be updated later when the requirements become more detailed.
