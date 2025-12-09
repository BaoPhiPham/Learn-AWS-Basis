---
title: "Week 13 Worklog"
date: 2025-12-01
weight: 13
chapter: false
pre: " <b> 1.13. </b> "
---

### Week 13 Goals:

- Integrate Backend (API Gateway).
- Implement Realtime Chat (AppSync).

### Tasks for this week:

| **Day** | **Task**                                                                                                                                | **Start**  | **Finish** | **References**                 |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------- | ------------------------------ |
| 2       | - Connect REST API Gateway.<br>- Handle CORS errors.                                                                                    | 02/12/2025 | 02/12/2025 | CORS Docs<br>Axios Docs        |
| 3       | - Integrate Student CRUD:<br>&emsp;+ Create<br>&emsp;+ Read<br>&emsp;+ Update<br>&emsp;+ Delete<br>- Implement loading/error UI states. | 03/12/2025 | 03/12/2025 | React Query Docs               |
| 4       | - **Main Focus:** Integrate **AWS AppSync**.<br>- Configure GraphQL Client.<br>- Write Query/Mutation for Chat.                         | 04/12/2025 | 04/12/2025 | Amplify GraphQL<br>AWS AppSync |
| 5       | - Implement GraphQL Subscription (Realtime).<br>- Test successfully: User A sends → User B receives instantly.                          | 05/12/2025 | 05/12/2025 | GraphQL Subscriptions          |
| 6       | - Refactor Frontend code.<br>- Optimize performance.<br>- Write code documentation.                                                     | 06/12/2025 | 06/12/2025 | React Performance              |

### Week 13 Outcomes:

**1. Successful API Integration:**

- Connected Frontend with Backend REST APIs.
- Fixed CORS issues with Backend collaboration.
- Built Axios API service with JWT auto-injection.
- Implemented loading spinners and error notifications.

**2. Completed Student CRUD Interface:**

- Built forms with validation.
- Display student list with pagination and search.
- Implemented delete with confirmation modal.
- Used React Query for caching and auto-refresh.

**3. Completed Realtime Chat Integration:**

- Configured GraphQL Client for AppSync.
- Built Query, Mutation, and Subscription.
- Successfully tested realtime chat between 2 users.

**4. Learned:**

- How to integrate REST and GraphQL APIs.
- When to choose REST (CRUD) vs GraphQL (Realtime).
- API debugging using DevTools.
- Collaborating with Backend to solve CORS & E2E test.

---
