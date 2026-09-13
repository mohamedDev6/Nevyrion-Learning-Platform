# Product Decisions

This document records important architectural and product decisions made during the design of Nevyrion Learning.

Each decision explains why it was made and how it affects the product.

---

## Academic MVP Scope

### Status

Accepted

### Context

The project is developed as an Academic MVP with limited development time.

### Decision

Focus only on the core learning experience and postpone non-essential features.

### Consequences

#### Positive

- Keeps development manageable.
- Delivers the core product vision.
- Reduces implementation complexity.

#### Negative

- Some engagement features are postponed.

---

## Course Approval Workflow

### Status

Accepted

### Context

Allowing instructors to publish courses directly may reduce content quality.

### Decision

Every newly created course must be reviewed and approved by an administrator before publication.

### Consequences

#### Positive

- Maintains content quality.
- Prevents inappropriate or incomplete courses.

#### Negative

- Publishing courses may take additional time.

---

## Learning Paths as a Core Feature

### Status

Accepted

### Context

The primary problem Nevyrion Learning solves is helping learners follow a structured learning journey.

### Decision

Learning Paths are considered one of the platform's primary features.

### Consequences

#### Positive

- Differentiates the platform.
- Provides clear learning roadmaps.
- Reduces learner confusion.

#### Negative

- Requires additional planning and maintenance.

---

## Free Course Preview

### Status

Accepted

### Context

Learners often want to evaluate a course before enrolling.

### Decision

Allow free preview lessons before course enrollment.

### Consequences

#### Positive

- Increases learner confidence.
- Improves enrollment decisions.

#### Negative

- Requires instructors to select preview lessons.

---

## Guest Access

### Status

Accepted

### Context

Visitors should be able to explore the platform before creating an account.

### Decision

Guests may browse courses and learning paths but cannot enroll, review courses, or access protected learning content.

### Consequences

#### Positive

- Encourages user registration.
- Allows visitors to evaluate the platform.

#### Negative

- Some platform features remain inaccessible to guests.

---

## Community Features

### Status

Accepted

### Context

Community functionality increases development complexity and is not essential for the first release.

### Decision

Postpone community features to Version 2.

### Consequences

#### Positive

- Keeps the MVP focused.
- Reduces implementation time.

#### Negative

- Learners cannot interact within the platform initially.

---

## Instructor Marketplace

### Status

Accepted

### Context

Allowing anyone to publish courses may reduce educational quality during the early stages.

### Decision

Instructor Marketplace is excluded from the Academic MVP.

### Consequences

#### Positive

- Ensures higher content quality.
- Simplifies platform management.

#### Negative

- Instructor onboarding is managed manually.

---

## Gamification

### Status

Accepted

### Context

Gamification improves engagement but is not essential for validating the platform's core value.

### Decision

Exclude advanced gamification features from the Academic MVP.

### Consequences

#### Positive

- Reduces development complexity.
- Allows focus on learning quality.

#### Negative

- Lower engagement compared to future versions.

---

## AI Features

### Status

Accepted

### Context

AI-powered learning assistance introduces significant technical complexity.

### Decision

AI features are excluded from the Academic MVP.

### Consequences

#### Positive

- Simplifies development.
- Keeps the product focused on its core value.

#### Negative

- Personalized AI assistance is unavailable.

---

## Strapi Administration Panel

### Status

Accepted

### Context

Strapi already provides a mature administration interface for managing content, users, permissions, and platform resources.

Building a custom administration dashboard would duplicate existing functionality without providing additional value for the Academic MVP.

### Decision

Use Strapi's built-in Administration Panel for all administrative operations.

A custom Admin Dashboard is intentionally excluded from the Academic MVP.

### Consequences

#### Positive

- Reduces development time.
- Reuses a secure and mature administration interface.
- Allows development efforts to focus on learner and instructor experiences.

#### Negative

- The administration interface follows Strapi's design rather than Nevyrion's branding.
- Future platform-specific administration features may require customization.

---

## Unified Platform Navigation

### Status

Accepted

### Context

Many learning platforms separate the public website from the user dashboard,
creating an inconsistent experience and making it difficult for users to navigate between learning and browsing.

### Decision

Use a unified navigation system across public pages and authenticated dashboards,
allowing users to move seamlessly between all platform sections.

### Consequences

#### Positive

- Creates a consistent user experience.
- Improves navigation across the platform.
- Makes discovering new courses easier while learning.

#### Negative

- Requires a more flexible navigation design for different user roles.

---

## Unified Platform Navigation

### Status

Accepted

### Context

Many learning platforms separate the public website from the user dashboard,
creating an inconsistent experience and making it difficult for users to navigate between learning and browsing.

### Decision

Use a unified navigation system across public pages and authenticated dashboards,
allowing users to move seamlessly between all platform sections.

### Consequences

#### Positive

- Creates a consistent user experience.
- Improves navigation across the platform.
- Makes discovering new courses easier while learning.

#### Negative

- Requires a more flexible navigation design for different user roles.
