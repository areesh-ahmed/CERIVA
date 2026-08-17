# High-Level Design (HLD)

## 1. Introduction
Cerevia is a gamification backend designed for BYJU'S to handle large-scale concurrent users interacting with Daily Streaks and Weekly Leaderboards.

## 2. Architecture Diagram

```mermaid
flowchart TD
    USER([Student]) --> LESSON[Complete Lesson]
    LESSON --> API[Next.js API Route]
    API --> AUTH[Auth Middleware]
    AUTH --> STREAK_SVC[Streak Service]
    AUTH --> SCORE_SVC[Score Service]
    STREAK_SVC --> PG[(PostgreSQL)]
    SCORE_SVC --> PG
    SCORE_SVC --> INVALIDATE[Invalidate Redis Cache]
    CRON[Hourly Cron] --> PG
    CRON --> REDIS[(Redis Cache)]
    LEADERBOARD_PAGE[Leaderboard GET] --> REDIS
```

## 3. Tech Stack
- **Framework**: Next.js 15 (App Router)
- **Database**: PostgreSQL (with Prisma ORM)
- **Caching**: Redis
- **Security**: Helmet, Rate Limiting, JWT
