# SKL — School Management Platform for Lebanese schools

A schooling platform for **Lebanese schools** with **three mobile apps** (Teacher, Student, Parent)
sharing a single backend and a shared React Native codebase.

## Lebanese context

- **Curriculum:** follows the MEHE / CRDP structure. The basic education cycles run EB1–EB9 and end with the **Brevet**. Secondary runs S1–S3 and ends with the **Lebanese Baccalaureate** (SG, SV, ES and LH tracks).
- **Grading:** marks are out of **20** and the pass mark is 10. Term averages come with a mention and a class rank.
- **School year:** three terms, with dates for Lebanese holidays such as Independence Day on 22 Nov.
- **Languages:** Arabic, French and English.
- **Fees:** in USD, payable by card, bank transfer, OMT, Whish Money or cash at the finance office.

## Prototypes

Open `index.html` to reach the clickable prototypes. Each app is one self-contained HTML file. The demo
school, **Al-Arz School** (مدرسة الأرز) in Achrafieh, Beirut, is made up. `design/index.html` shows every screen side by side.

## Features (v1)

- **Grades & report cards** — teachers record assessments; students & parents view results, GPA, report cards.
- **Attendance** — teachers mark attendance; parents are notified of absences.
- **Messaging & announcements** — direct messages and school/class announcements.
- **Schedule & homework** — timetable, class schedule, assignments with due dates & submissions.

## Architecture

```
skl/
├── backend/            Node.js + Express + Prisma + PostgreSQL (REST API, shared by all apps)
└── mobile/             React Native CLI monorepo
    ├── packages/
    │   └── shared/     Shared API client, types, auth, state, UI components
    └── apps/
        ├── teacher/    Teacher app build
        ├── student/    Student app build
        └── parent/     Parent app build
```

- **One codebase, three builds.** ~70% of the mobile code (API layer, auth, models, UI kit)
  lives in `packages/shared`. Each app in `apps/*` is a thin shell that composes shared
  screens for its role.
- **Role-based access** is enforced server-side. The same login endpoint serves all three
  apps; the JWT carries the user's role and the API authorizes every request accordingly.

## Getting started

See [`backend/README.md`](backend/README.md) to run the API, and
[`mobile/README.md`](mobile/README.md) to run the apps.

## Status

Backend: data model + auth + core APIs scaffolded. Mobile: monorepo + shared package scaffolded.
This is an in-progress build — see the checklist in each README.
