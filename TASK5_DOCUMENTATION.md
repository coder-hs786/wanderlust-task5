# Task 5: Docker Multi-Stage, Hardening & Deployment

## 1. Objective

The objective of Task 5 was to containerize the Wanderlust full-stack application using optimized multi-stage Docker builds, apply basic container hardening, run services using non-root users, publish Docker images to multiple container registries, and verify the complete application deployment.

---

## 2. Docker Multi-Stage Build

Multi-stage Docker builds were implemented for the frontend and backend applications.

### Frontend

The frontend uses,

- Node.js build stage
- Nginx runtime stage
- Production build generated using Vite
- Development dependencies excluded from the final runtime image

### Backend

The backend uses:

- Node.js build stage
- TypeScript compilation
- Separate production runtime stage
- Unnecessary build files and dependencies excluded from the final runtime image

---

## 3. Container Hardening

Basic container hardening practices were applied.

### Non-root execution

The application containers were configured to run as a non-root user.

Verification:

```bash
docker exec wanderlust-backend whoami


##Google OAuth Configuration

The backend uses Passport Google OAuth.

The following environment variables are required:

GOOGLE_CLIENT_ID
GOOGLE_CLIENT_SECRET

##The OAuth callback endpoint is:

/api/auth/google/callback
