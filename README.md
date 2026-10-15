# Thobic Backend

![Thobic Banner](./Image/ThobicBanner.png)

A REST API for a platform that simplifies ordering and tailoring Thawb by connecting clients, tailoring shops, and material providers.

[Live Website](https://thobic.vercel.app) · [Frontend Repository](https://github.com/AhKhamis/Thobic-Frontend) · [Backend Repository](https://github.com/AhKhamis/Thobic-Backend) · [API Documentation](https://thobic-backend.onrender.com/docs)

---

## Table of Contents

- [Overview](#overview)
- [Core Idea](#core-idea)
- [Live Deployment](#live-deployment)
- [Repositories](#repositories)
- [Features and User Stories](#features-and-user-stories)
- [Entity Relationship Diagram](#entity-relationship-diagram)
- [Wireframes](#wireframes)
- [Frontend Architecture](#frontend-architecture)
- [Backend Architecture](#backend-architecture)
- [Project Structure](#project-structure)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [API Documentation](#api-documentation)
- [API Route Reference](#api-route-reference)
- [User Roles](#user-roles)
- [Future Development](#future-development)
- [Team](#team)

---

## Overview

Thobic aims to reduce the need for clients to visit tailoring shops in person to manage measurements, choose materials, discuss prices, and arrange delivery. The backend provides server-side functionality for authentication, profiles, measurements, materials, shops, and order workflows.

## Core Idea

The platform connects clients, tailoring shops, and external material providers through a centralized digital system. It aims to simplify Thawb orders, store measurements for reuse, support material requests from external providers, and help tailors and providers manage inventory and order statuses.

---

## Live Deployment

- **Live Website:** [Thobic](https://thobic.vercel.app)
- **Backend API:** [Thobic Backend](https://thobic-backend.onrender.com)
- **Swagger UI:** [Interactive API Documentation](https://thobic-backend.onrender.com/docs)
- **ReDoc:** [Alternative API Documentation](https://thobic-backend.onrender.com/redoc)

## Repositories

- **Frontend Repository:** [Thobic-Frontend](https://github.com/AhKhamis/Thobic-Frontend)
- **Backend Repository:** [Thobic-Backend](https://github.com/AhKhamis/Thobic-Backend)

---

## Features and User Stories

The following user stories describe intended functionality. Availability depends on the current implementation.

### Client

- Register, sign in, and sign out securely.
- Create a Thawb order and select a tailor or shop branch.
- Select available materials or request material from an external provider.
- Browse and filter materials.
- Add, update, and delete saved measurements.
- Edit or cancel an order where permitted.
- Approve or reject proposed prices and delivery deadlines.
- Confirm delivery and browse tailoring shops.

### Admin

- Sign in and sign out securely.
- Create tailor and provider accounts.

### Tailor

- View assigned orders and their statuses.
- Accept or reject incoming orders and propose a price and deadline.
- Update order statuses and shop availability.
- Manage inventory and material availability.
- View material orders and confirm material delivery.

### Provider

- Manage material inventory.
- View incoming material orders.
- Accept or reject material orders and update their statuses.

---

## Entity Relationship Diagram

The ERD illustrates the main entities and relationships used by the platform.

![Thobic Entity Relationship Diagram](./Image/erd.png)

---

## Wireframes

The wireframes illustrate planned interfaces for clients, tailors, providers, and administrators.

![Thobic Wireframes](./Image/ThobicW.png)

---

## Frontend Architecture

The frontend is built with React and communicates with this API for authentication and application data.

![Thobic Components Hierarchy](./Image/c1.png)

![Thobic Frontend Architecture](./Image/co2.png)

See the [Thobic Frontend Repository](https://github.com/AhKhamis/Thobic-Frontend) for frontend implementation details.

---

## Backend Architecture

The backend uses FastAPI and SQLAlchemy, with PostgreSQL for persistence.

### Main Responsibilities

- User registration, authentication, and access control.
- User and profile management.
- Client measurement management.
- Thawb order management.
- Shop and tailor management.
- Material inventory and material-order management.
- Order status management.
- Database migrations and persistence.

---

## Project Structure

Simplified overview; actual files may vary as the project evolves.

```text
Thobic-Backend/
├── config/
├── controllers/
├── migrations/
├── models/
├── .env
├── .gitignore
├── alembic.ini
├── database.py
├── main.py
├── Pipfile
├── Pipfile.lock
└── README.md
```

---

## Technologies Used

### Backend

- **Python** — Backend programming language.
- **FastAPI** — REST API framework.
- **Uvicorn** — ASGI server.
- **SQLAlchemy** — ORM and database operations.
- **Alembic** — Database migrations.
- **Pydantic** — Data validation and serialization.
- **PyJWT** — Token handling.
- **Passlib and bcrypt** — Password hashing.
- **python-dotenv** — Environment variable management.
- **Pipenv** — Dependency and virtual environment management.

### Database

- **PostgreSQL** — Relational database.
- **psycopg2-binary** — PostgreSQL driver.

### Development and Deployment

- **Git and GitHub** — Version control.
- **Render** — Backend deployment.
- **Vercel** — Frontend deployment.
- **Swagger UI and ReDoc** — API documentation.

---

## Getting Started

### Prerequisites

- Python version compatible with the project's Pipfile.
- Pipenv.
- PostgreSQL.
- Git.

### 1. Clone the Repository

```bash
git clone https://github.com/AhKhamis/Thobic-Backend.git
cd Thobic-Backend
```

### 2. Install Dependencies

```bash
pipenv install
```

### 3. Configure Environment Variables

Create a `.env` file in the project root using the variables listed below.

### 4. Apply Database Migrations

```bash
pipenv run alembic upgrade head
```

### 5. Start the Development Server

```bash
pipenv run uvicorn main:app --reload
```

Local URLs:

- **API:** `http://127.0.0.1:8000`
- **Swagger UI:** `http://127.0.0.1:8000/docs`
- **ReDoc:** `http://127.0.0.1:8000/redoc`

---

## Environment Variables

| Variable       | Purpose                                                |
| -------------- | ------------------------------------------------------ |
| `DATABASE_URL` | PostgreSQL connection string.                          |
| `JWT_SECRET`   | Secret used to sign or validate authentication tokens. |
| `CORS_ORIGINS` | Comma-separated list of permitted frontend origins.    |

Example:

```env
DATABASE_URL=your_postgresql_connection_string
JWT_SECRET=your_secret_key
CORS_ORIGINS=http://localhost:5173,https://thobic.vercel.app
```

**Security:** Never commit real credentials, JWT secrets, or other sensitive values to GitHub. Keep `.env` excluded from version control.

---

## API Documentation

- **Production Swagger UI:** [Open Swagger UI](https://thobic-backend.onrender.com/docs)
- **Production ReDoc:** [Open ReDoc](https://thobic-backend.onrender.com/redoc)
- **Local Swagger UI:** `http://127.0.0.1:8000/docs`

Swagger UI shows the routes and schemas registered in the running application. Use it as the source of truth if a route below differs from the deployed implementation.

---

## API Route Reference

This high-level reference is based on the endpoints documented in the frontend integration. Verify exact methods, access rules, and schemas in [Swagger UI](https://thobic-backend.onrender.com/docs).

### Authentication

| Method | Endpoint            | Purpose                                  |
| ------ | ------------------- | ---------------------------------------- |
| `POST` | `/api/register`     | Register a client account.               |
| `POST` | `/api/login`        | Authenticate a user.                     |
| `GET`  | `/api/current_user` | Retrieve the current user's information. |

### Admin

| Method | Endpoint           | Purpose                              |
| ------ | ------------------ | ------------------------------------ |
| `POST` | `/api/admin/users` | Create a tailor or provider account. |

### Profiles

| Method | Endpoint           | Purpose                              |
| ------ | ------------------ | ------------------------------------ |
| `POST` | `/api/profiles`    | Create a profile.                    |
| `GET`  | `/api/profiles/me` | Retrieve the current user's profile. |
| `PUT`  | `/api/profiles/me` | Update the current user's profile.   |

### Client Measurements

| Method   | Endpoint               | Purpose                      |
| -------- | ---------------------- | ---------------------------- |
| `POST`   | `/api/measurements`    | Save measurements.           |
| `GET`    | `/api/measurements/me` | Retrieve saved measurements. |
| `PUT`    | `/api/measurements/me` | Update saved measurements.   |
| `DELETE` | `/api/measurements/me` | Delete saved measurements.   |

### Materials

| Method   | Endpoint                       | Purpose                                |
| -------- | ------------------------------ | -------------------------------------- |
| `POST`   | `/api/materials/upload-image`  | Upload a material image.               |
| `POST`   | `/api/materials`               | Add a material.                        |
| `GET`    | `/api/materials`               | Browse and filter materials.           |
| `GET`    | `/api/materials/mine`          | Retrieve the current user's materials. |
| `GET`    | `/api/materials/{material_id}` | Retrieve material details.             |
| `PUT`    | `/api/materials/{material_id}` | Update a material.                     |
| `DELETE` | `/api/materials/{material_id}` | Soft-delete a material.                |

Documented filters include `source_id`, `source_role`, `texture`, `pattern`, `season`, `stand`, `colour`, `min_price`, and `max_price`.

### Thawb Orders

| Method   | Endpoint                                | Purpose                          |
| -------- | --------------------------------------- | -------------------------------- |
| `POST`   | `/api/orders`                           | Create a Thawb order.            |
| `GET`    | `/api/orders/my-orders`                 | Retrieve relevant orders.        |
| `GET`    | `/api/orders/{order_id}`                | Retrieve order details.          |
| `PUT`    | `/api/orders/{order_id}`                | Edit an order where permitted.   |
| `DELETE` | `/api/orders/{order_id}`                | Delete an order where permitted. |
| `PATCH`  | `/api/orders/{order_id}/tailor-accept`  | Propose price and deadline.      |
| `PATCH`  | `/api/orders/{order_id}/tailor-reject`  | Reject an order.                 |
| `PATCH`  | `/api/orders/{order_id}/client-respond` | Respond to a proposal.           |
| `PATCH`  | `/api/orders/{order_id}/in-progress`    | Start tailoring.                 |
| `PATCH`  | `/api/orders/{order_id}/ready`          | Mark an order ready.             |
| `PATCH`  | `/api/orders/{order_id}/on-the-way`     | Mark an order as on the way.     |
| `PATCH`  | `/api/orders/{order_id}/delivered`      | Confirm delivery.                |

### Material Orders

| Method | Endpoint                                              | Purpose                                                |
| ------ | ----------------------------------------------------- | ------------------------------------------------------ |
| `GET`  | `/api/material-orders`                                | Retrieve material orders.                              |
| `GET`  | `/api/material-orders/{material_order_id}`            | Retrieve order details.                                |
| `PUT`  | `/api/material-orders/{material_order_id}/accept`     | Accept an order and provide an expected delivery date. |
| `PUT`  | `/api/material-orders/{material_order_id}/reject`     | Reject a material order.                               |
| `PUT`  | `/api/material-orders/{material_order_id}/on-the-way` | Mark materials as shipped.                             |
| `PUT`  | `/api/material-orders/{material_order_id}/delivered`  | Confirm material delivery.                             |

### Shops

| Method | Endpoint               | Purpose                                        |
| ------ | ---------------------- | ---------------------------------------------- |
| `GET`  | `/api/shops`           | Browse and filter tailoring shops.             |
| `GET`  | `/api/shops/{shop_id}` | Retrieve shop profile and available materials. |

---

## User Roles

| Role         | Main Responsibilities                                                                 |
| ------------ | ------------------------------------------------------------------------------------- |
| **Client**   | Browse shops and materials, manage measurements, create orders, and confirm delivery. |
| **Tailor**   | Manage shop profile, inventory, orders, prices, deadlines, and statuses.              |
| **Provider** | Manage material inventory and material orders.                                        |
| **Admin**    | Create tailor and provider accounts.                                                  |

Access to specific operations depends on permissions implemented in the backend.

---

## Future Development

Potential enhancements include online payments, notifications, real-time order tracking, advanced material search, customer reviews, delivery management, analytics, appointment booking, and mobile application support. These are potential enhancements and should not be considered implemented unless available in the application.

---

## Team

Thobic is a software engineering project focused on simplifying the traditional Thawb ordering and tailoring process through a centralized digital platform.

---

## Project Links

- [Live Website](https://thobic.vercel.app)
- [Frontend Repository](https://github.com/AhKhamis/Thobic-Frontend)
- [Backend Repository](https://github.com/AhKhamis/Thobic-Backend)
- [Swagger UI](https://thobic-backend.onrender.com/docs)
- [ReDoc](https://thobic-backend.onrender.com/redoc)
