# Incident Reporting System (IRS)

A lightweight, client-side web application for students to submit incident reports and for staff members to review, manage, and track those logs. Built with HTML, CSS, and vanilla JavaScript using `localStorage` for data persistence.

## Features

### Student Portal
* **Account Creation & Authentication:** Students can sign up with a username, Gmail address, and password, sign in with a "Remember me" option, and reset forgotten passwords.
* **Incident Report Submission:** File reports with date, time, Student ID (e.g., `AUJRC-00000-0000`), incident details, and optional photo attachments (up to 50 MB total).
* **My Reports View:** View submitted reports that are currently pending review.
* **Profile Settings:** Update recovery Gmail, change password, upload or remove a profile photo, switch between Light/Dark/System themes, or delete the account.

### Staff Portal (File Cabinet)
* **Unified Login:** Staff members sign in through the standard login screen using authorized staff credentials.
* **File Cabinet Dashboard:** Quickly filter and search reports by Student ID, reporter username, or incident details, and view live counts across three status drawers:
  * **Pending**
  * **Taking Action**
  * **Finished**
* **Incident Logs Management:** Inspect full report details, attached photo proof (with download support), and approximate IP-based geolocation metadata. Staff can update report statuses individually or in bulk, delete completed logs, and export all reports to JSON (`incident-reports.json`).
* **User Accounts Directory:** Search and filter registered student and built-in staff accounts, inspect last login timestamps and GeoIP information, and remove student accounts if needed.

## Getting Started

1. **Clone or Download the Repository:**
   ```bash
   git clone https://github.com/rain-coding-journey/IRS-Incident-Reporting-System.git
   cd IRS-Incident-Reporting-System
   ```
2. **Run the Application:**
   * Open `index.html` directly in a web browser, **or**
   * Serve the folder using a local development server (recommended so IP-based geolocation requests via `fetch` are not restricted by `file://` browser policies):
     ```bash
     npx serve .
     ```
     or with Python:
     ```bash
     python -m http.server 8000
     ```

## Staff Access

Staff access is handled directly through the main **Sign In** form (`#loginForm`). When a staff username and matching password are submitted, the application routes the session to the staff File Cabinet dashboard instead of the student portal.

* **Built-in Staff Usernames (case-insensitive):**
  * `aujrc-osa`
  * `aujrc-prefect`
* **Note on Storage & Security:** All user accounts, passwords, and incident reports are stored locally in the browser via `localStorage` (`incidentUsers`, `incidentReports`, `rememberedUsername`, and `incidentTheme`). Because credentials and data are stored client-side without a backend server, this project is intended for local demonstrations, prototyping, or educational use rather than production deployment.

## Project Structure

* `index.html` — Main single-page application containing all views (Sign In, Sign Up, Password Reset, Student/Staff Dashboards, Incident Form, Logs, User Accounts, and Profile Settings), embedded styles, and application logic.
* `animation.css` — External stylesheet for UI animations (referenced in `index.html`).
