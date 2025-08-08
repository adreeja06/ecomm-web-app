Kharidlo E-Commerce Monorepo
Kharidlo is a full-featured e-commerce platform built as a monorepo using Turborepo. It includes separate Next.js applications for admin and user interfaces, a shared database package powered by Prisma, and a modular architecture for scalability and maintainability.

Project Structure
├── apps/
│   ├── admin/      # Admin dashboard (Next.js)
│   └── user/       # User-facing storefront (Next.js)
├── packages/
│   └── db/         # Shared Prisma database package
├── package.json    # Root config, npm workspaces, scripts
├── turbo.json      # Turborepo configuration
Apps
admin: Admin dashboard for managing products, customers, sales, and more. Built with Next.js, includes authentication, analytics, and product management features.
user: User-facing storefront for browsing products, managing cart, wishlist, checkout, and account. Built with Next.js, includes authentication, product search, reviews, and more.
Packages
db: Shared Prisma database schema and client, used by both apps for data access.
Key Features
Modular monorepo architecture with Turborepo
Next.js apps for admin and user experiences
Authentication via next-auth
Database access via Prisma
Data visualization with Recharts
PDF generation with jsPDF and jsPDF-Autotable
Toast notifications with react-toastify
Carousel and UI enhancements with Swiper and DaisyUI
Shared components and utilities
Getting Started
1. Install Dependencies
npm install
2. Environment Variables
Each app and the database package require environment variables for proper operation (database connection, authentication secrets, API keys, etc.). Example files are provided:

Root: .env.example (contains variables for Google OAuth, Prisma, JWT, NextAuth)
Database: packages/db/.env.example (contains DATABASE_URL)
Setup Instructions:

Copy the example files to actual environment files:
At the root:
copy .env.example .env.local
For the database package:
copy packages\db\.env.example packages\db\.env
Open each .env.local and .env file and fill in your real credentials and secrets.
For example, set your Google OAuth client ID/secret, database connection string, JWT secret, NextAuth secret, etc.
Required variables include:

GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET (Google OAuth)
DATABASE_URL (Prisma database connection)
JWT_SECRET (JWT authentication)
NEXTAUTH_SECRET (NextAuth authentication)
Refer to the .env.example files for the full list and descriptions. You may need to add more variables depending on your deployment or third-party integrations.

3. Database Setup
Prisma migrations and schema are managed in packages/db/prisma. To set up the database:

npx prisma migrate dev --schema=packages/db/prisma/schema.prisma
4. Running the Apps
Start all apps and packages in development mode:

npm run dev
Or run a specific app:

cd apps/admin
npm run dev

cd apps/user
npm run dev
5. Build for Production
Build all apps and packages:

npm run build
This project is maintained by the Kharidlo team.

Useful Links
Next.js Docs
Prisma Docs
Build
To build all apps and packages, run the following command:

cd my-turborepo
npm build
Develop
To develop all apps and packages, run the following command:

cd my-turborepo
npm dev
Remote Caching
Tip

Vercel Remote Cache is free for all plans. Get started today at vercel.com.

Turborepo can use a technique known as Remote Caching to share cache artifacts across machines, enabling you to share build caches with your team and CI/CD pipelines.

By default, Turborepo will cache locally. To enable Remote Caching you will need an account with Vercel. If you don't have an account you can create one, then enter the following commands:

cd my-turborepo
npx turbo login
This will authenticate the Turborepo CLI with your Vercel account.

Next, you can link your Turborepo to your Remote Cache by running the following command from the root of your Turborepo:

npx turbo link
Useful Links
Learn more about the power of Turborepo:

Tasks
Caching
Remote Caching
Filtering
Configuration Options
CLI Usage
