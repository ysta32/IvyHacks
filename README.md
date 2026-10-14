# IvyHacks 2026 — Brodie for Coaches

**Team Beat Muse** · Jimmy, Kevin, Stanley, Ryan, Tristan

A coach writes the program. Brodie runs the workout over FaceTime. The coach sees how it went.

Personal trainers hand clients a PDF and hope they follow it. Brodie for Coaches turns that PDF into a coached session: the client video-calls Brodie, an AI coach that watches through the camera, counts every rep, corrects form out loud and talks between sets. When the call ends, the client and the coach each get a recap showing which muscles were trained and how cleanly. Nobody installs an app or makes an account — everything is a private link.

<p align="center"><img src="https://brodie-for-coaches.vercel.app/api/recap-image/demo" width="320" alt="The recap card Brodie sends after a call: front and back muscle heat map, rank, reps, sets and clean-rep percentage" /></p>

## Try it

| What | Link |
| --- | --- |
| Client recap (what the client gets after a call) | https://brodie-for-coaches.vercel.app/r/demo |
| Coach dashboard (every client's sessions) | https://brodie-for-coaches.vercel.app/c/demo |
| Recap card (the image Brodie texts to the client) | https://brodie-for-coaches.vercel.app/api/recap-image/demo |

## How it works

1. **The coach uploads a program PDF.** Gemini reads it into days, exercises, sets and reps. The coach checks the parsed days and assigns one to a client.
2. **The client calls Brodie.** A LiveKit worker loads that day, counts squats, push-ups, lunges, jumping jacks and curls with MediaPipe pose estimation, flags form faults, and coaches by voice.
3. **Every rep is saved.** When the call ends, the worker writes the session, sets, reps, faults and per-muscle scores to Supabase.
4. **Everyone sees the recap.** The client gets a recap link and a recap card; the coach's dashboard shows every client's sessions and which muscles were worked.

## Built with

Python · LiveKit Agents · MediaPipe pose · Gemini 2.5 Flash · Next.js 16 · Tailwind · shadcn/ui · Supabase · Vercel

## The code

This repo is the team's IvyHacks entry point. The project itself lives here:

**→ [jimmyc803/brodie-starter](https://github.com/jimmyc803/brodie-starter)** — call worker, web app, database schema and the shared exercise-to-muscle contract.

My part: the database, the call worker that saves each session, and the team contract (`shared/muscles.json`) that the coach and the web app both read.
