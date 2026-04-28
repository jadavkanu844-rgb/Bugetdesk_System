# BudgetDesk System 💼

![Django](https://img.shields.io/badge/Django-5.1.8-092E20?style=for-the-badge&logo=django&logoColor=white)
![React](https://img.shields.io/badge/React-18.3.1-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-5.4-1F1B4D?style=for-the-badge&logo=vite&logoColor=FFD62E)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.4-0F172A?style=for-the-badge&logo=tailwind-css&logoColor=38BDF8)
![JWT Auth](https://img.shields.io/badge/Auth-JWT_Cookies-0F766E?style=for-the-badge)
![PDF Export](https://img.shields.io/badge/Invoices-PDF_Export-B91C1C?style=for-the-badge)

BudgetDesk System is a comprehensive full-stack financial management application designed for freelancers, small business owners, and service teams. Manage invoices, track expenses, monitor cash flow, and gain insights into your business performance—all from a single, intuitive dashboard.

Detailed technical documentation is available in [PROJECT_DOCUMENTATION.md](./PROJECT_DOCUMENTATION.md).

## Live Demo

[View Live Demo](https://budget-desk-system.vercel.app/)

## Features

- Secure user authentication with JWT-based sessions stored in HttpOnly cookies
- Create, edit, manage, and track invoices with payment status visibility
- Download professional invoice PDFs for client sharing and record keeping
- Track expenses by category and month to keep spending organized
- Monitor income, expenses, and profit from a clean dashboard with charts
- Filter ledger views with shareable query-based search and sorting

## Quick Start

### For Development

```bash
# Clone the repository
git clone https://github.com/jadavkanu844-rgb/Bugetdesk_System.git
cd BudgetDesk_System-main

# Backend setup (Terminal 1)
cd backend
python -m venv venv
venv\Scripts\activate  # On macOS/Linux: source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver

# Frontend setup (Terminal 2)
cd frontend
npm install
npm run dev
```

Visit `http://localhost:5173` to see the application.

## Tech Stack

| Layer | Tools |
| --- | --- |
| Frontend | `React` `Vite` `Tailwind CSS` `Axios` `React Router` `Recharts` |
| Backend | `Django` `Django REST Framework` `Simple JWT` `django-filter` `ReportLab` |
| Database | `SQLite` for local development, `PostgreSQL` ready for production |
| Architecture | Monorepo structure with separate frontend and backend apps |

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/jadavkanu844-rgb/Bugetdesk_System.git
cd BudgetDesk_System-main
```

### 2. Set up the backend

SQLite is enabled by default, so you can run the backend locally without extra database setup.

```bash
cd backend
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

Optional local environment file:

```env
SECRET_KEY=change-me
DEBUG=True
USE_SQLITE=True
```

Backend runs on `http://127.0.0.1:8000`.

### 3. Set up the frontend

Open a new terminal:

```bash
cd frontend
npm install
npm run dev
```

Frontend runs on `http://localhost:5173`.

### 4. Start using the app

- Register a new account from the frontend
- Log in to access the protected dashboard
- Create invoices, track expenses, and review monthly performance

## Free Hosting

The most practical free setup for this project is:

- `Render` for the Django API
- `Render Static Site` for the React frontend
- `Neon` for free PostgreSQL

This repo now includes:

- `render.yaml` for Render blueprint deployment
- `backend/.env.example` with production variable examples
- `frontend/public/_redirects` for SPA routing on refresh

For production, make sure these values are updated:

- `VITE_API_BASE_URL` to your deployed backend URL
- `ALLOWED_HOSTS` to your backend domain
- `CORS_ALLOWED_ORIGINS` and `CSRF_TRUSTED_ORIGINS` to your frontend domain
- `JWT_COOKIE_SECURE=True`
- `JWT_COOKIE_SAMESITE=None`
- `USE_SQLITE=False` with your Postgres credentials

## Folder Structure

```text
BudgetDesk_System-main/
|-- backend/
|   |-- apps/
|   |   |-- expenses/
|   |   |   |-- models.py
|   |   |   |-- views.py
|   |   |   |-- serializers.py
|   |   |   |-- urls.py
|   |   |   |-- filters.py
|   |   |   `-- migrations/
|   |   |-- invoices/
|   |   |   |-- models.py
|   |   |   |-- views.py
|   |   |   |-- serializers.py
|   |   |   |-- services.py
|   |   |   |-- pdf.py
|   |   |   |-- urls.py
|   |   |   |-- filters.py
|   |   |   `-- migrations/
|   |   `-- users/
|   |       |-- models.py
|   |       |-- views.py
|   |       |-- serializers.py
|   |       |-- authentication.py
|   |       |-- urls.py
|   |       `-- migrations/
|   |-- config/
|   |   |-- settings.py
|   |   |-- urls.py
|   |   |-- wsgi.py
|   |   |-- asgi.py
|   |   `-- exception_handler.py
|   |-- manage.py
|   |-- requirements.txt
|   |-- .env.example
|   `-- db.sqlite3
|-- frontend/
|   |-- src/
|   |   |-- api/
|   |   |   |-- authService.js
|   |   |   |-- client.js
|   |   |   |-- dashboardService.js
|   |   |   |-- expenseService.js
|   |   |   `-- invoiceService.js
|   |   |-- auth/
|   |   |   |-- AuthContext.jsx
|   |   |   `-- ProtectedRoute.jsx
|   |   |-- components/
|   |   |   |-- charts/
|   |   |   |-- common/
|   |   |   `-- forms/
|   |   |-- pages/
|   |   |   |-- DashboardPage.jsx
|   |   |   |-- ExpensesPage.jsx
|   |   |   |-- InvoicesPage.jsx
|   |   |   |-- LoginPage.jsx
|   |   |   `-- RegisterPage.jsx
|   |   |-- router/
|   |   |   `-- AppRouter.jsx
|   |   |-- layouts/
|   |   |   `-- DashboardLayout.jsx
|   |   |-- utils/
|   |   |   `-- formatters.js
|   |   |-- main.jsx
|   |   `-- index.css
|   |-- index.html
|   |-- package.json
|   |-- vite.config.js
|   |-- tailwind.config.js
|   |-- postcss.config.js
|   `-- public/
|-- PROJECT_DOCUMENTATION.md
|-- README.md
|-- render.yaml
`-- package-lock.json
```

## Future Improvements

- Recurring invoices and automated billing cycles
- Email delivery and payment reminders for invoices
- Advanced financial reporting and analytics
- CSV/Excel export capabilities
- Multi-user workspaces with team collaboration
- Payment gateway integration (Stripe, PayPal)
- Mobile app for iOS and Android
- Automated invoice reminders and follow-ups
- Tax report generation
- Budget forecasting and planning tools

## Support & Documentation

For detailed technical information, architecture decisions, and advanced setup guides, please refer to [PROJECT_DOCUMENTATION.md](./PROJECT_DOCUMENTATION.md).

## License

This project is open source and available under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Contact & Support

For questions, bug reports, or feature requests, please open an issue on the GitHub repository.

---

**Built with ❤️ for freelancers and small business owners**
