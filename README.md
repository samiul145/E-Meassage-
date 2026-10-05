# E-Message Real App

Supabase URL and publishable key are configured in `index.html`.

## Required SQL

Run these once in Supabase SQL Editor:

1. The database schema previously supplied in chat.
2. `direct-conversation.sql`
3. `emessage-call-signals.sql`
4. `grants-fix.sql`
5. `username-rpc.sql`  <-- required for signup username availability check.
6. `signup-profile-trigger.sql`  <-- required: stores the chosen username during Auth signup.

Do NOT grant anonymous SELECT access to `public.profiles`. The app uses the secure `is_username_available()` RPC instead.

This build uses email/password auth, unique usernames, realtime chat, and WebRTC call signaling. TURN infrastructure is still required for reliable calls across restrictive NAT/firewalls.


V4 repair: signup sends username in Auth user metadata; the database trigger creates the profile. This works whether email confirmation is enabled or disabled.
