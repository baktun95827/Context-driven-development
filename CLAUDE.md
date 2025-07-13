# === PROJECT CONSTITUTION ===

## 1. Project Brief

We are building a web application as defined in VISION.md. The backend will be a FastAPI server, and the frontend will be a React single-page application.

## 2. Tech Context

- **Backend:** Python 3.11+, FastAPI, Pydantic V2, PostgreSQL with SQLAlchemy.
- **Frontend:** React (Vite), TypeScript, Tailwind CSS, Zustand for state management.
- **Testing:** Pytest for backend, Vitest and React Testing Library for frontend.
- **Tooling:** Docker for containerization, Ruff for linting/formatting.

## 3. System Patterns

- **TDD is Mandatory:** All new logic must be introduced via a failing test first.
- **API Design:** RESTful principles. Clear, noun-based endpoints. All responses must be JSON.
- **Error Handling:** Backend must use a centralized exception handler to return consistent, structured JSON error responses.
- **Code Style:** All Python code must be formatted with `ruff format`. No new code will be accepted if `ruff check .` fails.
