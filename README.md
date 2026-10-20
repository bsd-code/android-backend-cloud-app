# 🧊 Smart Fridge — Smart Pantry with Firebase & AI

![Kotlin](https://img.shields.io/badge/Kotlin-2.2.10-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)
![Android SDK](https://img.shields.io/badge/Android%20SDK-30%2B-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-Auth%20%7C%20Firestore%20%7C%20AI-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)

**Smart Fridge** is a native Android application built with **Kotlin** as part of the **A1 — Cloud Backend** module at *Institut Marianao*.

The app lets each user manage their household fridge or pantry independently and generate **AI-powered recipe suggestions** based on the ingredients currently available in their inventory.

---

## 🚀 Key Features

### 🔐 1. User Authentication — Firebase Authentication

- **Sign-up and sign-in:** Users can create an account and log in with an email address and password.
- **Form validation:** Required fields, email format, and password matching are validated, with errors handled centrally.
- **User data isolation:** Each user can access only their own pantry and ingredients.
- **Email verification:** Listed as an extension to the core functionality.

### 📦 2. Ingredient and Inventory Management — Cloud Firestore

- **Full CRUD operations:** Create, read, update, and delete ingredients in Cloud Firestore.
- **Deletion confirmation:** A confirmation dialog appears before an ingredient is deleted.
- **Dynamic editing:** Selecting an ingredient loads its details into the form so it can be edited.
- **Quick form reset:** A **Clear** button resets the form for a new entry.
- **Categories:** Ingredients can be organised into Fruit & Veggies, Meat & Fish, Dairy & Eggs, Bakery & Bread, Grains & Pasta, Sauces & Condiments, Drinks, Leftovers, and Other.

### 🤖 3. AI Recipe Suggestions — Firebase AI Logic

- **Automatic recipe generation:** Requests personalised recipe ideas based on the ingredients in the user's inventory.
- **Markdown formatting:** Processes formatted responses containing headings, bullet lists, and bold text.
- **Dedicated results screen:** Displays generated recipes in a separate activity, rendered with **Markwon**.
- **Loading feedback:** Shows a loading/progress indicator while the AI request is being processed.

---

## 📊 Cloud Firestore Data Model

The `ingredients` collection is scoped to the authenticated user using the following path:

`users/{userId}/ingredients/{ingredientId}`

| Field | Type | Required | Description |
|:---|:---|:---:|:---|
| `name` | `String` | Yes | Ingredient name, e.g. `Eggs`. |
| `quantity` | `Int` | Yes | Available quantity, e.g. `6`. |
| `unit` | `String?` | No | Unit of measurement, such as `units`, `grams`, `kg`, `liters`, `ml`, or `packs`. |
| `category` | `String?` | No | Ingredient category, such as `Fruit & Veggies`, `Meat & Fish`, or `Dairy & Eggs`. |
| `expiration` | `Date?` | No | Expiration date. |
| `addedAt` | `Date` | Yes | Date the ingredient was created or added. |

---

## 📱 App Screens

1. **Login screen:** Sign-in form with credential validation and navigation to registration.
2. **Registration screen:** Account creation form with password confirmation.
3. **Main fridge/pantry screen:**
   - Form to add or edit ingredients.
   - A `RecyclerView` displaying stored ingredients and updating in real time.
   - A button to generate an AI recipe suggestion.
   - A logout option.
4. **Suggested recipe screen:** Displays the AI-generated recipe, rendering its Markdown with `Markwon`.

---

## 🛠️ Tech Stack

- **Language:** [Kotlin](https://kotlinlang.org/)
- **Platform:** Android SDK (API 30+)
- **UI and Android components:** Android Jetpack, `ViewBinding`, `ConstraintLayout`, and `RecyclerView`
- **Authentication:** [Firebase Authentication](https://firebase.google.com/docs/auth)
- **Cloud database:** [Cloud Firestore](https://firebase.google.com/docs/firestore)
- **AI integration:** [Firebase AI Logic / Vertex AI for Firebase](https://firebase.google.com/docs/vertex-ai)
- **Markdown rendering:** [Markwon](https://github.com/noties/Markwon) (`io.noties.markwon:core`)
- **Build system:** Gradle

---

## 🔧 Setup and Installation

### Prerequisites

- Android Studio **Ladybug or later**.
- A [Firebase Console](https://console.firebase.google.com/) account.
- An Android emulator or physical device running **Android 11 (API 30) or later**.

### 1. Clone the repository

```bash
git clone https://github.com/bsd-code/smart-fridge-firebase-ai.git
cd smart-fridge-firebase-ai
```

### 2. Configure Firebase

1. Create a project in the Firebase Console.
2. Enable **Email/Password** as a sign-in provider in Firebase Authentication.
3. Set up Cloud Firestore and configure security rules so users can access only their own data. Avoid using open test-mode rules for a production deployment.
4. Register your Android app in the Firebase project and download `google-services.json`.
5. Place `google-services.json` in the project's `app/` directory.
6. Configure Firebase AI Logic as required by your Firebase project.

### 3. Open and run the app

1. Open the project in Android Studio.
2. Sync the Gradle project using **Sync Project with Gradle Files**.
3. Run the app on an Android emulator or a connected physical device.

---

*Developed for Institut Marianao — A1: Cloud Backend module.*
