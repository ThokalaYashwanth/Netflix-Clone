# netlix

netlix is a Netflix-style streaming UI built with Next.js. It includes authentication, profile selection, a featured title banner, movie browsing, a details modal, a watch page, and a favorites list backed by MongoDB through Prisma.

## Tech Stack

- Next.js 15
- React 18
- TypeScript
- Tailwind CSS
- Prisma ORM
- MongoDB
- NextAuth.js
- SWR for client data fetching
- Zustand for modal state
- Axios for HTTP requests
- Lodash and React Icons for utilities and UI

## Features

- Email/password sign up and sign in
- Google and GitHub authentication
- Protected home and profile routes
- Featured billboard movie with autoplay video preview
- Movie cards with play, favorite, and info actions
- Favorite movie management per user
- Dedicated watch page for playing a selected title
- Responsive navigation with mobile and desktop menus

## Project Structure

- [pages/](pages/) contains the route pages and API routes.
- [components/](components/) contains the reusable UI pieces.
- [hooks/](hooks/) contains SWR and Zustand-powered data hooks.
- [lib/](lib/) contains Prisma and auth helpers.
- [prisma/schema.prisma](prisma/schema.prisma) defines the MongoDB data models.
- [public/movies.json](public/movies.json) contains sample movie metadata.

## Prerequisites

- Node.js 18 or newer
- npm
- A MongoDB database
- NextAuth provider credentials for Google and/or GitHub if you want social login

## Environment Variables

Create a local environment file such as [`.env.local`](.env.local) with the values used by the app:

```env
DATABASE_URL=
NEXTAUTH_SECRET=
NEXTAUTH_JWT_SECRET=
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
GITHUB_CLIENT_ID=
GITHUB_CLIENT_SECRET=
```

## Install And Run

1. Install dependencies.

```bash
npm install
```

2. Generate the Prisma client if needed.

```bash
npx prisma generate
```

3. Start the development server.

```bash
npm run dev
```

4. Open [http://localhost:3000](http://localhost:3000).

## Available Scripts

- `npm run dev` starts the Next.js development server.
- `npm run build` creates a production build.
- `npm run start` runs the production server after building.
- `npm run lint` runs Next.js linting.

## App Flow

1. Visiting `/` checks for an authenticated session and redirects unauthenticated users to `/auth`.
2. The auth page supports login, registration, Google sign-in, and GitHub sign-in.
3. After signing in, the profile page lets the user enter the main experience.
4. The home page loads a featured title, trending movies, and the user’s favorites.
5. Movie cards open the watch page or the info modal, and favorite state is stored per user in MongoDB.

## Data Notes

- Movie records are fetched from the API routes under [pages/api/movies/](pages/api/movies/).
- Favorite movies are stored on the signed-in user document.
- The Prisma schema uses MongoDB object IDs for users, accounts, sessions, and movies.

## Styling Notes

- Global styling lives in [styles/globals.css](styles/globals.css).
- Tailwind is configured in [tailwind.config.js](tailwind.config.js).
- The app uses a dark Netflix-inspired layout with a fixed background hero image and video previews.

## Notes For Development

- If you add or change Prisma models, run `npx prisma generate` again.
- Social login requires the matching OAuth app credentials and a valid NextAuth secret setup.
- The project is already configured to use path aliases with `@/`.
