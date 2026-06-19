# CarePulse — Healthcare Patient Management System

A Next.js application for managing patient registration and appointment scheduling, with an admin dashboard for confirming, scheduling, and canceling appointments.

## Tech Stack

- [Next.js 14](https://nextjs.org/) (App Router) + TypeScript
- [Appwrite](https://appwrite.io/) — auth, database, file storage
- [Tailwind CSS](https://tailwindcss.com/) + [shadcn/ui](https://ui.shadcn.com/)
- [Twilio](https://www.twilio.com/) — SMS notifications
- [Sentry](https://sentry.io/) — error and performance monitoring
- [React Hook Form](https://react-hook-form.com/) + [Zod](https://zod.dev/) — form handling and validation

## Features

- Patient registration with personal, medical, and identification details
- File upload for identification documents (Appwrite Storage)
- Appointment booking with a chosen physician
- Admin dashboard to view, schedule/confirm, and cancel appointments
- SMS notifications on appointment confirmation/cancellation
- Passkey-protected admin access
- Responsive UI with light/dark theming

## Project Structure

```
app/
  admin/           Admin dashboard
  api/             API routes
  patients/        Patient registration & appointment flows
components/        UI components, forms, modals, tables
lib/
  actions/         Server actions (patient/appointment CRUD)
  appwrite.config.ts  Appwrite SDK client setup
  validation.ts    Zod schemas
constants/         Static data (doctors, options, defaults)
types/             Shared TypeScript types
```

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v18+)
- An [Appwrite](https://appwrite.io/) project (cloud or self-hosted)
- A [Twilio](https://www.twilio.com/) account (for SMS notifications)

### Installation

```bash
npm install
```

### Environment Variables

Create a `.env.local` file in the project root:

```env
# Appwrite
NEXT_PUBLIC_ENDPOINT=https://cloud.appwrite.io/v1
PROJECT_ID=
API_KEY=
DATABASE_ID=
PATIENT_COLLECTION_ID=
DOCTOR_COLLECTION_ID=
APPOINTMENT_COLLECTION_ID=
NEXT_PUBLIC_BUCKET_ID=

# Admin access
NEXT_PUBLIC_ADMIN_PASSKEY=

# Twilio
TWILIO_ACCOUNT_SID=
TWILIO_AUTH_TOKEN=
TWILIO_PHONE_NUMBER=

# Sentry
SENTRY_AUTH_TOKEN=
```

Set up the corresponding database and collections in your Appwrite project, and create a storage bucket for identification documents.

### Running the App

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

### Other Scripts

```bash
npm run build   # production build
npm run start   # run production build
npm run lint    # lint the codebase
```

## Notes

- If requests fail with `project_paused` (Appwrite error `403`), the Appwrite project has been paused due to inactivity — resume it from the Appwrite console.
