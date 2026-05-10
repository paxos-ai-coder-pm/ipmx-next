# IPMX Digital Ecosystem Blueprint
## Ultra-Granular Enterprise-Grade LLM Engineering Specification
### For the IPMX Programme at Indian Institute of Management Lucknow

---

# 1. SYSTEM VISION

## 1.1 Product Identity

The platform is not merely a college website, ERP, or social network.

It is a:

- Professional executive collaboration ecosystem
- Academic operations platform
- Career acceleration system
- Networking infrastructure
- Community operating system
- Alumni continuity engine
- Institutional memory layer

The system should behave like a unified enterprise platform specifically optimized for executive MBA users.

The emotional experience should communicate:

| Attribute | Desired Feeling |
|---|---|
| Professionalism | “This feels premium.” |
| Speed | “I can get information instantly.” |
| Prestige | “This reflects the IIM brand.” |
| Community | “I belong here.” |
| Reliability | “This system never fails me.” |
| Networking | “This platform increases my opportunities.” |
| Continuity | “This stays valuable after graduation.” |

---

## 1.2 Product Philosophy

The product philosophy should influence every engineering decision.

The platform should optimize for:

### A. Cognitive Efficiency

Users are busy professionals.

The system must reduce:

- Decision fatigue
- Navigation friction
- Information overload
- Repetitive actions
- Context switching

Engineering implications:

- Fewer clicks
- Better defaults
- Strong search
- Smart suggestions
- Persistent context memory

---

### B. High Information Density Without Chaos

MBA ecosystems generate large volumes of information.

Examples:

- Timetable changes
- Placement updates
- Group discussions
- Club events
- Academic resources
- Case competition announcements
- Networking opportunities

The UI must display large amounts of information while preserving clarity.

Engineering implications:

- Progressive disclosure
- Collapsible sections
- Information hierarchy
- Priority tagging
- Contextual surfacing

---

### C. Professional Identity Preservation

Every user profile should evolve into a long-term professional identity.

The profile should become richer over time through:

- Participation history
- Leadership roles
- Club involvement
- Placement outcomes
- Alumni achievements
- Contributions to discussions

The system must never feel disposable or temporary.

---

### D. Institutional Memory

The platform should preserve institutional history.

Examples:

- Historical events
- Past leadership talks
- Alumni stories
- Club archives
- Batch traditions
- International immersion memories

The platform becomes the institutional memory layer of the IPMX ecosystem.

---

# 2. USER ECOSYSTEM ANALYSIS

## 2.1 User Archetypes

The system must support multiple psychological and professional archetypes.

### Archetype 1 — Career Switcher

Characteristics:

- Uses placement portal heavily
- Actively seeks networking
- Frequently accesses alumni directory
- Participates in interview discussions

Needs:

- Mentorship
- Resume feedback
- Domain-transition guidance
- Industry discovery

System implications:

- Strong alumni search
- Anonymous placement discussions
- Smart recommendation engine

---

### Archetype 2 — Senior Industry Leader

Characteristics:

- High work experience
- Less active socially
- Uses platform primarily for efficiency

Needs:

- Fast communication
- Minimal friction
- High-quality discussions

System implications:

- Dense dashboard
- Shortcut navigation
- Efficient notifications

---

### Archetype 3 — Community Builder

Characteristics:

- Organizes clubs/events
- Creates discussions
- Coordinates activities

Needs:

- Group management tools
- Polling systems
- Event workflows
- Member management

System implications:

- Advanced moderator tooling
- Analytics for engagement
- Group administration capabilities

---

### Archetype 4 — Academic Performer

Characteristics:

- Heavy academic participation
- Uses forums extensively
- Shares resources

Needs:

- Structured discussions
- Resource organization
- Academic searchability

System implications:

- Rich forums
- Tag systems
- Knowledge indexing

---

# 3. SYSTEM ARCHITECTURE

## 3.1 Macro Architecture

```text
User Device
    ↓
CDN Layer
    ↓
Frontend Application
    ↓
API Gateway
    ↓
Authentication Layer
    ↓
Authorization Layer
    ↓
Business Logic Layer
    ↓
Database Layer
    ↓
Storage + Realtime + Queue Systems
```

---

## 3.2 Architectural Principles

### Principle 1 — Separation of Concerns

Every layer should have a single responsibility.

Examples:

| Layer | Responsibility |
|---|---|
| Frontend | UI rendering |
| API Layer | Request orchestration |
| Services | Business logic |
| Database | Persistence |
| Storage | Media delivery |

Never mix responsibilities.

---

### Principle 2 — Stateless Backend

APIs should remain stateless.

Benefits:

- Horizontal scalability
- Easier deployment
- Better reliability
- Simplified recovery

---

### Principle 3 — Event-Driven Updates

Realtime updates should be event-driven rather than polling-heavy.

Examples:

- New notice created
- Timetable updated
- Placement deadline added
- Group announcement published

Use subscriptions instead of refresh-based systems.

---

### Principle 4 — Defensive Architecture

Assume:

- Invalid user input
- Malicious uploads
- API abuse
- Permission escalation attempts
- Network instability

All systems must fail safely.

---

# 4. DATABASE ENGINEERING

## 4.1 Database Philosophy

The database must optimize for:

- Security
- Relational integrity
- Query performance
- Flexibility
- Long-term maintainability

---

## 4.2 Primary Database Design Rules

### Rule 1 — UUID Everywhere

Every entity must use UUID primary keys.

Reasoning:

- Prevent enumeration attacks
- Improve distributed scalability
- Reduce predictability

Never use auto-increment IDs for public-facing entities.

---

### Rule 2 — Soft Delete Critical Data

Important entities should use soft deletion.

Examples:

- Posts
- Threads
- Media
- Events

Reasoning:

- Auditability
- Recovery
- Moderation rollback

---

### Rule 3 — Immutable Audit Logs

Critical actions should generate immutable logs.

Examples:

- Role changes
- User bans
- Placement data modifications
- Timetable edits

---

### Rule 4 — Explicit Relationship Mapping

Never rely on inferred relationships.

Every many-to-many relationship requires a junction table.

Examples:

```text
group_members
event_attendees
thread_upvotes
user_connections
```

---

# 5. AUTHENTICATION & AUTHORIZATION

## 5.1 Security Philosophy

Security must be treated as a foundational architecture concern, not a later enhancement.

The system should assume:

- Attack attempts will happen
- Users may misuse permissions
- Tokens may leak
- Spam may occur
- Fake accounts may be created

---

## 5.2 Authentication Methods

Supported methods:

| Method | Purpose |
|---|---|
| Email/password | Default authentication |
| Google OAuth | Frictionless onboarding |
| Magic links | Recovery workflow |

---

## 5.3 Session Security

Requirements:

- Secure JWT storage
- Token expiration
- Silent refresh
- Device revocation
- Multi-device awareness

---

# 6. DASHBOARD ENGINEERING

## 6.1 Dashboard Philosophy

The dashboard is the operational nerve center.

Users should understand their entire day within 5 seconds.

The dashboard should answer:

- What changed?
- What requires attention?
- What is urgent?
- What is upcoming?
- What affects me personally?

---

## 6.2 Feed Ranking System

The feed should not be purely chronological.

Instead use weighted ranking.

### Ranking Factors

| Factor | Weight Impact |
|---|---|
| Pinned notice | Very high |
| Placement deadline | Very high |
| CR announcement | High |
| Group relevance | High |
| User interaction history | Medium |
| Recency | Medium |
| Popularity | Low |

---

# 7. PROFILE SYSTEM ENGINEERING

## 7.1 Identity Philosophy

Profiles are professional identity containers.

The profile must communicate:

- Competence
- Experience
- Credibility
- Expertise
- Leadership

---

## 7.2 Profile Data Model

### Static Information

Rarely changes.

Examples:

- Name
- Batch
- Roll number

---

### Dynamic Information

Changes often.

Examples:

- Bio
- Interests
- Placement status
- Club involvement

---

### Historical Information

Accumulates over time.

Examples:

- Past roles
- Event participation
- Leadership positions

---

# 8. GROUP SYSTEM ENGINEERING

## 8.1 Group Philosophy

Groups are foundational community primitives.

The platform should support hundreds of active subcommunities without becoming chaotic.

---

## 8.2 Group Lifecycle

```text
Create
→ Pending Approval
→ Approved
→ Active
→ Archived
```

---

## 8.3 Group Governance

Groups require moderation layers.

Roles inside groups:

| Role | Capabilities |
|---|---|
| Owner | Full control |
| Moderator | Content moderation |
| Member | Participation |
| Visitor | Read-only |

---

# 9. FORUM ENGINEERING

## 9.1 Forum Philosophy

Forums are long-form knowledge systems.

Unlike feeds:

- Content remains valuable longer
- Discoverability matters heavily
- Searchability is critical

---

## 9.2 Thread Lifecycle

```text
Created
→ Active Discussion
→ Solved
→ Archived
```

---

# 10. MEDIA SYSTEM ENGINEERING

## 10.1 Media Philosophy

Media is essential for emotional engagement and culture preservation.

Without media, the platform becomes transactional rather than communal.

---

## 10.2 Upload Pipeline

```text
Upload
→ MIME validation
→ Virus scan
→ Compression
→ Thumbnail generation
→ Metadata extraction
→ Storage
→ CDN propagation
```

---

# 11. TIMETABLE ENGINEERING

## 11.1 Mission-Critical Nature

The timetable system directly affects daily operations.

Downtime or incorrect data causes operational disruption.

---

## 11.2 Scheduling Constraints

Must support:

- Overlapping sections
- Faculty conflicts
- Room conflicts
- Holiday overrides
- Recurring schedules

---

# 12. PLACEMENT SYSTEM ENGINEERING

## 12.1 Placement Sensitivity

Placement workflows are highly confidential.

Potential risks:

- Compensation leakage
- Reputation damage
- Competitive intelligence exposure

---

## 12.2 Anonymous Posting System

Anonymous contributions must:

- Hide author identity publicly
- Preserve internal moderation traceability

Therefore:

```text
Public anonymity
≠
True database anonymity
```

Moderators should retain internal visibility.

---

# 13. REALTIME SYSTEM ENGINEERING

## 13.1 Realtime Philosophy

Realtime should improve responsiveness without overwhelming infrastructure.

---

## 13.2 Realtime Use Cases

Use realtime only where necessary.

Examples:

| Use Case | Realtime Needed? |
|---|---|
| Timetable changes | Yes |
| New likes | Optional |
| Placement alerts | Yes |
| Comments | Yes |
| Profile edits | No |

---

# 14. SEARCH ENGINEERING

## 14.1 Search Philosophy

Search becomes more important as institutional memory grows.

---

## 14.2 Search Features

Must support:

- Typo tolerance
- Semantic ranking
- Tag filters
- Recent searches
- Personalized ranking

---

# 15. NOTIFICATION ENGINEERING

## 15.1 Notification Philosophy

Notifications should reduce uncertainty, not create distraction.

---

## 15.2 Notification Delivery Channels

Support:

- In-app
- Email
- Push notifications
- SMS (future)

---

# 16. DEVOPS & INFRASTRUCTURE

## 16.1 Deployment Philosophy

Deployments must be:

- Fast
- Reversible
- Observable
- Reliable

---

## 16.2 Infrastructure Components

```text
Frontend Hosting
Database
Storage
CDN
Realtime Infrastructure
Background Job Queue
Monitoring
Logging
Analytics
```

---

# 17. SCALABILITY STRATEGY

## 17.1 Future Expansion Possibilities

Potential future growth:

- Multi-programme support
- Multi-campus support
- Cross-IIM collaboration
- Executive education expansion

---

## 17.2 Scalability Requirements

The architecture should tolerate:

- 10x user growth
- 100x media growth
- Large historical archives
- Heavy realtime traffic

---

# 18. ENGINEERING GOVERNANCE

## 18.1 Code Quality Standards

Mandatory:

- Type safety
- Unit testing
- Modular architecture
- Reusable components
- Documentation

---

## 18.2 Pull Request Standards

Every PR should include:

- Description
- Screenshots
- Test evidence
- Performance notes

---

## 18.3 Testing Strategy

Testing layers:

| Type | Purpose |
|---|---|
| Unit | Logic validation |
| Integration | Service interaction |
| E2E | User workflow |
| Load | Scalability |
| Security | Vulnerability detection |

---

# 19. LONG-TERM PRODUCT EVOLUTION

## 19.1 Future AI Features

Potential future integrations:

- AI-powered networking recommendations
- Resume analysis
- Intelligent search
- Smart event recommendations
- Academic summarization

---

## 19.2 Future Mobile App

Potential native app features:

- Offline caching
- Push-first workflows
- Event QR scanning
- Campus navigation

---

# 20. FINAL PRODUCT OUTCOME

The final product should feel like:

> “A premium enterprise-grade executive MBA operating system purpose-built for the IPMX ecosystem at IIM Lucknow.”

The platform should ultimately become:

- The operational layer of the programme
- The networking layer of the batch
- The memory layer of the institution
- The professional graph of the alumni ecosystem
- The collaboration infrastructure of the IPMX community

