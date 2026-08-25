Get it on [**Google Play Store**](https://play.google.com/store/apps/details?id=com.bersyte.billify) & [**App Store**](https://apps.apple.com/bg/app/billiffy/id1638395030) !

<p>
  <img width="1232" height="729" alt="Offline first architecture" src="https://github.com/user-attachments/assets/403edd51-b490-4eae-83b2-dd4cf9a783cd" />
</p>

# Billiffy

Cross-platform personal and collaborative finance app (Android/iOS), built with Flutter, offline-first.

## Problem and architecture decision

A finance app needs to work without a network connection and sync data across multiple devices and users without losing consistency. The core decision was making the local database the single source of truth for the UI, treating the backend as an async destination rather than a direct dependency of every user action.

## Flow 
```UI → Local DB (Drift) → Outbox → Sync → Firebase → Inbox → Local DB ```

- Outbox: local changes are queued and synced once connectivity is available.
- Inbox: remote changes are pulled and applied to the local database.
- Conflict Resolution: Last Write Wins (LWW), keeping sync deterministic across shared accounts on multiple devices.

This keeps the UI always responsive, even offline, and shields the user from network complexity.

## Core Features

- Income/expense transactions, created via text, voice, or receipt scan (AI-assisted).
- Automatic categorization and real-time currency conversion (multi-currency).
- Recurring transactions (subscriptions, bills, salaries).
- Monthly budgets by category, with progress tracking.
- Collaborative accounts: shared transactions, budgets, and categories, synced across devices.
- Multiple accounts with isolated data and session per account.
- Reports and analytics (weekly/monthly/yearly) with category breakdowns.
- Auth via email/password, Google, and Apple Sign-In.
- Internationalization (English and Portuguese).

## Tech Stack

* Flutter (Dart) - cross-platform application
* Drift - Local Relational database
* Firebase - Backend and cloud infrastructure
* Cloud Functions - Server-side operations
* Riverpod - State management and D.I
* GoRouter - Navigation
* RevenueCat - Subscriptions and Premium entitlements
* Firebase Crashlytics - crash reporting
* PostHog - Product Analytics
* AI - Automated transaction extraction and categorization

## Platforms

* Android
* iOS

<p align="left">
  <img width="370" height="436" alt="Billiffy" src="https://github.com/user-attachments/assets/78721c19-541d-4aab-b156-7484d3d181be"/>
  <img width="370" height="436" alt="Billiffy" src="https://github.com/user-attachments/assets/ccc118f2-b64f-4ff8-a452-f3ece789ba63"/>
</p>


## Engineering challenges solved:

- Designing local-first data flows with reliable outbox/inbox synchronization.
- Resolving concurrent writes across multiple devices.
- Isolating data when switching between accounts.
- Supporting offline mutations with eventual sync.
- Integrating multiple auth providers without breaking the offline-first experience.

Get it now on the [**Google Play Store**](https://play.google.com/store/apps/details?id=com.bersyte.billify) & [**App Store**](https://apps.apple.com/bg/app/billiffy/id1638395030) !

