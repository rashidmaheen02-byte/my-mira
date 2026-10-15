# My Mira — background cloud sync (no account login)

This package keeps the planner UI and adds a discreet **Private sync** panel. There is no sign-in/sign-up UI. Pair devices by creating a private code on one device and entering that same code on the other. The code is a bearer secret: anyone who has it can access that planner, so keep it private.

## Important: one-time Supabase setup is required
The browser files alone cannot safely write shared data to Supabase without exposing a privileged secret. This ZIP includes a Supabase Edge Function that uses the server-side service-role key. Do **not** put that key in `config.js`.

1. In Supabase SQL Editor, run `supabase/setup.sql`.
2. Install the Supabase CLI and log in. From this folder run: `supabase link --project-ref akebdmrvizrjzsqatnwj`
3. Set the function secret: `supabase secrets set SUPABASE_SERVICE_ROLE_KEY=YOUR_SERVICE_ROLE_KEY` (get it from Supabase project API settings; do not paste it into this chat or commit it). `SUPABASE_URL` is supplied by the Supabase environment.
4. Deploy: `supabase functions deploy mira-sync --no-verify-jwt`
5. Upload the contents of this folder to the root of your existing GitHub Pages repository, replacing matching files. Commit and wait for deployment.
6. Open My Mira on the first device → **Connect / pair device** → **Create new planner code**. Copy the code privately. On the second device, open **Connect / pair device**, paste the code, and choose **Connect with code**.

## Data behavior and limitation
The sync endpoint stores a JSON snapshot in a separate table; it does not use the earlier `mira_tasks`, `mira_prayers`, or `mira_reflections` tables. Existing local browser data is retained. On pairing, records are merged in the browser; if two devices edit the same task concurrently, the simple merge may not resolve every conflict perfectly. This is a starter implementation, not an audited sync service.

`config.js` contains only the public publishable key. Never place a service-role key in the website files.
