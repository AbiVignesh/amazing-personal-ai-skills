# System Design Frameworks

Structured approaches for designing scalable systems. Apply these frameworks consistently to solve any design problem.

---

## High-Level Design (HLD) Framework

Use this for interview questions like "Design Instagram", "Design Uber", "Design a rate limiter".

### Step 1: Clarify Requirements (5 min)

**Functional Requirements:**
- What are the core features? (e.g., post photos, follow users, like posts)
- What are the user flows? (e.g., upload → feed → view)

**Non-Functional Requirements (often missed but critical):**
- Scale: How many users? DAU/MAU? Requests per second?
- Latency: What's acceptable? (100ms? 1s?)
- Availability: 99.9% uptime? Can we lose data?
- Consistency: Eventual consistency OK? Or strong consistency needed?
- Cost: Optimize for speed or cost or both?

**Ask clarifying questions:**
- "How many daily active users?"
- "What's the primary use case?"
- "Can reads be stale?"
- "How much data do we need to store?"

### Step 2: Estimate Scale (5 min)

**Calculations to do:**
- DAU (daily active users): How many?
- Requests per second: DAU * avg requests per user per day / 86400
- Storage per day: avg data per request * requests per day
- Bandwidth: avg data per request * requests per second

**Example (Instagram):**
- 500M DAU
- 10 requests per user per day = 58k RPS
- 1MB average per post * 5B posts/day = 5PB/day storage
- Bandwidth = 58k RPS * 1KB avg = 58GB/s (needs compression)

### Step 3: High-Level Architecture (10 min)

**Core Components:**

1. **Client Layer:**
   - Web, mobile, third-party APIs
   - May need different endpoints for different clients

2. **API Gateway:**
   - Routes requests to appropriate services
   - Handles authentication, rate limiting
   - Load balancing

3. **Service Layer (Business Logic):**
   - User service (registration, profiles)
   - Post service (create, retrieve, feed)
   - Like/comment service
   - Search service
   - Notification service

4. **Data Layer:**
   - SQL database (users, relationships)
   - NoSQL database (posts, comments)
   - Cache layer (Redis for hot data)
   - Object storage (S3 for images/videos)

5. **Messaging/Queue:**
   - Async tasks (send notifications, process images)
   - Event streaming (Kafka for feed updates)

6. **Monitoring/Logging:**
   - Centralized logging
   - Metrics and alerts

**Draw a simple diagram:**
```
Client → API Gateway → Services → Database
                    ↓
                  Cache
                    ↓
                  Queue → Workers
```

### Step 4: Design Data Model (5 min)

**For each entity:**

```
User:
  - user_id (PK)
  - username
  - email
  - created_at

Post:
  - post_id (PK)
  - user_id (FK)
  - content
  - image_url
  - created_at
  - likes_count (denormalized for speed)

Like:
  - like_id (PK)
  - post_id (FK)
  - user_id (FK)
  - created_at

Feed:
  - user_id (PK)
  - post_ids (list, ordered by time)
  - updated_at
```

**Denormalization:** When to duplicate data for speed?
- Trade storage for read speed
- Example: Store `likes_count` in Post instead of counting every time

### Step 5: Deep Dive into Critical Flows (10 min)

**Pick the bottleneck flow:**

**Feed Generation Flow:**
1. User requests feed → API Gateway
2. Fetch followed user IDs from User Service
3. Fetch latest posts from Post Service (from followed users)
4. Sort by timestamp
5. Add like counts, user avatars
6. Return to client

**Optimization:**
- Cache feed for 1 minute (acceptable staleness?)
- Pre-generate feeds using batch jobs (push model vs pull model)
- Use indexing (post_id, user_id, created_at)

### Step 6: Handle Tradeoffs (5 min)

**Key decisions:**

| Decision | Choice A | Choice B | Tradeoff |
|----------|----------|----------|----------|
| **Data consistency** | Strong (immediate) | Eventual (10s delay) | Latency vs complexity |
| **Feed generation** | Pull (on-demand) | Push (precomputed) | Read latency vs write load |
| **Caching strategy** | Cache everything | Cache hot data only | Memory vs hit rate |
| **Database type** | SQL (relational) | NoSQL (fast writes) | Consistency vs speed |

**Example reasoning:**
- Feed can be eventually consistent (users accept 10-30s delay)
- Use push model for feed (Twitter/Meta approach)
- Cache hot data (trending posts)
- SQL for user relationships, NoSQL for posts

### Step 7: Handle Failure Modes (3 min)

**What breaks?**
- Database goes down → use read replicas + failover
- API gateway overloaded → auto-scale
- Cache miss → fallback to database (with rate limiting)
- Message queue backlog → scale workers

### Step 8: Discuss Monitoring (2 min)

- Metrics: Latency, QPS, error rate, cache hit rate
- Alerts: p99 latency > 1s, error rate > 1%
- Dashboards: Real-time system health

---

## Low-Level Design (LLD) Framework

Use this for "Design parking lot", "Design library system", "Design a cache".

### Step 1: Clarify Requirements

**Functional:**
- What are the core operations? (add, remove, search, etc.)
- What objects are involved?
- What are the workflows?

**Non-Functional:**
- Concurrency: Multiple threads?
- Size limits: How many objects?
- Performance: Real-time constraints?

### Step 2: Identify Core Classes

**For each class:**

```python
class User:
    def __init__(self, user_id, name, email):
        self.user_id = user_id
        self.name = name
        self.email = email
    
    def get_profile(self):
        pass
    
    def update_profile(self, name, email):
        pass
```

### Step 3: Model Relationships

- 1-to-1: User has one Profile
- 1-to-N: User has many Posts
- M-to-N: User follows many Users, followed by many Users

### Step 4: Design Methods

**For each operation:**
- Input/output
- Time/space complexity
- Edge cases

### Step 5: Handle Concurrency

**If multiple threads:**
- Use locks/mutexes for shared state
- Use thread-safe collections
- Avoid deadlocks (consistent lock ordering)

### Step 6: Error Handling

- Invalid input
- State conflicts
- Resource exhaustion

---

## Common System Design Patterns

### 1. Caching (Improve Read Performance)

**Strategies:**
- **Cache-aside:** Check cache, miss → fetch from DB
- **Write-through:** Write to cache and DB together
- **Write-behind:** Write to cache, async write to DB

**When to use:**
- Hot data (trending posts, user profiles)
- Expensive computations (feed generation)

**Tools:** Redis, Memcached

### 2. Replication (Improve Availability)

**Master-slave:** Writes to master, reads from slaves
**Multi-master:** Multiple nodes can accept writes

**Use when:** Need high availability, geographical distribution

### 3. Sharding (Handle Scale)

**Sharding key:** Distribute data by user_id, region, timestamp
**Hotspot:** One shard overloaded → need better key or rebalancing

**Use when:** Data too large for one database

### 4. Message Queue (Decouple Services)

**Producer-consumer:** Services communicate via queue
**Buffering:** Handle traffic spikes
**Async processing:** Long-running tasks don't block

**Tools:** RabbitMQ, Kafka, SQS

### 5. Load Balancing

**Round-robin:** Send requests to servers in order
**Least connections:** Send to least busy server
**Geo-routing:** Send to nearest server

### 6. CDN (Reduce Latency)

**Edge servers:** Cache content geographically
**Use when:** Global audience, large static content

### 7. Database Indexing

**B-tree index:** Fast lookups on columns
**Hash index:** O(1) lookups
**Covering index:** All query data in index

---

## Communication Tips During Interview

**Good:**
- "Let me draw the architecture" → use ASCII art
- "The bottleneck here is..." → identify specific issue
- "I would trade X for Y because..." → explain reasoning
- "Let me estimate the scale" → back-of-envelope math

**Bad:**
- Jumping to implementation details too early
- Not asking clarifying questions
- Designing for impossible scale
- Ignoring non-functional requirements

---

## Example: Design Instagram

### Clarification
- 500M DAU, 10M new posts/day, strong consistency for relationships
- Read-heavy (100:1 read:write)
- Latency: feed should load in 1-2 seconds
- Can tolerate 30 second eventual consistency for likes

### Estimation
- 500M users, 10M posts/day = 115 RPS
- Average post size: 100B metadata + 2MB image = 20B posts/day = 200PB
- Users follow 200 users on average

### Architecture
```
Client (mobile/web)
  ↓
API Gateway (auth, routing, rate limiting)
  ↓
Services:
  - User Service (profiles, follow relationships)
  - Post Service (create, retrieve posts)
  - Feed Service (generate personalized feeds)
  - Search Service (find users, posts)
  ↓
Data:
  - MySQL: Users, relationships, metadata
  - Cassandra: Posts (distributed, high write throughput)
  - Redis: Cache for hot data, feed cache
  - S3: Image storage
  ↓
Queue: Kafka for async tasks
Workers: Image processing, notification delivery
```

### Data Model
- Users table: user_id, name, email, created_at
- Follows table: follower_id, following_id (index on both)
- Posts table: post_id, user_id, content, image_url, created_at, likes_count
- Likes table: like_id, post_id, user_id, created_at (time-series database)

### Feed Generation
1. Get followed users: FROM Follows WHERE follower_id = ?
2. Get posts: FROM Posts WHERE user_id IN (followed_users) ORDER BY created_at DESC LIMIT 20
3. Add user info, like counts
4. Cache for 30 seconds

Optimization: Pre-generate feeds using push model (update when someone posts)

### Scaling
- Sharding by user_id: ensures related data on same shard
- Replication: Read replicas for followers
- Caching: Cache hot posts, trending data
- CDN: Serve images from CDN

