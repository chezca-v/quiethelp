# Blueprint: QuietHelp

## 1. Overview

QuietHelp is a Flutter-based mobile application that allows users to send silent emergency alerts to trusted contacts. The application uses Firebase for backend services including authentication, database, and push notifications.

## 2. Style and Design

*   **Theme:** Dark theme with a primary color of deep purple.
*   **Scaffold Background Color:** `#121212`
*   **Color Scheme:** Based on `Colors.deepPurple` with `Brightness.dark`.
*   **Typography:** Default Flutter typography.
*   **Iconography:** Standard Material Design icons.

## 3. Existing Features

### 3.1. User Authentication

*   **Login Screen (`/login`):** Allows users to log in to their account.
*   **Register Screen (`/register`):** Allows new users to create an account.
*   **Authentication Service (`lib/features/auth/auth_service.dart`):** Manages user authentication state.

### 3.2. Core Alerting

*   **Alert Screen (`/alert`):** The main screen for triggering an emergency alert.
*   **Alert History Screen (`/history`):** Displays a history of past alerts.

### 3.3. Contact Management

*   **Contacts Screen (`/contacts`):** Displays a list of trusted contacts.
*   **Add Contact Screen (`/add_contact`):** Allows users to add new trusted contacts.

### 3.4. Location Services

*   **Location Map Screen (`/map`):** Displays a map with the user's location.
*   **Geolocator:** The app uses the `geolocator` package to get the user's location.

### 3.5. Offline Support

*   **Offline Banner:** A banner is displayed at the top of the screen when the user is offline.
*   **Connectivity Service (`lib/core/services/connectivity_service.dart`):** Monitors the user's network connectivity.

### 3.6. Disguise Mode

*   **Disguise Screen (`/disguise`):** A screen to disguise the app.
*   **Disguise Settings Screen (`/disguise_settings`):** Allows the user to configure the disguise mode.

### 3.7. Navigation

*   The app uses the `go_router` package for navigation.
*   The main navigation is handled by a `ShellRoute` in `lib/app.dart`.

## 4. Plan for SMS Feature

The goal is to implement a feature that sends an SMS to the user's trusted contacts when an alert is triggered.

### 4.1. Install `telephony` package

I will add the `telephony` package to the `pubspec.yaml` file to enable sending SMS messages. This package provides a simple API for sending SMS messages.

### 4.2. Update `AlertScreen`

I will modify the `AlertScreen` to trigger the SMS sending functionality when the alert is triggered.

### 4.3. Implement SMS Sending Logic

I will create a new function in `lib/features/alert/alert_screen.dart` to handle the SMS sending logic. This function will:
1.  Retrieve the user's trusted contacts from Firestore.
2.  Get the user's current location using the `geolocator` package.
3.  For each trusted contact, send an SMS with the emergency alert and the user's location.

### 4.4. Handle Permissions

I will add the necessary permissions to the `AndroidManifest.xml` file to allow the app to send SMS messages and access the user's location. I will also use the `permission_handler` package to request these permissions at runtime.

### 4.5. Test the feature

I will add a test to verify that the SMS is sent correctly when an alert is triggered.
