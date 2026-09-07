# Tadilo (B2C Booking Service)

Flight and hotel booking service for consumers.

- **Role:** Senior Frontend Developer (near-total frontend ownership)
- **Period:** 2022 – 2025-12
- **Relationship:** built at MIROTECH GROUP

## Overview

Tadilo is a B2C platform for searching and booking flights and hotels. I owned almost the entire frontend application and wrote nearly all of it myself; occasionally another developer implemented a small feature or isolated part, which I reviewed before merging. The flight and hotel search/booking flows were primarily my responsibility, along with the payment flow (Stripe plus regional and local payment gateways) and PWA support, making the service installable with an app-like experience on desktop and mobile.

## Responsibilities & Contributions

- Owned and implemented nearly the entire frontend application, reviewing the few outside contributions before merging
- Built the flight and hotel search and booking flows end to end
- Implemented the payment flow with Stripe and regional/local payment gateways
- Added PWA support so the service could be installed and used like a native app
- Redesigned the real-time search architecture and solved large-result rendering performance issues (see below)
- Diagnosed and helped resolve a production SSR container-communication failure (see below)

## Notable Implementation Details

- **Incremental real-time search:** flight results arrived incrementally from multiple providers, and originally the server waited for all providers before filtering and sorting, adding unnecessary delay. I proposed moving this to the frontend: each provider's available results are sent immediately over WebSocket, and the frontend accumulates incoming results and handles sorting, filtering, pagination, and infinite scrolling itself.
- **Large result sets:** a single search could return 500+ detailed flight results, and rendering that many rich cards at once caused UI performance problems. I solved this with chunked data/result handling and controlled pagination/rendering, keeping the UI responsive while results continued to arrive.
- **SSR authentication fix:** the Nuxt app needed authenticated user data during SSR, but frontend and backend ran in separate Docker containers and server-side requests between containers were rejected in production, so users appeared logged out after refresh. I diagnosed the container-communication issue and worked with the backend team to resolve it.

## Tech Stack

- Nuxt3 (SSR)
- TypeScript
- WebSocket
- REST APIs
- Pinia
- I18n
- PWA

## Related Experience

- [Senior Frontend Developer & Team Lead @ MIROTECH GROUP](../../experiences/senior-frontend-developer-team-lead-mirotech/README.md)