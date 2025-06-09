
---

# 📱 SaveSavvy

**SaveSavvy** is a modern Android application that helps users track, analyze, and manage their monthly expenses. It empowers users to take control of their finances with tools like goal-setting, PDF reports, visual charts, and more—all built on Firebase.

---

## 🧾 Project Description

SaveSavvy allows users to:

* Log expenses by category
* View monthly summaries
* Set personalized budget goals
* Generate downloadable PDF reports
* See data visualizations via charts

The app is developed in **Android Studio** and integrates:

* Firebase Authentication
* Firestore (Cloud Firestore Database)
* Firebase Storage

SaveSavvy is built for **simplicity, speed, and scalability**, ensuring each user has a personalized financial management experience.

---

## 📚 Table of Contents

* [🚀 How to Install and Run](#-how-to-install-and-run)
* [📖 How to Use](#-how-to-use)
* [📱 Application Pages & Features](#-application-pages--features)
* [🔥 Firebase Structure](#-firebase-structure)
* [🙏 Credits](#-credits)
* [📄 License](#-license)

---

## 🚀 How to Install and Run

1. Clone or download this repository.
2. Open the project in **Android Studio**.
3. Link to Firebase via **Tools > Firebase**.
4. Enable the following Firebase services:

   * ✅ Email/Password Authentication
   * ✅ Firestore Database
   * ✅ Firebase Storage
5. Set **Firebase security rules** for user-based access control.
6. Run the app on an emulator or Android device (API level 21+).

---

## 📖 How to Use

1. **Sign up or log in** to your account.
2. **Navigate** using the bottom navigation bar.
3. Use features like:

   * 📥 Add Expense
   * 📊 Track Budget
   * ⚙️ Set Goals
   * 📂 Manage Categories
   * 🧾 Generate PDF Report

---

## 📱 Application Pages & Features

### 🔐 Sign In Page
![image](https://github.com/user-attachments/assets/47d3d0b1-b147-4c0f-9fd0-e60fc92cce82)



* Fields: Email, Password
* Firebase: `signInWithEmailAndPassword`
* Access restricted to authenticated users.

---

### 📝 Sign Up Page
![image](https://github.com/user-attachments/assets/8ccffeee-fd0e-4c8d-b131-0449d3e5ea2a)



* Fields: Email, Password, Confirm Password
* Firebase: `createUserWithEmailAndPassword`
* Auto-initializes user data in Firestore.

---

### 🏠 Home Dashboard
![image](https://github.com/user-attachments/assets/162662f5-bdb4-4ff2-9eda-d4bd27e069e4)


* Displays motivational tips & welcome messages.
* Encourages good financial habits.

---

### ➕ Add Expense Page
![image](https://github.com/user-attachments/assets/d57ba123-1741-4858-a583-350dfd0cf18e)


* Inputs: Amount, Description, Date, Category, Receipt Image
* Saves data to `users/{userId}/expenses`
* Uploads image to Firebase Storage

---

### 💳 Expense Page
![image](https://github.com/user-attachments/assets/8353064c-a9eb-4726-9609-1299ee8c8dfc)   ![image](https://github.com/user-attachments/assets/791d7015-1111-4c3f-ae52-403abcb5b655)


* Filter expenses by:

  * 📅 Date
  * 📂 Category
* 📈 View total expense & per-category chart
* ⚠️ Budget warnings
* 🗑️ Delete expenses
* Firebase:

  * Reads: `users/{userId}/expenses`
  * Reads goals: `goals/{userId}`

---

### 📊 Balance Overview Page
![image](https://github.com/user-attachments/assets/1984a829-4a0a-4825-977f-bb6858b89698)


* Monthly summary:

  * 🍰 Pie chart per category
  * 📏 Progress bar (against budget)
  * 📄 Generate monthly PDF report
* Firebase:

  * Reads: `users/{userId}/expenses`
  * Categories: `users/{userId}/categories`
  * Goals: `goals/{userId}`

---

### 🎯 Goal Settings Page
![image](https://github.com/user-attachments/assets/01e7afd3-da0b-4468-8881-2c1e0801d532)


* Define `minGoal` and `maxGoal`
* Firebase: `goals/{userId}`

---

### 📂 Category Manager
![image](https://github.com/user-attachments/assets/81f62f11-9d43-44d4-8f97-f5581844ed81)


* Add / delete / refresh categories
* Firebase: `users/{userId}/categories`
* Duplicate check before adding

---

### 🧭 Bottom Navigation (BaseActivity)
![image](https://github.com/user-attachments/assets/679c28d7-88c7-46f8-a341-4e9a09d78147)


* Accessible across all pages
* Tabs: Home, Categories, Goals, Expenses, Add Expense
* Highlights the current tab with **gold accent**

---

## 🔥 Firebase Structure

```
users (collection)
└── {userId} (document)
    ├── categories (collection)
    │   └── {categoryId}: { name }
    ├── expenses (collection)
    │   └── {expenseId}: { amount, date, description, category, imageUrl }

goals (collection)
└── {userId}: { minGoal, maxGoal }
```

* 🔒 All user data is isolated via `uid`
* 🖼️ Images stored in Firebase Storage and linked via `imageUrl`

---

## 🙏 Credits

Developed by:

* **Cameron Totham**
* **Makwande Ntombela**

### 🔗 Resources Used:

* [Firebase Documentation](https://firebase.google.com/docs)
* [MPAndroidChart Library](https://github.com/PhilJay/MPAndroidChart)
* [Android Developers Docs](https://developer.android.com)

> Special thanks to the Android Studio and Firebase communities 🙌

---

## 📄 License

This project is licensed under the **MIT License**. You may use, modify, and distribute with attribution.


---



**Useful resources for code:**

Bing. (2025). Android studio roomdb - Bing. [online] Available at: <https://www.bing.com/search?pglt=297&q=Android+studio+roomdb&cvid=5c42d94d53294caf97da015011d52dff&gs_lcrp=EgRlZGdqKgYIABBFGDkyBggAEEUYOTIGCAEQABhAMgYIAhAAGEAyBggDEAAYQDIGCAQQABhAMgYIBRAAGEAyBggGEAAYQDIGCAcQABhAMgYICBAAGEDSAQg2MzE4ajBqMagCALACAA&FORM=ANNTA1&PC=LCTS> [Accessed 25 April 2025].

Firebase. (2019). Add Firebase to your Android project | Firebase. [online] Available at: <https://firebase.google.com/docs/android/setup.> [Accessed 25 April 2025]

Jalaludin, M. (2018). How to Create User Interface Login & Register with Android Studio. [online] android.dev. Available at: <https://medium.com/muhamadjalaludin/how-to-create-user-interface-login-register-with-android-studio-34da847b05b2.> [Accessed 23 April 2025]

Romain Girou. (2024). Expense Tracker App #1 • Flutter • Firebase • Bloc. [online] YouTube. Available at: <https://www.youtube.com/watch?v=yDyg0A4wL9Y> [Accessed 29 April 2025].



