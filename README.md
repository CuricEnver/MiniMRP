Goal - Develop a full-stack Material Resource Planning (MRP) system designed to demonstrate complex inventory netting, automated Bill of Materials (BOM) explosion, and procurement synchronization.

Preliminary Schema for MRP system based off of generated MRP flow diagram:

![Generated MRP Flow Diagram](./docs/generated-mrp-flow-diagram.png)

![System Schema](./docs/mrp-schema-v1.png)


Part 1: Authentication & Seamless Provisioning

Users Table:

![Users Table](./docs/users-table.png)

Plan: 
Implement a stateless authentication system designed to minimize user friction through automated guest provisioning and JWT-secured sessions.

Execution:

Task - Implement Local Identity Persistance

How - Check localStorage for unique identifier (UUID) upon initialization; automatically provision a new guest identity if one is absent.

Why - This ensures frictionless "zero-touch" onboarding experience, allowing users to interact with the MRP logic immediately without filling out registration forms. 

Task - Deploy Stateless JWT Authentication

How - Issue a signed JSON Web Token (JWT) for all subsequent API requests to identify user roles and permissions.

Why - By shifting session data to a self-contained token, the backend remains stateless. This eliminates the need for server-side session tracking, enhancing scalability and maintaining a decoupled architecture.

Task - Configure a 7-Day Sliding Window for Guest Persistence

How - Set guest account expiration for 7 days, with the window resetting upon each active interaction.

Why - This balances user convenience with system maintenance. It provides guest users ample time to explore the system's inventory netting and BOM explosion features while ensuring the database is periodically cleared of inactive "orphan" data.

