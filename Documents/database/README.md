# `database/README.md`

This is a simple README explaining **what the database represents** and where the ERD is located.

```md
# Database Design

## Overview

The Nevyrion Learning database is designed to support the core functionality of the Academic MVP.

The database stores users, courses, learning content, enrollments, learning progress, assessments, certificates, learning paths, and other supporting platform data.

## ERD

The Entity Relationship Diagram (ERD) represents the database entities and their relationships.

The ERD is maintained as the visual source of truth for the database structure.

## Main Entities

### Users

Stores platform users and their account information.

Users may interact with the platform according to their assigned role.

### Courses

Stores course information and its relationships with categories, instructors, sections, lessons, requirements, learning outcomes, completion rules, and other course-related entities.

### Categories

Organizes courses into categories.

### Sections

Represents the sections or modules within a course.

### Lessons

Represents individual learning units within course sections.

### Lesson Resources

Stores resources associated with lessons.

### Enrollments

Represents the relationship between learners and courses.

It records which courses a learner has enrolled in.

### Lesson Progress

Tracks learner progress through individual lessons.

### Quizzes

Represents assessments associated with learning content.

### Questions

Stores quiz questions.

### Question Options

Stores the available options for quiz questions.

### Quiz Attempts

Represents a learner's attempt to complete a quiz.

### Quiz Attempt Answers

Stores the answers submitted during a quiz attempt.

### Certificates

Stores certificates issued to learners after completing the required course conditions.

### Reviews

Stores learner reviews and ratings for courses.

### Favorites

Represents courses saved by learners.

### Learning Paths

Represents structured learning paths containing multiple steps and courses.

### Learning Path Steps

Represents the ordered steps within a learning path.

### Learning Path Step Courses

Associates courses with learning path steps.

### Learning Path Enrollments

Represents learners enrolled in learning paths.

### Course Requirements

Stores the knowledge or prerequisites expected before taking a course.

### Course Learning Outcomes

Stores the expected learning outcomes of a course.

### Course Completion Rules

Defines the conditions required for completing a course.

### Module Challenges

Represents practical challenges associated with learning modules.

### Challenge Submissions

Stores learner submissions for module challenges.

### Notifications

Stores notifications associated with users.

## Relationships

The database uses relationships between entities to represent the structure of the learning platform.

Examples include:

User → Courses
User → Enrollments
User → Lesson Progress
User → Reviews
User → Favorites
User → Certificates

Course → Category
Course → Sections
Course → Requirements
Course → Learning Outcomes
Course → Completion Rules
Course → Reviews

Section → Lessons
Lesson → Resources
Lesson → Progress

Quiz → Questions
Question → Question Options
Quiz → Quiz Attempts
Quiz Attempt → Quiz Attempt Answers

Learning Path → Learning Path Steps
Learning Path Step → Courses
User → Learning Path Enrollments

Module Challenge → Challenge Submissions
User → Challenge Submissions
```

## Keys

### Primary Keys (PK)

Each entity has a unique primary key used to identify individual records.

### Foreign Keys (FK)

Foreign keys establish relationships between related entities.

### For example:

```text
course_id
user_id
lesson_id
quiz_id

are used to reference related records.
```

## Many-to-Many Relationships

Many-to-many relationships are represented using intermediate entities.

Examples:

```text
Users ↔ Courses
        │
   Enrollments

and:

Learning Path Steps ↔ Courses
              │
   Learning Path Step Courses
```

## Design Goals

### The database design aims to:

- Represent the core Academic MVP requirements.
- Maintain clear relationships between entities.
- Support learner progress tracking.
- Support course and learning path management.
- Support assessments and certificates.
- Avoid unnecessary duplication.
- Allow future expansion of the platform.

## Scope

This database design represents the Academic MVP.

Future versions may introduce additional entities or modify existing relationships as new platform requirements are introduced.

## Important Note

I **intentionally omitted the data types and SQL schemas** from the README.

The purpose of the README here is to explain:

> **What the database does and what it consists of.**

The ERD, on the other hand, is what illustrates the **tables, relationships, and PKs/FKs** in detail.

This way, you have:

```text
PRD
 │
 ├── Features
 ├── Business Rules
 ├── User Personas
 └── MVP Requirements

System Design
 │
 ├── Architecture README
 └── Database README
       └── ERD
```
