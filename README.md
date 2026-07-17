# 👿 ScreenDemons

**ScreenDemons** is a multiplayer screen time battling app. It leverages Apple's strict **Family Controls (Screen Time) API** to let users challenge their friends to stay off their phones. Break the rules, and the demons win.

## 🚀 The Core Concept
Traditional screen time apps rely on single-player guilt. ScreenDemons introduces **social accountability**. 
Users can create challenges (e.g., "No Instagram for 24 hours" or "Under 2 hours of total screen time today") and invite friends. The app securely monitors device activity thresholds and automatically updates multiplayer leaderboards, streaks, and ELO ratings based on who succeeds and who fails.

## 🛠 Tech Stack
This project is built with a highly optimized, modern mobile stack:

* **Frontend:** React Native (Expo)
* **Backend / Database:** Supabase (PostgreSQL)
* **Authentication:** Supabase Auth (Sign in with Apple, Google Sign-In)
* **Native API:** Apple Family Controls / DeviceActivity framework
* **Cloud Code:** Supabase Edge Functions (Deno)

## 🏗 Architecture Highlights
* **Lean Database:** Highly normalized PostgreSQL schema utilizing Row Level Security (RLS) policies to ensure users can only ever access data relevant to their active challenges.
* **Serverless Backend:** No dedicated Node.js servers. All backend logic runs exclusively through PostgreSQL Triggers and Supabase Edge Functions.
* **Automated Janitor:** `pg_cron` jobs automatically clean up orphaned challenges and permanently purge user data 48 hours after an account deletion request.
* **Privacy First:** Detailed app usage data never leaves the device. The iOS client evaluates screen time limits locally and only transmits binary pass/fail signals or aggregate metadata to the backend.

## 📖 Setup & Deployment
If you are setting up the backend from scratch, refer to the `SETUP_GUIDE.md` file in the root of this repository. It contains the exact SQL commands required to instantiate the database tables, RLS policies, enums, triggers, and cron jobs.

## 🔒 License
**Copyright (c) 2026 ScreenDemons. All Rights Reserved.**

This software and associated documentation files are proprietary and confidential. No part of this software may be reproduced, distributed, or transmitted in any form or by any means, without the prior written permission of the owner.
