# IA Student Hub

Student hub for **Innovation Academy** — live chat, Anime / Music / Course Help tabs, login, and mod tools.

Deploys to [Vercel](https://vercel.com) with [Supabase](https://supabase.com) for auth, chat, and data.

## Features

- **Live chat** with realtime messages
- **Tabs:** Anime, Music, Course Help (Algebra 1 & Geometry 1)
- **Login / Sign up** for all students
- **Konami code secret page:** `↑ ↑ ↓ ↓ ← → ← → B A` opens a hidden note
- **Mod account** (`jishiprem26@gmail.com`):
  - Delete any chat message
  - Ban / kick users from the site
  - Edit tab page text
  - Edit the secret note text box

## 1. Create Supabase project

1. Go to [supabase.com](https://supabase.com) and create a free project.
2. Open **SQL Editor** and run the full script in `supabase/schema.sql`.
3. Open **Database → Replication** and confirm `messages` is enabled for Realtime (the schema script adds it).
4. Open **Authentication → Providers → Email** and turn **off** “Confirm email” for easier student sign-up (optional but recommended for a school hub).

## 2. Environment variables

Copy `.env.example` to `.env.local` and fill in values from **Project Settings → API**:

```
NEXT_PUBLIC_SUPABASE_URL=...
NEXT_PUBLIC_SUPABASE_ANON_KEY=...
```

## 3. Run locally

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## 4. Deploy to Vercel

1. Push this folder to GitHub.
2. Import the repo in [Vercel](https://vercel.com/new).
3. Add the same two environment variables in **Project Settings → Environment Variables**.
4. Deploy.

Or use the CLI:

```bash
npm i -g vercel
vercel
```

## Mod access

Sign up or log in with **jishiprem26@gmail.com**. That email automatically gets mod powers (badge shows **MOD** in the header).

## Secret page

While logged in, enter the Konami code on your keyboard:

**Up Up Down Down Left Right Left Right B A**

Mods see an editable text area. Other signed-in users see read-only content (or blank if empty).

## Project structure

```
app/           Next.js pages & global styles
components/    Hub UI (chat, tabs, auth, secret page)
lib/           Supabase clients & mod helpers
supabase/      Database schema SQL
```

## Notes

- Banned users are signed out and cannot use the hub until unbanned by a mod.
- Kick applies a ban (same as ban for this version).
- Keep your Supabase anon key in env vars only — never commit `.env.local`.
