````md
# Strapi Content Architecture

## 1. Overview

Nevyrion Learning uses **Strapi** as the backend platform responsible for content management, API generation, administrative operations, and communication with the database.

The React frontend communicates with Strapi through APIs and does not communicate directly with the database.

This document defines how the entities and relationships identified during the system design phase are represented as **Strapi Content Types and Relations**.

The purpose of this document is to provide a clear mapping between the system's conceptual data model and its implementation within Strapi.

---

## 2. Architecture Context

The platform follows a separated frontend and backend architecture:

```text
┌──────────────────────────┐
│     React Frontend       │
│      Learner UI          │
└────────────┬─────────────┘
             │
             │ API Requests / Responses
             │
             ▼
┌──────────────────────────┐
│          Strapi          │
│                          │
│  • Backend API           │
│  • Content Management    │
│  • Admin Dashboard       │
│  • Authentication        │
└────────────┬─────────────┘
             │
             │ Database Access
             ▼
┌──────────────────────────┐
│        Database          │
│     Persistent Data      │
└──────────────────────────┘
```
````

### Responsibilities

#### React Frontend

The React application is responsible for the learner-facing experience, including:

- Course discovery
- Course details
- Course enrollment
- Learning experience
- Lesson progress
- Quizzes
- Certificates
- Learning paths
- Reviews
- Favorites
- Notifications
- User profile

React communicates with Strapi through API requests and receives API responses.

React does not access the database directly.

#### Strapi

Strapi is responsible for:

- Backend API
- Content management
- Authentication and user management
- Content Types
- Relations between entities
- Course management
- Learning path management
- Quiz management
- Administrative course approval
- Database access
- Automatic API generation

#### Database

The database is responsible for persistent storage of platform data.

The database is accessed through Strapi and is not directly exposed to the React frontend.

---

# 3. Content Architecture Principles

The Strapi content architecture follows these principles:

### 3.1 Separation of Responsibilities

Each part of the system has a clear responsibility.

- React handles the user interface.
- Strapi handles backend operations and content management.
- The database stores persistent data.

### 3.2 API-Based Communication

The frontend communicates with Strapi through APIs.

```text
React
  ↓
API Request
  ↓
Strapi
  ↓
Database
  ↓
Strapi
  ↓
API Response
  ↓
React
```

### 3.3 Reuse of the Existing Data Model

The Strapi architecture is based on the previously approved database design and ERD.

No unnecessary entities should be introduced during implementation.

### 3.4 MVP-Focused Architecture

Only entities required by the Academic MVP are included.

Future features should not be implemented unless they are explicitly moved into the MVP scope.

---

# 4. Content Types

The following Content Types represent the main entities of the Nevyrion Learning platform.

---

## 4.1 Core Content Types

These Content Types represent the core learning platform structure.

### User

Represents a registered platform user.

Strapi's built-in user and authentication system will be used rather than implementing authentication from scratch.

Users may interact with the platform as:

- Student
- Instructor

Administrative users are managed through Strapi's administrative system.

Users may be related to:

- Courses
- Enrollments
- Lesson Progress
- Reviews
- Certificates
- Favorites
- Quiz Attempts
- Challenge Submissions
- Learning Path Enrollments
- Notifications

---

### Category

Represents a course category.

A category may contain multiple courses.

Relationship:

```text
Category
   │
   └── 1 : N
          │
          ▼
       Courses
```

---

### Course

Represents a complete educational course.

The Course is one of the central Content Types in the platform.

A course is associated with:

- Category
- Instructor
- Sections
- Requirements
- Learning Outcomes
- Completion Rules
- Quizzes
- Enrollments
- Reviews
- Certificates
- Favorites
- Module Challenges

Course publication is controlled through a defined approval workflow.

---

### Section

Represents a section within a course.

A course may contain multiple sections.

Relationship:

```text
Course
   │
   └── 1 : N
          │
          ▼
       Sections
```

A section may contain:

- Lessons
- Module Challenges

---

### Lesson

Represents an individual learning unit inside a section.

Relationship:

```text
Section
   │
   └── 1 : N
          │
          ▼
       Lessons
```

A lesson may have:

- Lesson Resources
- Lesson Progress records

---

### Lesson Resource

Represents an additional resource associated with a lesson.

Examples may include:

- Documents
- External resources
- Supporting materials

Relationship:

```text
Lesson
   │
   └── 1 : N
          │
          ▼
    Lesson Resources
```

---

# 5. Assessment Content Types

These Content Types represent quizzes and quiz attempts.

---

## 5.1 Quiz

Represents an assessment associated with learning content.

A quiz may contain multiple questions.

Relationship:

```text
Quiz
   │
   └── 1 : N
          │
          ▼
      Questions
```

---

## 5.2 Question

Represents a question within a quiz.

A question may contain multiple answer options.

Relationship:

```text
Question
   │
   └── 1 : N
          │
          ▼
   Question Options
```

---

## 5.3 Question Option

Represents one possible answer to a question.

Question options belong to a specific question.

---

## 5.4 Quiz Attempt

Represents one attempt made by a user to complete a quiz.

A user may have multiple quiz attempts.

Relationship:

```text
User
  │
  └── 1 : N
         │
         ▼
   Quiz Attempts
```

A quiz attempt is associated with:

- User
- Quiz
- Quiz Attempt Answers

---

## 5.5 Quiz Attempt Answer

Represents an answer submitted by a user during a quiz attempt.

Relationship:

```text
Quiz Attempt
     │
     └── 1 : N
            │
            ▼
    Attempt Answers
```

Each answer belongs to a specific quiz attempt and references the selected question option where applicable.

---

# 6. Learning and Progress Content Types

These Content Types represent the learner's interaction with courses and learning content.

---

## 6.1 Enrollment

Represents a user's enrollment in a course.

Users and courses have a many-to-many relationship that is represented through Enrollment.

```text
User
 │
 ├──── Enrollment ──── Course
 │
 └──── Enrollment ──── Course
```

An enrollment may contain information such as:

- Enrollment status
- Enrollment date
- Completion state

---

## 6.2 Lesson Progress

Represents the progress of a user within a specific lesson.

Users and lessons have a many-to-many relationship represented through Lesson Progress.

```text
User
 │
 └──── Lesson Progress ──── Lesson
```

Lesson Progress is used to track whether a learner has completed specific lessons.

---

## 6.3 Certificate

Represents a certificate issued to a user after completing a course.

A certificate is associated with:

- User
- Course

Certificate data may also contain historical snapshot information such as:

- Student name
- Course name
- Instructor name

These snapshot values preserve the information as it existed when the certificate was issued.

---

## 6.4 Review

Represents a user's review of a course.

Users and courses have a many-to-many relationship represented through Review.

```text
User
 │
 └──── Review ──── Course
```

Business rules determine who is allowed to submit a review.

---

## 6.5 Favorite

Represents a course saved by a user.

Users and courses have a many-to-many relationship represented through Favorite.

```text
User
 │
 └──── Favorite ──── Course
```

Favorites allow learners to save courses for later access.

---

# 7. Course Structure Content Types

These Content Types store additional information that defines the educational structure of a course.

---

## 7.1 Course Requirement

Represents knowledge or prerequisites recommended or required before starting a course.

Examples:

- Previous knowledge
- Required concepts
- Prerequisite courses

Requirements describe what the learner should know before taking the course.

They are different from Course Completion Rules.

---

## 7.2 Course Learning Outcome

Represents a learning outcome that the learner should achieve after completing the course.

A course may contain multiple learning outcomes.

```text
Course
   │
   └── 1 : N
          │
          ▼
   Learning Outcomes
```

---

## 7.3 Course Completion Rule

Defines the conditions required for a learner to complete a course.

This is conceptually different from Course Requirements.

### Course Requirement

Answers:

> What should the learner know before starting?

### Course Completion Rule

Answers:

> What must the learner complete before the course is considered completed?

The Completion Rule is modeled as a one-to-one relationship with a Course.

```text
Course
   │
   └── 1 : 1
          │
          ▼
   Completion Rule
```

---

# 8. Learning Path Content Types

Learning Paths provide a structured sequence of courses.

---

## 8.1 Learning Path

Represents a structured educational path containing multiple steps.

A Learning Path contains multiple Learning Path Steps.

```text
Learning Path
      │
      └── 1 : N
             │
             ▼
       Learning Path Steps
```

---

## 8.2 Learning Path Step

Represents one step within a learning path.

A step determines the position and structure of courses inside the learning path.

---

## 8.3 Learning Path Step Course

Represents the relationship between a Learning Path Step and its courses.

This allows a step to contain one or more courses where required by the platform structure.

```text
Learning Path
      │
      ▼
    Steps
      │
      ▼
 Step Courses
      │
      ▼
   Courses
```

---

## 8.4 Learning Path Enrollment

Represents a user's enrollment in a learning path.

Users and learning paths have a many-to-many relationship represented through Learning Path Enrollment.

```text
User
 │
 └──── Learning Path Enrollment ──── Learning Path
```

The enrollment may track the learner's current step.

---

# 9. Challenge Content Types

Challenges provide optional practical activities associated with learning modules.

---

## 9.1 Module Challenge

Represents a practical challenge associated with a course section.

Relationship:

```text
Section
   │
   └── 1 : N
          │
          ▼
   Module Challenges
```

A challenge may receive submissions from users.

---

## 9.2 Challenge Submission

Represents a learner's submission for a module challenge.

Relationship:

```text
Module Challenge
       │
       └── 1 : N
              │
              ▼
      Challenge Submissions
```

Each submission is associated with the user who submitted it.

```text
User
 │
 └── 1 : N
        │
        ▼
Challenge Submissions
```

---

# 10. Notification Content Type

## Notification

Represents a notification delivered to a user.

Each notification belongs to a specific user.

```text
User
 │
 └── 1 : N
        │
        ▼
   Notifications
```

Notifications may be generated for important platform events such as:

- Course approval
- Course rejection
- Enrollment-related events
- Learning progress events
- Certificate availability

The exact notification events are controlled by the platform's business rules and feature scope.

---

# 11. Main Relationships Overview

The main relationships between Content Types can be summarized as follows:

```text
Category
   │
   └── Courses

User
   │
   ├── Courses
   ├── Enrollments
   ├── Reviews
   ├── Favorites
   ├── Lesson Progress
   ├── Certificates
   ├── Quiz Attempts
   ├── Learning Path Enrollments
   ├── Challenge Submissions
   └── Notifications

Course
   │
   ├── Category
   ├── Instructor
   ├── Sections
   ├── Requirements
   ├── Learning Outcomes
   ├── Completion Rule
   ├── Quizzes
   ├── Enrollments
   ├── Reviews
   ├── Favorites
   └── Certificates

Section
   │
   ├── Lessons
   └── Module Challenges

Lesson
   │
   ├── Lesson Resources
   └── Lesson Progress

Quiz
   │
   └── Questions
          │
          └── Question Options

Quiz Attempt
   │
   └── Quiz Attempt Answers

Learning Path
   │
   └── Learning Path Steps
          │
          └── Step Courses

Module Challenge
   │
   └── Challenge Submissions
```

---

# 12. User Management

Nevyrion Learning will use Strapi's built-in user and authentication capabilities.

The system does not require a custom authentication backend for the MVP.

The main application-level user roles are:

- Guest
- Student
- Instructor

### Guest

A guest is an unauthenticated visitor.

Guests can:

- Browse public content
- Explore courses
- View available course information

Guests cannot:

- Enroll in courses
- Access protected learning content
- Submit reviews
- Access student-specific functionality

### Student

A Student is an authenticated learner.

Students can:

- Enroll in courses
- Access enrolled courses
- Track learning progress
- Complete lessons
- Take quizzes
- Receive certificates
- Review courses
- Save courses
- Enroll in learning paths
- Submit challenges
- Receive notifications
- Manage their profile

### Instructor

An Instructor is an authenticated user who can create and manage courses.

Instructors can:

- Create courses
- Manage course content
- Manage sections and lessons
- Submit courses for review
- Manage their own course content

Course publication remains subject to administrative approval.

### Admin

Administrative management is handled through the Strapi Admin Panel.

The Admin is responsible for administrative operations such as:

- Reviewing submitted courses
- Approving courses
- Rejecting courses
- Managing platform content

The Admin Dashboard is not implemented as a separate React dashboard in the Academic MVP.

---

# 13. Course Lifecycle

Courses follow an approval-based lifecycle.

```text
Draft
  │
  ▼
Submitted
  │
  ▼
Under Review
  │
  ├───────────────┐
  │               │
  ▼               ▼
Approved        Rejected
  │
  ▼
Published
```

### Draft

The instructor is creating or editing the course.

### Submitted

The instructor has submitted the course for administrative review.

### Under Review

The course is being reviewed by an administrator.

### Approved

The course has passed administrative review.

### Rejected

The course was rejected and may require changes before resubmission.

### Published

The course is available to learners according to the platform's publication rules.

---

# 14. Administrative Approval Workflow

The approval workflow is implemented using Strapi's administrative capabilities.

The intended flow is:

```text
Instructor
    │
    ▼
Create Course
    │
    ▼
Complete Course Content
    │
    ▼
Submit Course
    │
    ▼
Admin Review
    │
    ├── Reject
    │      │
    │      ▼
    │   Instructor Updates Course
    │
    └── Approve
           │
           ▼
        Published
```

This workflow ensures that instructors cannot directly publish courses without administrative approval.

---

# 15. API Generation

Strapi automatically generates API endpoints based on configured Content Types and their relationships.

Therefore, the project does not require a separately implemented backend API layer for the Academic MVP.

The development process will focus on:

1. Creating Content Types.
2. Defining their fields.
3. Defining relationships.
4. Configuring permissions.
5. Configuring authentication.
6. Configuring publication and administrative workflows.
7. Consuming the generated APIs from React.

The React frontend will consume the APIs exposed by Strapi.

Example conceptual flow:

```text
React
   │
   │ GET /courses
   ▼
Strapi API
   │
   ▼
Database
   │
   ▼
Strapi API
   │
   │ Course Data
   ▼
React
```

The exact endpoint structure is determined by Strapi's API generation and project configuration rather than manually designing an independent API architecture.

---

# 16. Permissions and Access Control

Access to platform functionality is controlled through authentication and permissions.

The system should distinguish between:

### Public Access

Examples:

- Public course discovery
- Course information
- Public learning path information

### Authenticated Student Access

Examples:

- Enrollment
- Learning content
- Progress tracking
- Quiz attempts
- Reviews
- Favorites
- Certificates
- Learning path enrollment
- Challenge submissions
- Notifications

### Instructor Access

Examples:

- Creating courses
- Editing owned courses
- Managing course content
- Submitting courses for review

### Administrative Access

Examples:

- Course approval
- Course rejection
- Platform content management

Permissions should follow the Business Rules and Functional Requirements defined elsewhere in the project documentation.

---

# 17. Database Mapping

The Strapi Content Architecture maps directly to the approved database design.

| Database Entity            | Strapi Representation                  |
| -------------------------- | -------------------------------------- |
| Users                      | Strapi User                            |
| Categories                 | Category Content Type                  |
| Courses                    | Course Content Type                    |
| Sections                   | Section Content Type                   |
| Lessons                    | Lesson Content Type                    |
| Lesson Resources           | Lesson Resource Content Type           |
| Quizzes                    | Quiz Content Type                      |
| Questions                  | Question Content Type                  |
| Question Options           | Question Option Content Type           |
| Quiz Attempts              | Quiz Attempt Content Type              |
| Quiz Attempt Answers       | Quiz Attempt Answer Content Type       |
| Enrollments                | Enrollment Content Type                |
| Lesson Progress            | Lesson Progress Content Type           |
| Reviews                    | Review Content Type                    |
| Certificates               | Certificate Content Type               |
| Favorites                  | Favorite Content Type                  |
| Course Requirements        | Course Requirement Content Type        |
| Course Learning Outcomes   | Course Learning Outcome Content Type   |
| Course Completion Rules    | Course Completion Rule Content Type    |
| Learning Paths             | Learning Path Content Type             |
| Learning Path Steps        | Learning Path Step Content Type        |
| Learning Path Step Courses | Learning Path Step Course Content Type |
| Learning Path Enrollments  | Learning Path Enrollment Content Type  |
| Module Challenges          | Module Challenge Content Type          |
| Challenge Submissions      | Challenge Submission Content Type      |
| Notifications              | Notification Content Type              |

This mapping ensures consistency between the conceptual database design and the actual Strapi implementation.

---

# 18. MVP Scope

The Strapi architecture described in this document represents the **Academic MVP**.

The MVP includes the core functionality required for:

- User authentication
- Course discovery
- Course enrollment
- Course learning
- Lesson progress
- Quizzes
- Certificates
- Learning paths
- Reviews
- Favorites
- Instructor course management
- Administrative course approval
- Notifications
- Module challenges and submissions

The architecture does not require implementation of future features that were explicitly postponed from the MVP.

Examples of postponed areas include:

- Community features
- Instructor marketplace
- Advanced gamification
- AI-powered learning assistants
- Advanced instructor analytics

These features may be introduced in future versions without being considered part of the Academic MVP.

---

# 19. Future Extensibility

The architecture is designed to allow future expansion.

Future features can introduce additional Content Types or extend existing ones when required.

Possible future areas include:

- Advanced gamification
- Community features
- Instructor marketplace
- Instructor analytics
- AI learning assistants
- Advanced recommendation systems
- Additional learning activities

Future extensions should be evaluated against the existing PRD and Product Decisions before implementation.

---

# 20. Implementation Guidelines

During implementation, the following order is recommended:

```text
1. Configure Strapi
        ↓
2. Configure Users & Permissions
        ↓
3. Create Core Content Types
        ↓
4. Create Course Structure
        ↓
5. Create Assessment Content Types
        ↓
6. Create Learning & Progress Content Types
        ↓
7. Create Learning Path Content Types
        ↓
8. Create Challenge Content Types
        ↓
9. Create Notifications
        ↓
10. Configure Relationships
        ↓
11. Configure Permissions
        ↓
12. Configure Course Approval Workflow
        ↓
13. Add Initial Content
        ↓
14. Connect React Frontend
```

Implementation should follow the approved ERD and business rules.

If an implementation detail conflicts with the documented system design, the documentation should be reviewed before introducing the change.

---

# 21. Design Constraints

The following constraints apply to the Academic MVP:

- React must not access the database directly.
- Strapi is the backend API layer.
- Strapi is responsible for database access.
- Strapi's generated APIs should be used instead of building an unnecessary custom API layer.
- Administrative course approval must be preserved.
- Core MVP functionality should not depend on postponed Version 2 features.
- New entities should not be introduced without a clear functional requirement.
- The database design and Strapi relationships must remain consistent.

---

# 22. Final Architecture Summary

The final Nevyrion Learning content architecture can be summarized as:

```text
                    Nevyrion Learning
                           │
                           ▼
                  ┌─────────────────┐
                  │ React Frontend  │
                  │   Learner UI    │
                  └────────┬────────┘
                           │
                 API Requests / Responses
                           │
                           ▼
                  ┌─────────────────┐
                  │     Strapi      │
                  │                 │
                  │ Backend API     │
                  │ Content Types   │
                  │ Authentication  │
                  │ Admin Panel     │
                  │ Permissions     │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │    Database     │
                  │                 │
                  │ Persistent Data │
                  └─────────────────┘
```

Strapi serves as the central backend platform connecting the React frontend with the persistent database and managing the platform's content and administrative operations.

The Content Types and relationships defined in this document represent the implementation-level translation of the approved system design.

---

# 23. Document Status

**Project:** Nevyrion Learning
**Company:** Nevyrion
**Version:** 1.0.0
**Release Type:** Academic MVP
**Document:** Strapi Content Architecture
**Status:** Approved for Implementation
