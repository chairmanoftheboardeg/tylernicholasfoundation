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
