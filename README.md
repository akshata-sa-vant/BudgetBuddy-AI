# BudgetBuddy Full Project

This project implements the requested BudgetBuddy foundation and Milestone 2 flow using **FastAPI** for the backend and **React** for the frontend.

## Included

- Core relational models: User, Profile, Income, Expense, Budget, Savings Goal, Notification, Report
- SQLite local database and PostgreSQL-ready `DATABASE_URL`
- Alembic migration
- Password hashing and JWT authentication
- Role field (`student` / `admin`)
- Protected APIs and strict user ownership filtering
- Expense CRUD with only the six project categories
- Income CRUD with the three project income sources
- Monthly category-wise budget creation and retrieval
- Transaction dashboard totals, remaining amount, category totals, and recent activity
- React registration/login/protected dashboard skeleton
- Seed data and automated ownership/category tests

## Data model

```text
User 1 ─── 1 Profile
  │
  ├──── N Income
  ├──── N Expense
  ├──── N Budget
  ├──── N SavingsGoal
  ├──── N Notification
  └──── N Report

Expense.category ──> Food | Travel | Shopping | Education | Entertainment | Miscellaneous
Budget.category  ──> same six categories
Income.source    ──> Pocket Money | Scholarship | Freelance Income
```

## Start backend

See `backend/README.md`.

## Start frontend

See `frontend/README.md`.

## Important API ownership rule

Every financial query uses the authenticated user's ID. For example, expense update/delete queries require both the expense ID and `user_id == current_user.id`, so User A cannot operate on User B's record.
