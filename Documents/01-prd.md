# Product Requirements Document

## Product Overview

### Product Name

Nevyrion Learning

### Product Type

Learning Management System (LMS)

### Description

Nevyrion Learning is a modern learning platform designed to provide learners with a structured
and organized educational experience. Instead of leaving learners lost
between countless educational resources, the platform offers carefully
designed learning paths, curated courses,
and progress tracking to help them stay focused and continuously improve.

Although the long-term vision is to support multiple learning fields such as programming,
mathematics, science, and languages, the first version of the platform primarily focuses on programming education.

---

## Problem Statement

The internet provides an enormous amount of educational content,
but having access to information does not always mean having a clear learning journey.
Learners often struggle with information overload, unclear roadmaps,
and constant distraction while trying to achieve their learning goals.

Common challenges include:

- Learning from random resources without a structured plan.
- Following unclear or conflicting roadmaps.
- Losing motivation before completing a learning journey.
- Feeling overwhelmed by the rapid growth of technology and AI.

---

## Proposed Solution

Nevyrion Learning addresses these challenges by providing structured learning paths,
carefully curated courses, and progress tracking within a single platform.

Instead of spending time searching for what to learn next,
learners are guided through clear step-by-step learning paths
that allow them to focus on learning, stay motivated, and build their skills with confidence.

---

## Objectives

### Business Objectives

- Build a modern educational platform with a strong foundation for future SaaS development.
- Deliver a high-quality Academic MVP that demonstrates the platform's core vision.
- Create an organized learning experience that can be expanded with additional features in future releases.

### User Objectives

- Help learners stop feeling lost between countless educational resources.
- Provide a clear starting point and structured learning journey.
- Encourage learners to stay consistent and motivated throughout their learning process.
- Enable learners to focus on learning instead of deciding what to learn next.
- Build learners' confidence by giving them a clear sense of progress toward their goals.

---

## MVP Scope

The Academic MVP focuses on delivering the core learning experience while keeping the project achievable within the available development time.

### Included

- User Authentication
- Course Browsing
- Learning Paths
- Course Enrollment
- Video Learning
- Progress Tracking
- Reviews & Ratings
- Instructor Course Management
- Administrative Approval Workflow

### Excluded

- AI Tutor
- Live Classes
- Community Features
- Course Marketplace
- Mobile Application

---

## Target Audience

### Primary Audience

The primary audience for Nevyrion Learning is people who want to learn programming in a structured and organized way.
This includes university students, self-learners, and career switchers who often struggle
with choosing the right learning path and staying consistent.

### Secondary Audience

As the platform evolves, it will expand to support learners interested in other fields
such as mathematics, science, languages, and other professional skills.

---

## User Roles

### Guest

**Description**

A guest is a visitor who has not created an account yet. Their primary goal is to explore the platform,
evaluate its learning content, and decide whether it meets their educational needs before registering.

**Permissions**

- Browse courses.
- Search for courses.
- Filter courses.
- View course details.
- View learning paths.
- View instructor profiles.
- View course reviews.

**Restrictions**

- Cannot enroll in courses.
- Cannot watch course lessons.
- Cannot download learning resources.
- Cannot submit reviews.
- Cannot track learning progress.
- Cannot interact with course content.

### Student

**Description**

A student is a registered user who uses the platform to enroll in courses,
follow structured learning paths, track progress, and actively participate in the learning experience.

**Permissions**

- Enroll in courses.
- Access enrolled course lessons.
- Continue learning from the last completed lesson.
- Track learning progress.
- Take quizzes and module challenges.
- Add courses to favorites.
- Submit course reviews and ratings.
- View and edit their profile.

**Restrictions**

- Cannot create, edit, or delete courses.
- Cannot manage other users.
- Cannot manage instructors.
- Cannot access the administration dashboard.
- Cannot issue certificates without meeting course completion requirements.

**Typical User Journey**

Login

↓

Continue Learning

↓

Watch Lesson

↓

Complete Lesson

↓

Complete Module Challenge (if available)

↓

Progress Updated

↓

Logout

### Instructor

**Description**

An instructor is responsible for creating and managing educational content on the platform.
Their primary goal is to publish high-quality courses, monitor student progress, and provide an engaging learning experience.

**Permissions**

- Create and edit their own courses.
- Organize courses into sections and lessons.
- Upload learning materials.
- Create quizzes and module challenges.
- Define course completion requirements.
- View enrolled students.
- View course analytics.
- Submit courses for review before publishing.
- Manage their own instructor profile.
- Upload course thumbnail.
- Manage course resources.

**Restrictions**

- Cannot publish courses without administrator approval.
- Cannot manage platform categories or settings.
- Cannot edit or delete courses created by other instructors.
- Cannot modify student learning progress.
- Cannot manage users or other instructors.
- Cannot access the administration dashboard.

**Typical User Journey**

Login

↓

Create Course

↓

Add Sections

↓

Add Lessons

↓

Create Quizzes & Challenges

↓

Submit Course for Review

↓

Admin Approval

↓

Course Published

↓

Monitor Students & Update Course

### Administrator

**Description**

The administrator is responsible for managing the entire platform, maintaining content quality,
overseeing users and instructors, and ensuring the platform operates smoothly.

**Permissions**

- Manage all users.
- Manage all instructors.
- Review, approve, reject, or remove courses.
- Manage categories, skill levels, and tags.
- Manage platform settings.
- Moderate reviews and reported content.
- View platform analytics.
- Manage certificates and platform-wide educational content.
- Suspend or remove accounts that violate platform policies.

**Restrictions**

- Has full administrative access within the platform.

**Typical User Journey**

Login

↓

Review Submitted Courses

↓

Approve or Reject Courses

↓

Manage Users & Instructors

↓

Moderate Platform Content

↓

Monitor Platform Analytics

↓

Update Platform Settings

↓

Logout

---

## MVP Scope

The Academic MVP focuses on delivering a complete and structured learning experience
while keeping the implementation achievable within the available development time.

The MVP includes the following core features:

- User authentication and authorization.
- Course discovery, search, filtering, and enrollment.
- Structured learning paths.
- Video-based learning experience.
- Learning progress tracking.
- Quizzes and module challenges.
- Course reviews and ratings.
- Course completion certificates.
- Student dashboard.
- Instructor dashboard.
- Course approval workflow.
- Notifications.

The following features are intentionally excluded from the Academic MVP and planned for future releases:

- AI-powered learning assistant.
- Community posts and discussions.
- Instructor marketplace.
- Live classes.
- Gamification and reward system.
- Events and workshops.
- Instructor and student messaging.
- Native mobile applications.

---

## Functional Requirements

- Functional requirements are documented in detail in the Features document.

---

## Non-Functional Requirements

- Responsive user interface across desktop, tablet, and mobile devices.
- Fast page loading and smooth navigation.
- Secure authentication and role-based authorization.
- Maintainable and modular application architecture.
- Scalable backend architecture to support future growth.
- Reliable progress tracking and data persistence.
- Consistent user experience across the platform.
- RESTful API communication between frontend and backend.
- Modern and accessible user interface.

---

## Assumptions

The following assumptions were made during the design of the Academic MVP:

- Users have a stable internet connection while using the platform.
- Instructors create high-quality educational content.
- Administrators review submitted courses regularly.
- Learners follow learning paths as intended.
- The platform will continue to evolve with future feature releases.

---

## Constraints

The Academic MVP is developed under the following constraints:

- The project is developed by a single developer.
- Development time is limited by the academic schedule.
- Administrative operations rely on Strapi's built-in Administration Panel.
- Advanced features are intentionally postponed to future versions.
- The first release focuses on programming education only.

---

## Risks

- Limited educational content during the initial release.
- Delays in course approval may affect instructor experience.
- Users may abandon learning paths before completion.
- Future feature expansion may require database and API modifications.
- Third-party service dependencies may affect platform availability.
- Video storage and streaming may introduce additional infrastructure complexity.

---

## Success Criteria

The Academic MVP will be considered successful if it demonstrates a complete and realistic learning experience, including:

- User registration and authentication
- Course discovery
- Learning path exploration
- Course enrollment
- Lesson completion
- Progress tracking
- Quiz completion
- Certificate generation
- Instructor course management
- Administrative course approval workflow

---

## Success Metrics

The Academic MVP will be considered successful if:

- All core user journeys are fully functional.
- Users can complete the learning journey without critical issues.
- Progress tracking works accurately across enrolled courses.
- Course approval workflow functions correctly.
- Certificates are generated automatically after successful course completion.
- The platform provides a consistent user experience across supported devices.
