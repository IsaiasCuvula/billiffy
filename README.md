Get it on [**Google Play Store**](https://play.google.com/store/apps/details?id=com.bersyte.billify) & [**App Store**](https://apps.apple.com/bg/app/billiffy/id1638395030) !

<p align="left">
  <img width="370" height="436" alt="Billiffy" src="https://github.com/user-attachments/assets/78721c19-541d-4aab-b156-7484d3d181be"/>
  <img width="370" height="436" alt="Billiffy" src="https://github.com/user-attachments/assets/ccc118f2-b64f-4ff8-a452-f3ece789ba63"/>
</p>

# Billiffy

A cross-platform personal/colaborative finance app built with Flutter for android and iOS, focused on offline-first data management, collaborative accounts, and automated recurring transaction entry.

The app is currently available on Google Play, with the iOS release coming next.

## Technical Highlights

* Offline-first architecture with local persistence as the primary source for the UI.
* Drift for the local relational database and reactive data access.
* Firebase for authentication, backend services, and cloud data.
* Outbox pattern for reliably queueing local mutations while offline and synchronizing them when connectivity is restored.
* Inbox pattern for pulling and applying remote changes locally.
* Last Write Wins (LWW) conflict resolution for concurrent updates.
* Collaborative accounts with shared transactions, budgets, and categories.
* Multiple accounts with isolated account data and session management when switching between accounts.
* Multi-currency transactions with automatic currency conversion.
* AI-assisted transaction creation from text, voice, and receipt scans.
* RevenueCat for subscription and premium feature management.
* Firebase Crashlytics for crash reporting and stability monitoring.
* PostHog for product analytics and usage insights.
* Google and Apple Sign-In, plus email/password authentication.
* Internationalization with English and Portuguese support.

## Architecture

The application follows a layered architecture designed to keep the domain and presentation layers independent from infrastructure concerns.

### Offline-first

The local database is the primary data source for the application.

User actions are persisted locally first, allowing the application to remain fully usable without a network connection. Changes that need to reach the backend are placed in an outbox queue and synchronized when connectivity becomes available.

Remote changes are handled through an "inbox flow", allowing the local database to consume changes received from the backend.

The synchronization flow can be summarized as:

```text
UI
 ↓
Local Database (Drift)
 ↓
Outbox
 ↓
Sync
 ↓
Firebase
 ↓
Inbox
 ↓
Local Database
```

This approach allows the UI to remain responsive and functional regardless of network availability.

### Conflict Resolution

Collaborative accounts introduce concurrent writes from multiple devices.

Billiffy currently uses Last Write Wins (LWW) as the conflict resolution strategy for synchronized entities. This keeps synchronization deterministic while allowing multiple users and devices to modify shared data.

### Multiple Accounts

The application supports multiple financial accounts and requires session state to be managed independently from the currently selected account.

Switching accounts updates the active data scope while keeping account-specific transactions, budgets, and categories isolated.

## Core Features

### Transaction Management

* Create income and expense transactions.
* Add transactions using text, voice, or receipt scanning.
* Automatic transaction categorization.
* Attach receipts and images to transactions.
* Support for multiple currencies.
* Automatic currency conversion using current exchange rates.
* Recurring transactions for subscriptions, bills, salaries, and other regular payments.

### Budgets

* Create monthly budgets.
* Define spending limits by category.
* Track budget progress.
* Organize spending using customizable categories.

### Collaborative Accounts

* Create shared accounts.
* Share transactions with other users.
* Share budgets and categories.
* Keep financial data synchronized across multiple devices.

### Analytics

* Expense and income reports.
* Category-based analysis.
* Daily, weekly, monthly, and yearly views.
* Charts for understanding spending patterns.

### Authentication

* Email/password authentication.
* Google Sign-In.
* Apple Sign-In.
* Multiple account support.

## Tech Stack

* Flutter / Dart - cross-platform application
* Drift - local relational database
* Firebase - backend and cloud infrastructure
* Cloud Functions — server-side operations
* Riverpod - state management
* GoRouter - navigation
* RevenueCat - subscriptions and premium entitlements
* Firebase Crashlytics - crash reporting
* PostHog - product analytics
* AI - automated transaction extraction and categorization

## Platforms

* Android
* iOS

Key engineering challenges included:

* Designing local-first data flows.
* Implementing reliable synchronization through outbox/inbox patterns.
* Handling concurrent writes and conflict resolution.
* Keeping multiple devices synchronized.
* Managing account-scoped data when switching between accounts.
* Supporting offline mutations and eventual synchronization.
* Integrating authentication across multiple providers.
* Introducing collaborative financial data without compromising the local-first experience.

Get it now on the [**Google Play Store**](https://play.google.com/store/apps/details?id=com.bersyte.billify) & [**App Store**](https://apps.apple.com/bg/app/billiffy/id1638395030) !

