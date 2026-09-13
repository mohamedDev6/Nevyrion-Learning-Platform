# Business Rules

This document defines the business rules that govern how Nevyrion Learning operates.

These rules ensure consistent platform behavior regardless of implementation details.

---

# User Management

- Every user must register before accessing protected platform features.
- Email verification is required before accessing learning features.
- Users are assigned a role during account creation.
- Users cannot change their own role.
- Students cannot access instructor or administrator features.
- Instructors cannot access administrator features.
- Account deletion is excluded from the Academic MVP.

---

# Authentication

- Only authenticated users can enroll in courses.
- Authentication is required to track learning progress.
- Authentication is required to submit reviews.
- Authentication is required to receive certificates.
- Password reset requires email verification.

---

# Courses

- Every course belongs to exactly one instructor.
- Courses must belong to a category.
- Courses must have a difficulty level.
- Courses cannot be published without administrator approval.
- Published courses are visible to all users.
- Draft courses are visible only to their instructor.
- Guests may browse course information but cannot enroll.
- Courses may contain free preview lessons.
- Students may enroll only once in the same course.
- Enrolled students keep permanent access unless future business policies state otherwise.

---

# Learning

- Students can access only courses they are enrolled in.
- Lessons should be completed sequentially when required by the instructor.
- Learning progress is automatically saved.
- Students can resume learning from their last watched lesson.
- Completing lessons updates course progress automatically.
- Progress cannot be modified manually by instructors.
- Only enrolled students can complete quizzes and challenges.

---

# Quizzes & Module Challenges

- Instructors define quizzes and module challenges for their own courses.
- Quiz results contribute to course completion requirements.
- Module challenges contribute to course completion requirements.
- Students may only attempt quizzes belonging to enrolled courses.

---

# Reviews & Ratings

- Only enrolled students can submit course reviews.
- Each student may submit only one review per course.
- Ratings use a five-star scale.
- Review comments are optional.
- Students may edit or delete their own reviews.
- Review ratings contribute to the course's average rating.
- Instructors may view review content but cannot modify or remove student reviews.
- Administrators may moderate or remove inappropriate reviews.

---

# Certificates

- Certificates are generated automatically.
- Certificates are issued only after all completion requirements are satisfied.
- Completion requirements are defined by the course instructor.
- Students may download certificates as PDF files.
- Instructors may define custom certificate templates.
- Administrators may view all generated certificates.

---

# Learning Paths

- Learning Paths are created and managed only by administrators.
- A learning path consists of multiple ordered learning stages.
- Students must complete stages sequentially.
- Previously purchased courses reduce the total learning path price.
- Learning path duration is calculated from the selected courses.
- Completing a learning path grants a platform certificate.
- Completing a learning path may unlock profile achievements.

---

# Instructor Management

- Instructors manage only their own courses.
- Instructors cannot edit or delete courses created by other instructors.
- Instructors cannot publish courses directly.
- Course updates require administrator approval before publication.
- Instructors may upload learning materials.
- Instructors may create quizzes and challenges.
- Instructors may monitor enrolled students.
- Instructors may view learning analytics.
- Instructors cannot modify student learning progress.

---

# Administration

- Administrators have full platform management permissions.
- Administrators manage users, instructors, categories, learning paths, and platform settings.
- Administrators approve or reject submitted courses.
- Administrators may suspend accounts that violate platform policies.
- Administrative operations are performed through Strapi Administration Panel.

---

# Notifications

- Notifications are generated automatically by platform events.
- Notifications remain available until deleted by the user.
- Users may mark notifications as read.
- Users may delete individual notifications or all notifications.

---

# Search

- Users may search for courses, instructors, and learning paths.
- Search results may be filtered and sorted.
- Search is available to guests and authenticated users.
