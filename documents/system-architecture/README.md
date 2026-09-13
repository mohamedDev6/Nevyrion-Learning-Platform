# System Architecture

## Overview

Nevyrion Learning follows a separated frontend and backend architecture.

The learner-facing interface is developed using React, while Strapi is used as the backend API and administrative interface.

The system uses a relational database to store platform data.

## Architecture Diagram

The system consists of three main components:

- React Frontend
- Strapi
- Database

### Communication Flow

```text
React Frontend
   │
   │ API Requests / Responses
   ▼
Strapi
   │
   ▼
Database
```
