# my-tasks-and-expenses
A modern personal productivity and finance management web application built with HTML, CSS, JavaScript, and Firebase.
# My Tasks and Expenses

A modern, responsive personal productivity and finance management web application built with HTML, CSS, and JavaScript, with Firebase integration for authentication and real-time cloud data synchronization.

## Overview

**My Tasks and Expenses** is a web-based application designed to help users organize their daily tasks, track their income and expenses, and monitor their productivity through a single dashboard.

The application features a modern interface, dark and light themes, responsive layouts, and two data-storage modes: Firebase cloud synchronization and browser-based local storage.

## Features

### 1. Task Management
- Create, edit, and delete tasks.
- Organize tasks into three statuses:
  - To Do
  - In Progress
  - Done
- Drag and drop tasks between columns.
- Schedule upcoming tasks.
- Track overdue tasks.
- Categorize tasks (Work, Personal, Study, Health, Home, and Other).
- Search tasks by title or category.
- Undo recently deleted tasks.

### 2. Income and Expense Management
- Add income transactions.
- Record expenses.
- Categorize financial transactions.
- Track total income and expenses.
- Automatically calculate the available balance.
- Edit and delete financial transactions.

### 3. Dashboard and Statistics
- View a quick summary of tasks and finances.
- Monitor task completion over the last seven days.
- Analyze monthly expenses by category.
- View monthly financial totals.

### 4. Productivity Tools
- Pomodoro focus timer (25-minute focus session).
- Automatic 5-minute break after a focus session.
- Focus Mode for minimizing distractions.
- Task completion points and streak tracking.

### 5. User Authentication
- Create a new account.
- Sign in using email and password.
- Reset forgotten passwords.
- Continue without an account using Local Mode.

### 6. Data Storage and Synchronization
- Firebase Authentication.
- Firebase Realtime Database.
- Real-time synchronization across devices when signed in.
- LocalStorage support for browser-based data persistence.
- Export application data as a JSON backup.
- Import previously exported JSON backups.

### 7. Interface and Customization
- Dark and Light themes.
- Responsive design for desktop, tablet, and mobile.
- Hide financial balances for privacy.
- Modern dashboard with a purple-to-blue visual theme.

## Technologies Used

| Technology | Purpose |
|---|---|
| HTML5 | Application structure |
| CSS3 | Styling, animations, and responsive design |
| JavaScript (ES Modules) | Application logic and interactivity |
| Firebase Authentication | User authentication |
| Firebase Realtime Database | Cloud data storage and synchronization |
| LocalStorage | Local data persistence |
| Google Fonts (Inter) | Typography |

**Firebase SDK Version:** 11.10.0

## Project Structure

```text
my-tasks-and-expenses/
│
├── index.html
├── README.md
└── .gitignore
```

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/my-tasks-and-expenses.git
```

### 2. Open the Project

```bash
cd my-tasks-and-expenses
```

### 3. Run the Application

Since this project uses a single HTML file, no package installation or build process is required.

You can open `index.html` directly in your browser for local usage.

Alternatively, use Visual Studio Code with the Live Server extension:

1. Open the project folder in Visual Studio Code.
2. Right-click `index.html`.
3. Select **Open with Live Server**.

A local HTTP server is recommended for Firebase integration.

## Firebase Configuration

The application uses Firebase for authentication and cloud synchronization.

To configure your own Firebase project:

1. Visit [Firebase Console](https://console.firebase.google.com/).
2. Create a Firebase project.
3. Register a Web App.
4. Enable **Email/Password** under Authentication → Sign-in method.
5. Create a **Realtime Database**.
6. Copy your Firebase Web App configuration.
7. Replace the existing `firebaseConfig` object inside `index.html` with your own configuration.

### Realtime Database Security Rules

The application stores user data under:

```text
users/
  USER_UID/
    tasks/
    transactions/
    settings/
    meta/
```

Use the following rules to ensure that authenticated users can access only their own data:

```json
{
  "rules": {
    "users": {
      "$uid": {
        ".read": "auth != null && auth.uid === $uid",
        ".write": "auth != null && auth.uid === $uid"
      }
    }
  }
}
```

**Important:** Never use public read/write database rules in a deployed application. Configure Firebase Authorized Domains for your deployment domain.

## Data Backup and Restore

The application provides built-in data management tools:

- **Export:** Download your tasks, transactions, settings, and metadata as a JSON file.
- **Import:** Restore previously exported application data.
- **Delete:** Remove saved tasks and transactions.

It is recommended to export a backup regularly.

## Deployment

This application can be deployed using GitHub Pages.

1. Open your GitHub repository.
2. Navigate to **Settings**.
3. Select **Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select the `main` branch.
6. Select the `/ (root)` folder.
7. Click **Save**.

Your application will be published at:

```text
https://YOUR-USERNAME.github.io/my-tasks-and-expenses/
```

Make sure your Firebase project's Authorized Domains include your GitHub Pages domain.

## Browser Compatibility

The application is designed for modern browsers that support:
- JavaScript ES Modules.
- CSS Grid and Flexbox.
- LocalStorage.
- Firebase JavaScript SDK.

Recommended browsers: Google Chrome, Microsoft Edge, Firefox, and Safari.

## Important Notes

- Local Mode stores data only in the current browser.
- Firebase synchronization requires an internet connection.
- Data synchronization requires valid Firebase configuration and appropriate database security rules.
- The application currently uses a dynamically generated Web App Manifest. A separate service worker and offline caching system are not included.

## License

This project is available for educational and personal use. If you intend to distribute or reuse it, add an appropriate open-source license.

---

**My Tasks and Expenses**  
*Organize your tasks. Manage your money. Improve your productivity.*
