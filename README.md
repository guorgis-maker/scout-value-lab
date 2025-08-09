
# Scout Value Lab — MVP Scaffold

This scaffold is a minimal Next.js + TypeScript app with an example API endpoint, Postgres schema (Prisma), and Azure deployment notes.

## What this includes
- Next.js front-end (TypeScript + Tailwind)
- Simple serverless API route returning mock player data
- Prisma schema for PostgreSQL
- Example SQL migration to create `players` table
- GitHub Actions workflow for Azure Static Web Apps

## Local dev
1. Install dependencies:

```bash
npm install
```

2. Run the dev server:

```bash
npm run dev
```

3. Open http://localhost:3000

## Database
This scaffold uses PostgreSQL. For local dev you can run Postgres via Docker:

```bash
docker run --name svl-postgres -e POSTGRES_PASSWORD=pass -e POSTGRES_USER=svl -e POSTGRES_DB=svl -p 5432:5432 -d postgres:15
```

Set environment variable `DATABASE_URL` (example):

```
DATABASE_URL="postgresql://svl:pass@localhost:5432/svl?schema=public"
```

Run Prisma migrate:

```bash
npx prisma migrate dev --name init
```

## Deploy to Azure
1. Create an Azure Static Web App (link to your GitHub repo) — select `custom` build: `npm run build`
2. Provision Azure Database for PostgreSQL (Flexible Server)
3. Set the `DATABASE_URL` as a secret in GitHub Actions/Azure Static Web Apps

## Next steps I can implement for you if you want me to continue:
- Integrate real football data sources (API-Football / Transfermarkt scrapers)
- Build valuation engine (rule-based then ML)
- Add authentication (Azure AD B2C) and role-based permissions
- Create admin UI + import pipelines
