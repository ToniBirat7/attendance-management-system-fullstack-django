# Attendance Management System (Django)

Full-stack Django application for managing courses, students, and attendance. Teachers can take attendance from a calendar view and export weekly reports to Excel.

## Features
- User authentication (login, logout, password reset) and basic registration.
- Admin dashboard for managing teachers, students, courses, and class assignments.
- Teacher profile management with profile image upload.
- Attendance capture by date from a calendar view.
- Weekly attendance report view.
- Attendance report export to Excel.

## Tech Stack
- Django 4.2
- SQLite (default)
- HTML/CSS templates with static assets
- Pandas + OpenPyXL for Excel export

## Project Structure
```
ams/                 Django project settings and URLs
auth_app/            Authentication and admin management flows
Attendance/          Core models (Person, Course, Student, Class) and teacher views
calendar_app/        Attendance tracking, calendar view, reporting, export
templates/           HTML templates
static/              Static assets (CSS, images)
media/               Uploaded media (profile images)
```

## Prerequisites
- Python 3.10+ recommended
- pip / virtualenv

## Setup
1. Create and activate a virtual environment:
   ```
   python -m venv .venv
   source .venv/bin/activate
   ```
2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```
3. Run migrations:
   ```
   python manage.py migrate
   ```
4. (Optional) Create a superuser for Django admin:
   ```
   python manage.py createsuperuser
   ```

## Run the App
```
python manage.py runserver
```
Open `http://127.0.0.1:8000/` in your browser.

## Key User Flows
- **Registration/Login**: `auth/` routes handle user registration and login.
- **Admin Management**: Use the admin page to add teachers, courses, students, and assign students to classes.
- **Teacher Home**: Teachers see their course list and can launch the calendar view.
- **Take Attendance**: Select a course → calendar → date to mark students as present/absent.
- **Reports**: View weekly attendance summaries and download an Excel report.

## Useful Routes
- `/auth/login/` – Login
- `/auth/admin-page/` – Admin dashboard
- `/attendance/logged-in/` – Teacher course list
- `/calendar/display-calendar/{course_id}` – Calendar view (course_id is an integer; corresponds to Django route `display-calendar/<int:course_id>`)

## Tests
Run the test suite:
```
python manage.py test
```

## Notes
- Default database is SQLite (`db.sqlite3`).
- Uploaded media is stored in `/media`.
- For production, set `DEBUG=False`, configure `ALLOWED_HOSTS`, and keep `SECRET_KEY` secret (never commit it to version control).
