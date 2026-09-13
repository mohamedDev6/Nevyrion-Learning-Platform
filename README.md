````md
# Nevyrion Learning

> An Academic Learning Management Platform built with React and Strapi.

Nevyrion Learning is an academic LMS-style platform designed to provide a structured learning experience where students can discover courses, enroll in learning content, track their progress, complete quizzes, follow learning paths, and earn certificates.

The platform also provides instructors with course management capabilities and administrators with course review and approval workflows.

---

## 📌 Project Overview

Nevyrion Learning is being developed as an **Academic MVP** with a long-term vision of evolving into a production-ready SaaS learning platform.

The project is designed around a clear separation between the frontend, backend, and database:

```text
┌──────────────────────────────┐
│        React Frontend        │
│         Learner UI           │
└──────────────┬───────────────┘
               │
               │ API Requests / Responses
               ▼
┌──────────────────────────────┐
│            Strapi            │
│                              │
│      Backend API             │
│      Content Management      │
│      Authentication          │
│      Admin Panel             │
└──────────────┬───────────────┘
               │
               │ Database Access
               ▼
┌──────────────────────────────┐
│          Database            │
│       Persistent Data        │
└──────────────────────────────┘
````

The React frontend communicates with Strapi through APIs.

React does **not** communicate directly with the database.

---

# 🎯 Project Goals

The main goals of Nevyrion Learning are:

* Provide a structured online learning experience.
* Make course discovery simple and organized.
* Allow learners to follow structured learning paths.
* Track learner progress.
* Provide quizzes and assessments.
* Generate certificates after course completion.
* Allow instructors to create and manage courses.
* Provide an administrative course approval workflow.
* Build a scalable foundation for future platform features.

---

# 👥 User Roles

The Academic MVP is based on three main application roles:

### Guest

Unauthenticated visitors who can explore public platform content.

Guests can:

* Browse courses.
* View course information.
* Explore learning paths.

Guests cannot:

* Enroll in courses.
* Access protected learning content.
* Submit reviews.
* Access student functionality.

---

### Student

Authenticated learners who use the platform to study.

Students can:

* Browse and search courses.
* Enroll in courses.
* Access learning content.
* Complete lessons.
* Track learning progress.
* Take quizzes.
* Receive certificates.
* Follow learning paths.
* Submit course reviews.
* Save courses to favorites.
* Submit module challenges.
* Receive notifications.
* Manage their profile.

---

### Instructor

Authenticated users who create and manage educational content.

Instructors can:

* Create courses.
* Manage their courses.
* Create sections and lessons.
* Add course content.
* Submit courses for review.
* Update rejected courses.

Courses cannot be published directly by instructors.

They must go through the administrative approval workflow.

---

### Admin

Administrative operations are handled through the **Strapi Admin Panel**.

Admins can:

* Review submitted courses.
* Approve courses.
* Reject courses.
* Manage platform content.

A separate custom React Admin Dashboard is not part of the Academic MVP.

---

# 🚀 Core Features

## Course Discovery

Learners can:

* Browse available courses.
* Search for courses.
* Explore course details.
* View course categories.
* Preview available lessons.

---

## Course Enrollment

Authenticated students can enroll in available courses.

Enrollment allows the learner to access protected learning content and track their progress.

---

## Learning Experience

Students can:

* Access enrolled courses.
* Navigate through sections.
* Complete lessons.
* Access lesson resources.
* Track their progress.

---

## Quizzes

The platform supports:

* Quizzes.
* Questions.
* Question options.
* Quiz attempts.
* Submitted answers.

Quiz attempts are associated with the learner and the relevant quiz.

---

## Progress Tracking

The platform tracks learner progress at the lesson level.

This allows students to see which parts of their courses have been completed.

---

## Certificates

After satisfying the course completion requirements, students can receive certificates.

Certificates preserve historical information such as:

* Student name.
* Course name.
* Instructor name.

---

## Learning Paths

Learning Paths provide a structured sequence of courses.

Students can:

* Explore learning paths.
* Enroll in learning paths.
* Follow learning path steps.
* Complete courses within a learning path.
* Track their current position.

---

## Reviews

Students can submit reviews for courses according to the platform's business rules.

---

## Favorites

Students can save courses to their favorites for easier access later.

---

## Module Challenges

Courses may contain practical challenges associated with learning sections.

Students can submit their solutions through challenge submissions.

---

## Notifications

Users can receive notifications for important platform events.

Examples include:

* Course approval.
* Course rejection.
* Enrollment-related events.
* Certificate availability.
* Learning-related events.

---

# 🔐 Authentication

Nevyrion Learning uses Strapi's authentication and user management capabilities.

The project does not implement a separate custom authentication backend.

The general authentication flow is:

```text
Visitor
   │
   ▼
Register / Login
   │
   ▼
Authenticated User
   │
   ▼
Student / Instructor
   │
   ▼
Access Role-Specific Features
```

Authentication and authorization are handled through Strapi and its permissions system.

---

# 🧩 Course Approval Workflow

Courses follow an approval-based lifecycle:

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
  │               │
  ▼               │
Published ◄───────┘
```

### Draft

The instructor is creating or editing the course.

### Submitted

The instructor submits the course for review.

### Under Review

The administrator reviews the course.

### Approved

The course passes the review process.

### Rejected

The course requires changes before it can be approved.

### Published

The approved course becomes available to learners according to the platform's publication rules.

---

# 🏗️ Technology Stack

## Frontend

* React
* JavaScript
* HTML
* CSS
* Tailwind CSS

## Backend

* Strapi

## Database

* Relational Database managed through Strapi

## Development & Design

* Git
* GitHub
* draw.io
* Postman

> The exact package versions and environment configuration may change during implementation.

---

# 🏛️ System Architecture

Nevyrion Learning follows a separated frontend/backend architecture.

```text
User
 │
 ▼
React Frontend
 │
 │ API Requests / Responses
 ▼
Strapi
 │
 ├── REST API
 ├── Authentication
 ├── Content Management
 ├── Permissions
 └── Admin Panel
 │
 ▼
Database
```

### React

Responsible for the learner-facing user experience.

### Strapi

Responsible for:

* Backend APIs.
* Content Types.
* Relationships.
* Authentication.
* Permissions.
* Database communication.
* Administrative content management.

### Database

Responsible for persistent application data.

---

# 🗄️ Database Architecture

The database design was created around the main entities and relationships required by the platform.

Major entities include:

* Users
* Categories
* Courses
* Sections
* Lessons
* Lesson Resources
* Quizzes
* Questions
* Question Options
* Quiz Attempts
* Quiz Attempt Answers
* Enrollments
* Lesson Progress
* Reviews
* Certificates
* Favorites
* Course Requirements
* Course Learning Outcomes
* Course Completion Rules
* Learning Paths
* Learning Path Steps
* Learning Path Step Courses
* Learning Path Enrollments
* Module Challenges
* Challenge Submissions
* Notifications

The database design uses relationships and intermediary entities where required to represent many-to-many relationships.

---

# 🔗 Strapi Content Architecture

Strapi Content Types are based on the approved database design.

The main Content Types include:

```text
Core
├── User
├── Category
├── Course
├── Section
├── Lesson
└── Lesson Resource

Assessment
├── Quiz
├── Question
├── Question Option
├── Quiz Attempt
└── Quiz Attempt Answer

Learning
├── Enrollment
├── Lesson Progress
├── Certificate
├── Review
└── Favorite

Course Structure
├── Course Requirement
├── Course Learning Outcome
└── Course Completion Rule

Learning Paths
├── Learning Path
├── Learning Path Step
├── Learning Path Step Course
└── Learning Path Enrollment

Challenges
├── Module Challenge
└── Challenge Submission

Notifications
└── Notification
```

Strapi automatically generates API endpoints based on the configured Content Types and relationships.

The project therefore does not require a separately implemented custom backend API layer for the Academic MVP.

---

# 📚 Documentation

The project documentation is organized to keep product decisions, system design, and implementation details separated.

## Product Documentation

### Product Requirements Document

Defines the overall product vision, goals, scope, users, and requirements.

📄 [`01-product-requirements.md`](documents/01-prd.md)

---

### User Personas

Defines the main users of the platform and their goals, problems, and motivations.

📄 [`02-user-personas.md`](documents/02-user-personas.md)

---

### Product Decisions

Contains important product decisions made during the planning phase.

📄 [`07-decisions.md`](documents/04-decisions.md)

---

### Features

Defines the platform's features and their behavior.

📄 [`09-features.md`](documents/05-features.md)

---

# 🏗️ System Design Documentation

## Database Design

Defines the database entities, relationships, primary keys, foreign keys, and overall data model.

📄 [`Database Design`](documents/database/README.md)

---

## Entity Relationship Diagram

The ERD provides a visual representation of the database structure and relationships.

📄 [`ERD`](documents/database/)

---

## System Architecture

Defines the relationship between React, Strapi, and the database.

📄 [`System Architecture`](documents/system-architecture/README.md)

---

## Strapi Content Architecture

Defines how the approved system design is translated into Strapi Content Types and relationships.

📄 [`Strapi Content Architecture`](documents/strapi-content-architecture.md)

---

## User Flows

Documents the critical user journeys through the platform.

📄 [`User Flows`](documents/user-flows/README.md)

---

# 📋 Requirements Documentation

The project also includes documentation covering:

* Functional Requirements
* Non-Functional Requirements
* Assumptions
* Constraints
* Business Rules
* Risks
* Success Criteria
* Success Metrics
* MVP Scope

These documents should be treated as part of the project's system requirements and design decisions.

---

# 📁 Project Documentation Structure

The documentation is organized approximately as follows:

```text
docs/
│
├── product/
│   ├── 01-product-requirements.md
│   ├── 02-user-personas.md
│   ├── 07-decisions.md
│   └── 09-features.md
│
├── database/
│   ├── README.md
│   └── ERD/
│
├── architecture/
│   ├── README.md
│   └── strapi-content-architecture.md
│
└── user-flows/
    └── README.md
```

Additional requirement documents may exist depending on the final documentation structure.

---

# 📦 MVP Scope

The Academic MVP focuses on the core learning experience.

### Included

* Authentication
* Course discovery
* Course search
* Course details
* Course preview
* Course enrollment
* Learning content
* Lesson progress
* Quizzes
* Quiz attempts
* Course completion
* Certificates
* Learning paths
* Reviews
* Favorites
* Instructor course management
* Course approval workflow
* Notifications
* Module challenges
* Challenge submissions

---

# 🚫 Out of Scope

The following features are intentionally excluded from the Academic MVP:

### Community Features

Community discussions and social learning features are postponed to a future version.

### Instructor Marketplace

A marketplace connecting instructors and learners is not part of the MVP.

### Advanced Gamification

Advanced points, badges, leaderboards, and similar gamification systems are postponed.

### AI Learning Assistants

AI-powered tutors, learning assistants, and AI recommendation systems are not part of Version 1.

### Advanced Instructor Analytics

Advanced instructor analytics and detailed performance dashboards are postponed.

These features may be introduced in future versions without changing the core product vision.

---

# 🧭 Future Vision

The Academic MVP is intended to provide the foundation for a future production-ready SaaS platform.

Potential future directions include:

* Community features.
* Instructor marketplace.
* Advanced gamification.
* AI-powered learning assistants.
* Personalized learning recommendations.
* Advanced instructor analytics.
* More advanced assessment systems.
* Expanded learning activities.

Future features should be evaluated against the existing PRD and Product Decisions before implementation.

---

# 📊 Success Criteria

The MVP is considered successful if users can complete the platform's core journeys.

### Student

```text
Register
   ↓
Explore Courses
   ↓
View Course
   ↓
Enroll
   ↓
Learn
   ↓
Track Progress
   ↓
Complete Quiz
   ↓
Complete Course
   ↓
Receive Certificate
```

### Instructor

```text
Login
   ↓
Create Course
   ↓
Manage Content
   ↓
Submit Course
   ↓
Wait for Review
   ↓
Course Approved
   ↓
Course Published
```

### Admin

```text
Login
   ↓
Open Admin Panel
   ↓
Review Submitted Course
   ↓
Approve / Reject
   ↓
Course Published or Returned
```

---

# ⚠️ Known Risks

The main identified project risks include:

* Limited educational content during the initial release.
* Course approval delays affecting instructor experience.
* Learners abandoning learning paths before completion.
* Future feature expansion requiring database or API changes.
* Dependencies on third-party services.

These risks are documented in more detail within the project documentation.

---

# 🔄 Development Approach

The project follows a documentation-first approach during the system design phase.

The general process is:

```text
Product Discovery
       ↓
PRD
       ↓
Features
       ↓
Business Rules
       ↓
Requirements
       ↓
User Personas
       ↓
Database Design
       ↓
System Architecture
       ↓
Strapi Content Architecture
       ↓
Final System Review
       ↓
Implementation
```

The documentation acts as the reference point for implementation decisions.

If a new requirement or problem appears during development, the relevant documentation should be updated when necessary.

---

# 🛠️ Implementation Strategy

After completing the final system design review, development will proceed with the actual implementation.

The expected implementation sequence is:

```text
1. Configure Strapi
        ↓
2. Configure Authentication & Permissions
        ↓
3. Create Core Content Types
        ↓
4. Configure Relationships
        ↓
5. Create Course Structure
        ↓
6. Create Assessment System
        ↓
7. Create Enrollment & Progress System
        ↓
8. Create Learning Paths
        ↓
9. Create Challenges
        ↓
10. Create Notifications
        ↓
11. Configure Course Approval Workflow
        ↓
12. Add Initial Content
        ↓
13. Connect React Frontend
        ↓
14. Implement Core User Journeys
        ↓
15. Test & Refine
```

---

# 🧪 Testing

Testing will focus primarily on the critical user journeys and business rules.

Important scenarios include:

* Registration.
* Login.
* Authentication errors.
* Course discovery.
* Course enrollment.
* Protected course access.
* Lesson completion.
* Progress tracking.
* Quiz attempts.
* Course completion.
* Certificate generation.
* Review submission.
* Favorite management.
* Learning path enrollment.
* Instructor course creation.
* Course submission.
* Course approval.
* Course rejection.
* Notifications.
* Challenge submissions.

---

# 📌 Project Status

**Current Phase:**

> System Design → Final Review

The major product and system design documentation has been completed.

Current status:

* [x] Product Requirements
* [x] User Personas
* [x] Product Decisions
* [x] Features
* [x] Requirements
* [x] Business Rules
* [x] MVP Scope
* [x] Database Design
* [x] ERD
* [x] System Architecture
* [x] Strapi Content Architecture
* [ ] Final Documentation Review
* [ ] Implementation
* [ ] Testing
* [ ] Academic MVP Release

---

# 📜 Project Information

| Property     | Value                         |
| ------------ | ----------------------------- |
| Company      | Nevyrion                      |
| Product      | Nevyrion Learning             |
| Version      | 1.0.0                         |
| Release Type | Academic MVP                  |
| Frontend     | React                         |
| Backend      | Strapi                        |
| Database     | Relational Database           |
| Architecture | Frontend + Backend + Database |
| Status       | System Design / Final Review  |

---

# 🎯 Long-Term Vision

The long-term vision is to transform the Academic MVP into a production-ready SaaS learning platform.

The MVP provides the foundation for:

* Scalable learning experiences.
* Structured educational content.
* Multiple user roles.
* Instructor content management.
* Administrative moderation.
* Progress tracking.
* Learning paths.
* Assessments.
* Certifications.
* Future AI-powered learning capabilities.

The goal is not to implement every possible LMS feature in Version 1.

The goal is to build a **solid, well-structured foundation** that can evolve without unnecessarily rebuilding the system.

---

# 👨‍💻 Development Philosophy

Nevyrion Learning is designed around several principles:

### Keep the MVP Focused

Only features that contribute directly to the core learning experience should be included in Version 1.

### Keep Responsibilities Clear

React handles the UI.

Strapi handles the backend and content management.

The database handles persistent storage.

### Avoid Unnecessary Complexity

The system should not introduce custom backend architecture where Strapi already provides the required functionality.

### Design Before Implementation

Major architectural and product decisions should be documented before implementation.

### Allow Controlled Evolution

Future features should extend the existing architecture rather than forcing unnecessary redesigns.

---

# 📄 Documentation as the Source of Truth

The project documentation serves as the main reference for product and system decisions.

Before introducing a major feature or architectural change, the following should be considered:

> Does this change align with the PRD, Business Rules, Database Design, and System Architecture?

If the answer is no, the change should be reviewed before implementation.

---

# 📚 Documentation Navigation

| Document                                                                        | Description                                    |
| ------------------------------------------------------------------------------- | ---------------------------------------------- |
| [Product Requirements](documents/product/01-prd.md)                 | Product vision, goals, scope, and requirements |
| [User Personas](documents/02-user-personas.md)                               | Main users and their goals                     |
| [Product Decisions](documents/04-decisions.md)                               | Important product decisions                    |
| [Features](documents/05-features.md)                                         | Platform features and behavior                 |
| [Database Documentation](documents/database/README.md)                               | Database structure and relationships           |
| [System Architecture](documents/system-architecture/README.md)                              | React, Strapi, and database architecture       |
| [Strapi Content Architecture](documents/strapi-content-architecture/README.md) | Strapi Content Types and relationships         |
| [User Flows](documents/user-flows/README.md)                                         | Critical platform user journeys                |

---

# 🚀 Final Note

Nevyrion Learning is currently being developed as an **Academic MVP**.

The project prioritizes:

**Clear requirements → Solid system design → Focused implementation → Working product**

The documentation defines the foundation.

The implementation brings it to life.

---
