# Issues_Tracker

A modern issue tracking application built with Next.js.

## Features and Functionality

*   **Issue Tracking:** Create, assign, and track issues with ease. Set priorities, due dates, and statuses to keep your team on track.
*   **Intuitive UI:** A clean, modern interface that makes project management a breeze. No clutter, just what you need to get work done.
*   **Collaboration:** Work together seamlessly. Comment on issues, mention team members, and keep everyone in the loop.
*   **Custom Workflows:** Create workflows that match your team's process. Customize statuses, labels, and more.
*   **Real-time Updates:** See changes as they happen. No need to refresh or wait for updates.
*   **Powerful Search:** Find anything instantly with our powerful search. Filter by assignee, status, priority, and more.
*   **Authentication:** Secure user authentication with sign-in and sign-up functionality located at `/app/(auth)/signin/page.tsx` and `/app/(auth)/signup/page.tsx` respectively.
*   **Dashboard:** Centralized dashboard for managing and viewing issues.
*   **API Endpoints:** RESTful API endpoints for issue management located under `/app/api/issue/`.

## Technology Stack

*   **Framework:** Next.js
*   **UI Components:** React, custom UI components (located in `/app/components/ui/`)
*   **Database:** PostgreSQL with Drizzle ORM (configured in `/db/index.ts` and `/db/schema.ts`)
*   **Authentication:** JWT (JSON Web Tokens)
*   **Styling:** Tailwind CSS
*   **Validation:** Zod
*   **Testing:** Vitest

## Prerequisites

*   Node.js (version >= 18)
*   PostgreSQL database
*   Neon database (optional, for Vercel deployments)

## Installation Instructions

1.  Clone the repository:

    ```bash
    git clone https://github.com/Mohammed-Zrirake/Issues_Tracker.git
    cd Issues_Tracker
    ```

2.  Install dependencies:

    ```bash
    npm install
    # or
    yarn install
    # or
    pnpm install
    ```

3.  Set up your environment variables:

    Create a `.env.local` file in the root directory with the following variables:

    ```
    DATABASE_URL=<your_database_url>
    JWT_SECRET=<your_jwt_secret> # Minimum 32 characters long
    VERCEL=<true or false> # Set to true if deploying to Vercel
    ```

    *   `DATABASE_URL`: The connection string to your PostgreSQL database. Example: `postgres://user:password@host:port/database` or Neon database URL.
    *   `JWT_SECRET`: A secret key used to sign JWT tokens.  Must be at least 32 characters long.
    *   `VERCEL`: Set to `true` when deploying to Vercel, otherwise `false`. This configures the database connection using `drizzleNeon` or `drizzlePostgres` in `/db/index.ts`.

4.  Run database migrations (if necessary):

    This project uses Drizzle ORM.  Refer to Drizzle ORM documentation for migration instructions.  Generally, you'll use the Drizzle CLI with commands like:

    ```bash
    drizzle-kit generate:pg #Generate migration
    drizzle-kit push:pg #Apply migrations
    ```

5.  Seed the database (optional):

    To populate the database with some initial data, run the `seed.ts` script:

    ```bash
    npm run seed
    # or
    yarn seed
    # or
    pnpm seed
    ```

    This script creates demo users (admin@example.com, user@example.com) with the password "password123" and some sample issues. The script is located at `/scripts/seed.ts`.

6.  Start the development server:

    ```bash
    npm run dev
    # or
    yarn dev
    # or
    pnpm dev
    ```

    This will start the Next.js development server, usually on `http://localhost:3000`.

## Usage Guide

1.  Open your browser and navigate to `http://localhost:3000` (or the address where your development server is running).
2.  If you don't have an account, click on "Sign up" to create one at `/signup`.
3.  After signing up or if you already have an account, click on "Sign in" at `/signin` to log in.
4.  Once logged in, you'll be redirected to the dashboard (`/dashboard`), where you can view and manage issues.
5.  Click "New Issue" to create a new issue.  The `IssueForm` component located at `/app/components/IssueForm.tsx` is used for issue creation and editing.
6.  To view issue details, click on an issue in the dashboard.  The issue details page is located at `/app/issues/[id]/page.tsx`.
7.  To edit an issue, navigate to `/issues/[id]/edit` using the "Edit" button on the issue details page.
8.  You can delete an issue using the "Delete" button on the issue details page.
9.  To sign out, click on the "Sign Out" button in the navigation menu.

## API Documentation

The application includes RESTful API endpoints for managing issues. The API routes are located in the `/app/api/issue/` directory.

*   **GET /api/issue:** Retrieves all issues. Returns a JSON array of issue objects.
*   **GET /api/issue/[id]:** Retrieves a specific issue by ID. Returns a JSON object representing the issue.
*   **POST /api/issue:** Creates a new issue. Requires a JSON payload with the following properties:
    *   `title` (string, required): The title of the issue.
    *   `description` (string, optional): The description of the issue.
    *   `status` (string, optional, default: "backlog"): The status of the issue ("backlog", "todo", "in\_progress", or "done").
    *   `priority` (string, optional, default: "medium"): The priority of the issue ("low", "medium", or "high").
    *   `userId` (string, required): The ID of the user assigned to the issue.

    Example request body:

    ```json
    {
      "title": "New Issue",
      "description": "This is a new issue.",
      "status": "todo",
      "priority": "high",
      "userId": "user123"
    }
    ```

## Contributing Guidelines

Contributions are welcome! To contribute to this project:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Make your changes and commit them with descriptive commit messages.
4.  Test your changes thoroughly.
5.  Submit a pull request to the `The_Master` branch.

## License Information

No license is specified for this project. All rights are reserved by the author.

## Contact/Support Information

For questions, bug reports, or feature requests, please contact Mohammed-Zrirake through GitHub.