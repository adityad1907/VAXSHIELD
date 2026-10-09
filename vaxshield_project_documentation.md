# VaxShield AI

> **Intelligent Cold Chain Telemetry, Equipment Reliability & Predictive Maintenance Platform**

[![Tech Stack](https://img.shields.io/badge/Stack-Next.js%20%7C%20TypeScript%20%7C%20Prisma%20%7C%20PostgreSQL-blue)](https://github.com/adityad1907/VAXSHIELD)
[![Test Suite](https://img.shields.io/badge/Tests-Vitest-green)](https://github.com/adityad1907/VAXSHIELD)
[![License](https://img.shields.io/badge/License-MIT-purple.svg)](LICENSE)

---

## Overview

**VaxShield AI** is an end-to-end telemetry and asset monitoring platform tailored for temperature-sensitive healthcare logistics, primarily vaccine cold chains. By streaming and auditing storage conditions, computing proactive reliability metrics, and alerting operators to excursion risks, VaxShield prevents pharmaceutical spoilage across distributed regional healthcare facilities.

---

## Key Features

- **Real-Time Telemetry Tracking:** Ingests live temperature, humidity, and power telemetry across remote refrigeration hubs.
- **Predictive Health & Reliability Scoring:** Algorithmic calculation of equipment wear, mean-time-between-failure (MTBF) indicators, and critical excursion risk indices.
- **Threshold Alerting & Anomaly Flagging:** Instant escalation triggers when temperature curves breach the safe $+2^\circ\text{C}$ to $+8^\circ\text{C}$ clinical envelope.
- **Role-Based Access Control (RBAC):** Middleware-enforced permissions isolating views for field technicians, facility leads, and regional inventory directors.
- **Audit Trails & Compliance:** Auto-generates timestamped logs and cold chain custody compliance reports.
- **High-Coverage Test Suite:** Thorough unit and integration test coverage across algorithmic scoring pipelines using Vitest.

---

## Tech Stack

| Domain | Technologies |
|---|---|
| **Framework** | Next.js (App Router, Server Actions) |
| **Language** | TypeScript (Strict mode enabled) |
| **Styling & UI** | Tailwind CSS, Lucide Icons |
| **Data Layer & ORM** | Prisma ORM |
| **Database** | PostgreSQL |
| **Testing** | Vitest |
| **Tooling & CI** | ESLint, Prettier, Git |

---

## System Architecture

```text
       [ IoT / Field Sensors & Telemetry Simulators ]
                              │
                              ▼
             [ Next.js API Routes / Ingestion ]
                              │
               (Validation & Auth Middleware)
                              │
         ┌────────────────────┴────────────────────┐
         ▼                                         ▼
[ Scoring & Alert Engine ]                 [ Prisma ORM Client ]
  - Excursion Risk Index                     - Schema Migrations
  - Sensor Anomaly Flags                     - Relational Queries
         │                                         │
         └────────────────────┬────────────────────┘
                              ▼
                   [ PostgreSQL Database ]
                              │
                              ▼
              [ Next.js Real-time Dashboard ]
            (Technicians / Clinic Admins / Leads)
```

---

## Project Structure

```bash
VAXSHIELD/
├── prisma/
│   ├── schema.prisma        # Database schema definitions and relational models
│   └── migrations/          # Version-controlled database migration history
├── src/
│   ├── app/                 # Next.js App Router (pages, dashboards, API routes)
│   ├── components/          # Reusable UI widgets, layout wrappers, and charts
│   ├── lib/                 # Core business logic, scoring formulas, prisma client
│   └── middleware.ts        # Route authentication & role enforcement
├── tests/                   # Vitest unit test suites & mock datasets
├── public/                  # Static assets and graphics
├── .env.example             # Template for local environment configuration
├── package.json             # Scripts and dependency specifications
├── tsconfig.json            # TypeScript compiler configuration
└── vitest.config.ts         # Vitest execution configuration
```

---

## Getting Started

### Prerequisites

Ensure you have the following installed on your local development machine:

- **Node.js**: `v18.17.0` or later
- **npm** (v9+), **pnpm**, or **yarn**
- **PostgreSQL**: A running local instance or a cloud database URL (e.g., Supabase, Neon)

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/adityad1907/VAXSHIELD.git
   cd VAXSHIELD
   ```

2. **Install project dependencies:**
   ```bash
   npm install
   ```

3. **Set up environment variables:**
   Copy the example environment configuration:
   ```bash
   cp .env.example .env
   ```
   Populate your `.env` with your credentials:
   ```env
   DATABASE_URL="postgresql://<DB_USER>:<DB_PASSWORD>@localhost:5432/<DB_NAME>?schema=public"
   NEXTAUTH_SECRET="generate-a-strong-secret-key"
   NEXTAUTH_URL="http://localhost:3000"
   ```

4. **Run database migrations & generate client:**
   ```bash
   npx prisma migrate dev --name init
   npx prisma generate
   ```

5. **Start the local development server:**
   ```bash
   npm run dev
   ```

6. Open [http://localhost:3000](http://localhost:3000) in your browser to view the application.

---

## Testing

Unit and integration test suites are managed with Vitest:

```bash
# Execute test suite once
npm run test

# Run tests in continuous watch mode
npm run test:watch

# Generate code coverage reports
npm run test:coverage
```

---

## Roadmap

- [ ] Automated SMS / WhatsApp webhook alerts via Twilio for critical cold chain failures.
- [ ] Direct MQTT / LoRaWAN edge gateway integration for physical sensor streaming.
- [ ] Exportable PDF compliance reports for WHO / regulatory inspection audits.

---

## Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'feat: add some amazing feature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## License

Distributed under the MIT License. See `LICENSE` for more information.