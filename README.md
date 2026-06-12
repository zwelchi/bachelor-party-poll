{\rtf1\ansi\ansicpg1252\cocoartf2869
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0

\f0\fs24 \cf0 # Bachelor Party Poll\
\
Single-page HTML/CSS/JS app for groomsmen to select available bachelor party weekends.\
\
## Supabase table setup\
\
Run this SQL in Supabase:\
\
```sql\
create table public.bachelor_votes (\
  id bigint generated always as identity primary key,\
  created_at timestamp with time zone default now() not null,\
  name text not null,\
  weekends text[] not null,\
  note text\
);\
\
alter table public.bachelor_votes enable row level security;\
\
create policy "Anyone can insert votes"\
on public.bachelor_votes\
for insert\
to anon\
with check (true);\
\
create policy "Anyone can read votes"\
on public.bachelor_votes\
for select\
to anon\
using (true);\
```\
\
## Deploy\
\
Open `bachelor-poll.html` locally or deploy as a static site.}