# Asan Service

Warranty and guarantee service web application with a blog website, built solo across the full stack.

- **Role:** Full-Stack Developer
- **Period:** 2020 – 2021
- **Relationship:** client work at Danak Corporation

## Overview

Asan Service is a warranty-request system built around an existing internal inventory and warranty-management application that the company exposed via a web service. My application retrieved available parts from that web service, stored warranty-request forms in its own database, and also posted warranty requests to the internal system, storing the external reference returned by the web service locally so records stayed linked across both systems.

I worked independently across the frontend and backend: database schema design, backend API routes and business logic, the frontend UI, registration and login, and printable invoices.

## Responsibilities & Contributions

- Designed the database schema and implemented backend API routes and business logic
- Built the frontend UI, including registration/login and printable invoices
- Integrated with the company's existing internal inventory/warranty web service to retrieve available parts
- Posted warranty requests to the internal system in addition to storing them locally
- Stored the internal system's returned reference locally so records stayed linked across both systems

## Notable Implementation Details

- **Cross-system record synchronization:** every warranty request existed both in this app's own database and in the company's internal system; the app stored the internal system's reference per request, keeping the two systems' records linked.

## Tech Stack

- Nuxt.js (SSR)
- Vuex
- Express.js
- MongoDB
- Mongoose.js
- Socket.io
- REST APIs
- PWA

## Related Experience

- [Chief Technology Officer @ Danak Corporation](../../experiences/chief-technology-officer-danak-corporation/README.md) — period spans the CTO role
- [Full-Stack Developer @ Danak Corporation](../../experiences/full-stack-developer-danak-corporation/README.md) — period spans the Full-Stack Developer role