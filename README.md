# 🧠 PHP Quiz Website

A dynamic web-based quiz application built with **PHP**, **MySQL**, **JavaScript**, and **HTML/CSS**. Users can register, log in, and take a timed multiple-choice quiz with scores tracked in real time.

---

## 📁 Project Structure

```
quiz-website/
├── login.php           # Login page (UI)
├── sign_up.php         # Sign up page (UI)
├── check_user.php      # Login authentication handler
├── signup_process.php  # Registration handler
├── ndex.php            # Main quiz page
├── image.php           # Alternate quiz UI (decorative version)
├── get_questions.php   # API endpoint — returns questions as JSON
├── script.js           # Quiz logic (timer, scoring, navigation)
├── style.css           # Main stylesheet
└── quiz_db.sql         # Database schema + seed data
```

---

## ⚙️ Tech Stack

| Layer      | Technology              |
|------------|-------------------------|
| Frontend   | HTML, CSS, JavaScript   |
| Backend    | PHP 8.x                 |
| Database   | MySQL / MariaDB         |
| Server     | Apache (XAMPP / WAMP)   |

---

## 🚀 Getting Started

### Prerequisites

- [XAMPP](https://www.apachefriends.org/) or WAMP installed
- PHP 8.x
- MySQL / MariaDB
- A browser

### Installation Steps

1. **Clone or download** this repository into your server's root folder:
   ```
   C:/xampp/htdocs/quiz-website/
   ```

2. **Start Apache and MySQL** from the XAMPP Control Panel.

3. **Import the database:**
   - Open `http://localhost/phpmyadmin`
   - Create a new database named `quiz_db`
   - Click **Import** and select `quiz_db.sql`
   - Click **Go**

4. **Open the app in your browser:**
   ```
   http://localhost/quiz-website/login.php
   ```

---

## 🔐 Authentication

- Users can **Sign Up** with a name, email, and numeric password.
- On login, credentials are verified against the `sign_up` table using prepared statements.
- Successful login redirects to the quiz page (`ndex.php`).

### Default Test Users (from seed data)

| Username  | Password |
|-----------|----------|
| meghraj   | 123      |
| deepak    | 123      |
| aditya    | 123      |
| karishma  | 123      |

---

## 📝 Quiz Features

- **10 multiple-choice questions** loaded from the database via `get_questions.php`
- **60-second countdown timer** per question — auto-advances on timeout
- **Score tracking** — correct answers counted in real time
- **Final score display** after all questions are answered
- Questions and options fetched dynamically using `fetch()` (no page reload)

---

## 🗄️ Database Schema

### `questions` table

| Column          | Type         | Description                     |
|-----------------|--------------|---------------------------------|
| id              | INT (PK, AI) | Unique question ID               |
| question_text   | VARCHAR(255) | The question                    |
| option1–option4 | VARCHAR(100) | Four answer choices             |
| correct_option  | INT          | Correct option number (1–4)     |

### `sign_up` table

| Column   | Type         | Description         |
|----------|--------------|---------------------|
| S_no     | INT (PK, AI) | User ID             |
| username | TEXT         | Username            |
| password | INT(20)      | Numeric password    |
| email    | VARCHAR(30)  | User email          |

---

## ⚠️ Known Issues & Improvements

| Issue | Recommendation |
|-------|----------------|
| Passwords stored as plain integers | Use `password_hash()` and `password_verify()` |
| No session management after login | Add `$_SESSION` to maintain auth state |
| `ndex.php` filename typo | Rename to `index.php` |
| `signup_process.php` queries wrong column (`name` vs `username`) | Fix to match DB schema |
| No CSRF protection on forms | Add CSRF tokens |
| Password field uses `type="number"` | Change to `type="password"` for masking |

---

## 📸 Pages Overview

| Page           | File              | Description                          |
|----------------|-------------------|--------------------------------------|
| Login          | `login.php`       | User login form                      |
| Sign Up        | `sign_up.php`     | New user registration form           |
| Quiz           | `ndex.php`        | Main quiz UI with timer and scoring  |
| Auth Check     | `check_user.php`  | Handles login POST and redirects     |
| Registration   | `signup_process.php` | Handles signup POST              |
| Questions API  | `get_questions.php` | Returns all questions as JSON      |

---

## 👤 Author

**Meghraj Parashar **   
🔗 [GitHub: MEGHRAJPARASHAR](https://github.com/MEGHRAJPARASHAR)  
🌐 [Portfolio: meghrajparashar](https://meghrajparashar.github.io)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
