# Arak Rail

Industrial steel-grating business website with a custom backend engineering calculator for grating design and weight — turning a conventional catalog site into a practical calculation tool.

- **Role:** Full-Stack Developer
- **Period:** 2019 – 2019
- **Relationship:** client work at Danak Corporation

## Overview

Arak Rail started as a conventional industrial business website and catalog, but its centerpiece is a custom backend engineering calculator for industrial steel grating (forged grating and press-locked/pressured grating). Users enter a configuration — bearing bar height/thickness/pitch, cross bar height/thickness/pitch where applicable, and clear span — along with a load scenario: either custom load input (concentrated/point load or distributed load) or predefined classified vehicle-load scenarios (Class 1–4, FL1–FL6). The backend validates allowed parameter combinations per configuration and runs the calculations: standard and galvanized grating weight, structural stress, deflection, and validation of the result against allowable stress and allowable deflection (span-based) limits.

The result is more than weight estimation: the tool evaluates whether a chosen configuration stays within the implemented structural limits for the chosen load scenario.

## Responsibilities & Contributions

- Built the full calculation stack: backend validation of allowed parameter combinations, the calculation engine, and the frontend interface
- Implemented the calculation engine covering standard and galvanized grating weight, structural stress, and deflection
- Implemented allowable-stress and allowable-deflection validation (stress against threshold, deflection against a span-based limit)
- Supported both custom load input (concentrated/point, distributed) and predefined vehicle-load scenarios (Class 1–4, FL1–FL6)

## Tech Stack

- Nuxt.js (SSR)
- Vuex
- Express.js
- MongoDB
- Mongoose.js
- PWA
- REST APIs

## Related Experience

- [Full-Stack Developer @ Danak Corporation](../../experiences/full-stack-developer-danak-corporation/README.md)