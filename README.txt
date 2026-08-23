TYLER NICHOLAS FOUNDATION - WEBSITE FILES
==========================================
For the Youth. For the Islands. For Tomorrow.

HOW THIS FOLDER WORKS
---------------------
Each folder contains an index.html that is served at a "clean" URL:

  index.html                        ->  yoursite.com/
  about/index.html                  ->  yoursite.com/about
  programs/index.html               ->  yoursite.com/programs
  programs/program/index.html       ->  yoursite.com/programs/program?slug=...
  opportunities/index.html          ->  yoursite.com/opportunities
  opportunities/opportunity/...     ->  yoursite.com/opportunities/opportunity?slug=...
  get-involved/index.html           ->  yoursite.com/get-involved
  news/index.html                   ->  yoursite.com/news
  news/article/index.html           ->  yoursite.com/news/article?slug=...
  events/index.html                 ->  yoursite.com/events
  events/event/index.html           ->  yoursite.com/events/event?slug=...
  careers/index.html                ->  yoursite.com/careers
  careers/job/index.html            ->  yoursite.com/careers/job?slug=...
  donate/index.html                 ->  yoursite.com/donate
  resources/index.html              ->  yoursite.com/resources
  faq/index.html                    ->  yoursite.com/faq
  contact/index.html                ->  yoursite.com/contact
  safeguarding/index.html           ->  yoursite.com/safeguarding
  404.html                          ->  shown for unknown URLs

  login/index.html                  ->  yoursite.com/login   (staff & volunteer sign-in)
  portal/index.html                 ->  yoursite.com/portal  (volunteer portal)
  staff/index.html                  ->  yoursite.com/staff   (staff & board back office)

Most static hosts (Netlify, Vercel, Cloudflare Pages, GitHub Pages) serve
folder/index.html at /folder automatically. Just upload everything keeping
the folders exactly as they are.

BACKEND (Supabase)
------------------
All pages connect to Supabase project: mcnemlwalcgdlmclijxc
Before the site works with real data, in that project you must:
  1. Run the database script (tnf-backend-schema.sql - provided separately).
  2. Create YOUR OWN account first via /login - the first sign-up
     automatically becomes the superadmin (that's you).
  3. Grant your account the hr / finance / governance / safeguarding
     permissions so you can see those areas in /staff.
  4. In Supabase Auth settings, set the Site URL to your domain and add
     your domain + /login to the redirect URLs.
  5. Fill in your contact details + social links in Site Settings (via /staff)
     so the footers and contact page populate.

Until content is added through /staff, public pages show tasteful empty
states - that is expected on a fresh database.


UPDATE - INTERNAL PLATFORM (staff + volunteer)
----------------------------------------------
STAFF back office (yoursite.com/staff)
- Redesigned with a top navigation bar (mobile shows a slide-in menu).
- New Home dashboard: time-of-day photo, live clock, local weather + place,
  greeting, your profile card and live stats.
- Team chat: delete your own messages (admins can delete anyone's).
- Data cleanup (admins) under Settings > Data cleanup: wipe old chat messages
  and read notifications to keep the database small.
- Staff accounts (admins + anyone with HR permission) under People & HR:
  edit a person's role, department, permissions, photo, and switch their
  account on/off. To ADD a new login, create the user in Supabase
  (Authentication > Users); they then appear here automatically. To remove
  access, just switch their account to inactive.

VOLUNTEER portal (yoursite.com/portal) - rebuilt
- Same clean look as staff. Sections: Home, My hours (log your own), 
  Announcements, Events (with RSVP), Opportunities, Resources, My details.
- My details is READ-ONLY (managed by the Foundation).
- Notification bell included. No documents section (staff-only by design).

NO serverless functions and NO email service are required anywhere.

BACKEND SQL TO RUN (in Supabase SQL editor, in order)
-----------------------------------------------------
1. tnf-backend-schema.sql        (base - already done)
2. tnf-backend-v3-upgrade.sql    (notifications, documents, etc. - already done)
3. tnf-backend-v3_1-hr-accounts.sql   (lets HR edit profiles) <-- run this
That's everything. All account management, cleanup, chat delete, hours and
notifications work with plain tables + row-level security. No functions.
