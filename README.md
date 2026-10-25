# UniCircle

UniCircle is a College Friend Finder for students across India, backed by Supabase.

Students create an account, enter their college name and the city/state where the college is present, discover classmates, connect, and chat.

## Features

- Supabase Auth login / sign-up (email + password) — no sample/demo accounts, no localStorage accounts
- Profiles stored in Supabase, visible to all signed-in users across laptop and mobile
- Create Account with college name, city and state/UT
- 133-college list tagged by type: Diploma, BTech, Medical and University, with a Google Maps link built from the exact typed college + city + state
- Discover real Supabase profiles, filtered by same college, same city, online status and mutual interests
- Connections (accept / decline) and chats stored in Supabase
- Hero scrolling marquee and a scroll-driven Campus Journey animation (entering college, gates opening, meeting friends)

## Run it

Open `index.html` in any browser. No build step is needed — it is a single self-contained HTML file that connects to Supabase.

## Supabase setup

In Supabase, run the SQL for the `profiles`, `connections` and `messages` tables with Row Level Security (see the in-app setup banner if tables are missing). The banner SQL is a repair pass: it adds any missing columns with `alter table … add column if not exists` (including `college_name` and `looking`) and reloads the schema cache, without deleting existing accounts or data.

Profile saves are resilient: if Supabase reports a missing column, the app drops just that field, retries, and shows a plain-language message instead of a raw schema-cache error.

Email confirmation is on by default in Supabase Auth: after sign-up, confirm the email, then sign in. Turn off "Confirm email" in Authentication → Sign In / Providers → Email for instant sign-in during testing.

## Storage note

Accounts and profiles live in Supabase, not in browser localStorage, so a laptop account shows up on mobile and vice versa.
