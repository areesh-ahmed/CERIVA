# Low-Level Design (LLD)

## 1. Database Schema (Prisma)

- **User**: Stores basic info and authentication details.
- **Streak**: Tracks `currentStreak`, `longestStreak`, and `lastActivityAt`.
- **WeeklyScore**: Tracks `xp` earned per week and year.
- **XpRecord**: Audit log of lessons completed.

## 2. API Endpoints
- `POST /api/lessons/[id]/complete`: Updates streak synchronously, updates XP, invalidates Redis.
- `GET /api/user/leaderboard`: Fetches ranked user list from Redis (falls back to DB if missed).

## 3. Caching Strategy (Redis)
- Cache-aside invalidation pattern.
- Key format: `leaderboard:weekly:<year>:<week>`
- On lesson complete, cache pattern is invalidated, triggering a fresh read from PostgreSQL on next fetch.
- Fallback cron job refreshes cache every hour.
