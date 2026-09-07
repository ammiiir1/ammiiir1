# Easybestell (Restaurant Management App)

Restaurant order management application.

- **Period:** 2023 – 2024
- **Relationship:** built at MIROTECH GROUP

## Overview

The restaurant-side operations app of the Easybestell restaurant ordering and operations platform, where restaurants manage incoming orders from the online ordering app, with the admin panel covering platform administration. Five frontend developers worked across the ecosystem, with different developers owning different areas.

## Responsibilities & Contributions

- Frontend development on the restaurant-side order management app within the shared Easybestell platform

## Notable Implementation Details

- **Automatic ticket printing:** restaurant and kitchen tickets are narrow receipt-printer output, and normal browser printing shows a confirmation dialog — unsuitable for automatic order processing. The team designed a local printing bridge: a companion Electron app running on the restaurant's computer exposes a local server/API, the web frontend calls that local service, and the Electron app handles automatic receipt/ticket printing with no browser confirmation modal. Another developer built the Electron app; I contributed to this architecture and the frontend integration.

## Tech Stack

- Next.js (CSR)
- TypeScript
- Zustand
- I18n
- REST APIs
- Firebase
- PWA

## Related Experience

- [Senior Frontend Developer & Team Lead @ MIROTECH GROUP](../../experiences/senior-frontend-developer-team-lead-mirotech/README.md)