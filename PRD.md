# Product Requirements Document (PRD)

## Product Name
Cerevia (BYJU'S Gamification System)

## 1. Objective
To build a scalable, production-grade gamification system for BYJU'S to power daily learning streaks and weekly competitive leaderboards at scale, improving student engagement and retention.

## 2. Target Audience
Students on the BYJU'S platform.

## 3. Core Features
1. **Daily Streaks**: A streak representing consecutive days a student completes at least one lesson.
2. **Weekly Leaderboard**: Real-time weekly score updates, with cached read-heavy leaderboard view.

## 4. Non-Functional Requirements
- **High Availability & Low Latency**: Write operations must be immediate. Read operations can tolerate caching.
- **Scalability**: Handle high concurrent requests using Redis.
- **Security**: Robust rate limiting, CORS policies, XSS mitigation, JWT authentication.
