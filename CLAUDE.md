# CLAUDE.md - Scheduler-UI

## Project Overview

Scheduler-UI is the appointment scheduling frontend for the AMRIT healthcare platform. It provides telemedicine appointment management including timesheets, specialization calendar views, staff management, SMS templates, and consultation reports.

## Tech Stack

- Angular 16 (NgModule-based, not standalone)
- TypeScript 5.1
- Angular Material 16
- RxJS, zone.js
- Karma + Jasmine (testing)
- ESLint + Prettier (linting)
- Husky + commitlint (conventional commits)

## Build & Run Commands

```bash
npm install                    # Install dependencies
npm start                      # Dev server (port 4208)
npm run build-dev              # Development build
npm run build-prod             # Production build
npm run build-ci               # CI build (uses EJS template + env vars)
npm test                       # Run tests
npm run lint                   # Lint
npm run commit                 # Commitizen conventional commit
```

WAR packaging: `mvn -B package --file pom.xml -P <profile>`

Dev server port: **4208**

## Project Structure

```
src/app/
  app.module.ts                # Root module
  app-routing.module.ts        # Routes: redirin -> /telemedicine (lazy-loaded)
  redir-open/                  # Redirect/landing component
  app-modules/
    core/                      # Core module (services, material imports)
      core.module.ts
      material.module.ts       # Centralized Material imports
      services/
        auth.service.ts        # Authentication
        auth-guard.service.ts  # Route guard
        http-interceptor.service.ts
        http-service.service.ts
        confirmation.service.ts
        spinner.service.ts
    scheduler/                 # Main feature module (lazy-loaded at /telemedicine)
      dashboard/               # Main dashboard layout
      timesheet/               # Staff timesheet management
      specialization-calander-view/  # Specialization day view calendar
      appointment-view/        # View appointments
      mystaff/                 # Staff management + profile view
      sms-template/            # SMS template CRUD (create, view)
      reports/                 # Consultation reporting
        chief-complaint-report/
        total-consultation-report/
        consultation-report/
        monthly-report/
        daily-report/
      shared/                  # Shared scheduler utilities
```

## Architecture Notes

- Single lazy-loaded feature module (`SchedulerModule`) at route `/telemedicine`
- Uses hash-based routing (`useHash: true`)
- `RedirOpenComponent` handles initial redirect/authentication flow
- Dashboard component acts as shell with child routes for all features
- HTTP interceptor attaches auth headers; session timeout at 27 min (status `5002` = expired)
- i18n via custom JSON files (`src/assets/English.json`, `src/assets/Hindi.json`)
- CI environment generated from `environment.ci.ts.template` via `scripts/ci-prebuild.js`

## Commit Conventions

Conventional Commits enforced. Allowed types: `feat`, `fix`, `build`, `chore`, `ci`, `docs`, `perf`, `refactor`, `revert`, `style`, `test`. Header max 100 chars.
