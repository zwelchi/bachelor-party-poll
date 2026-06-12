# Bachelor Party Poll

Single-page HTML/CSS/JS app for groomsmen to select available bachelor party weekends.

## Supabase table setup

Run this SQL in Supabase:

```sql
create table public.bachelor_votes (
  id bigint generated always as identity primary key,
  created_at timestamp with time zone default now() not null,
  name text not null,
  weekends text[] not null,
  note text
);

alter table public.bachelor_votes enable row level security;

create policy "Anyone can insert votes"
on public.bachelor_votes
for insert
to anon
with check (true);

create policy "Anyone can read votes"
on public.bachelor_votes
for select
to anon
using (true);
```

## Deploy

Open `index.html` locally or deploy as a static site.
