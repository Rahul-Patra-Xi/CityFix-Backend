## CityFix-Backend
This README reflects the current repository state and gives recommended next steps if you want a proper backend.

## Project summary
CityFix is an application to report and track city infrastructure issues (potholes, streetlight outages, waste, etc.). The code currently in this repository implements a single-file React application (App.js) that provides UI and client-side logic to create and persist reports in the browser (localStorage). A firebase.js file is included.

## What’s in this repo now
- App.js — a React component that implements the CityFix UI and client-side logic (state management, localStorage persistence, image handling, admin flows, etc.)
- firebase.js — a file with Firebase initialization / helper code for connecting to Firebase services.

## Key behaviors implemented in App.js
- Creates and stores user id in localStorage (per-browser).
- Persists reports to localStorage and keeps them across reloads.
- Allows creating reports with title, description, location text, photo URL, coordinates.
- Provides separate views and flows for citizens and admin (basic admin toggles / password flow handled client-side).
- Includes image preview and simple camera support (if browser supports getUserMedia).
- The component appears to use react-icons and other common React APIs.

## Tech stack (current)
- UI: React (single-file React component)
- Persistence: Browser localStorage by default
- Optional integration: Firebase (firebase.js included)
- UI icons: react-icons (App.js references icon components)

## How to run the current UI locally
There is no build system in the repo as-is, so the easiest ways to run App.js are:

1. Create a new CRA project (if you don't have one):
   npx create-react-app cityfix-front
   cd cityfix-front

2. Replace src/App.js with the App.js file from this repo and add firebase.js to src/ (copy file contents).

3. Install any missing peer dependencies used by the component, for example:
   npm install react-icons

4. Start dev server:
   npm start
   Open http://localhost:3000


## Firebase integration
firebase.js is included to allow optional migration from localStorage to Firebase (Firestore / Realtime DB / Storage). To enable:
1. Create a Firebase project and a Web app in the Firebase console.
2. Copy the Firebase config values into firebase.js (or an environment-based wrapper).


API endpoints (examples to implement in a backend)
- POST /api/reports — create a report (multipart for photo)
- GET /api/reports — list reports (filtering, paging)
- GET /api/reports/:id — get single report
- PATCH /api/reports/:id — update status, assign staff
- POST /api/auth/login — admin/city staff login
- POST /api/uploads — upload photos (or use pre-signed S3 URLs)


## Contributing
- If you want to convert this repo into a full-stack project, consider opening issues for:
  - Adding a backend template
  - Integrating Firestore as the persistent store
  - Moving App.js into a proper front-end project with a build pipeline
- Make a fork, create a feature branch, add tests and documentation, and open a PR.

## Contact
- Maintainer: Rahul-Patra-Xi (repository owner)

---
