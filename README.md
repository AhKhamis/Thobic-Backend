# Thobic Backend

![Thobic Banner](./Image/ThobicBanner.png)

Thobic is a web-based platform designed to simplify and automate the process of ordering and tailoring Thawb (traditional Arabic men's clothing).

The platform connects clients, tailoring shops, and external material providers through a centralized digital system, making it easier to manage orders, measurements, materials, and order statuses.

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
- [User Roles](#user-roles)
- [Future Development](#future-development)
- [Team](#team)

---

## Overview

Thobic aims to reduce the need for clients to visit tailoring shops in person to manage measurements, choose materials, discuss prices, and arrange order delivery.

The platform also supports communication between tailoring shops and external material providers when the required materials are unavailable in the tailor's inventory.

The backend provides the API and server-side functionality required to support the platform, including authentication, database operations, user management, orders, measurements, and materials.

## Core Idea

The website automates the process of ordering and tailoring Thawb by connecting clients with tailoring shops and external material providers.

The platform aims to:

- Simplify the creation and management of Thawb orders.
- Allow clients to select materials from a tailor's available inventory.
- Support requests for materials from external providers.
- Store and reuse client measurements for future orders.
- Reduce unnecessary physical visits to tailoring shops.
- Help tailors manage orders, materials, pricing, and deadlines.
- Allow material providers to manage their inventory and incoming material orders.
- Organize the order lifecycle through status updates.

---

## Live Deployment

- **Live Website:** [Thobic](https://thobic.vercel.app)
- **Backend API:** [Thobic Backend](https://thobic-backend.onrender.com)
- **Interactive API Documentation:** [Swagger UI](https://thobic-backend.onrender.com/docs)

## Repositories

- **Frontend Repository:** [Thobic-Frontend](https://github.com/AhKhamis/Thobic-Frontend)
- **Backend Repository:** [Thobic-Backend](https://github.com/AhKhamis/Thobic-Backend)

---

## Features and User Stories

The following user stories describe the platform's intended functionality. Individual features may depend on their implementation status.

### Client

- As a client, I want to sign up, sign in, and sign out securely.
- As a client, I want to create an order and assign it to a specific tailor or tailoring shop branch.
- As a client, I want to select a material for my order.
- As a client, I want to request material from an external provider if I cannot find a suitable option in the tailor's inventory.
- As a client, I want to browse and filter available materials.
- As a client, I want to add and save my measurements for future orders.
- As a client, I want to update my saved measurements.
- As a client, I want to delete my measurements.
- As a client, I want to book an appointment for measurements at a physical location.
- As a client, I want to update order details before the tailor accepts the order.
- As a client, I want to cancel an order before it is accepted by the tailor.
- As a client, I want to approve or reject the proposed price and delivery deadline.
- As a client, I want to confirm that my order has been delivered.
- As a client, I want to browse tailoring shops and view their profiles.
- As a client, I want to filter tailoring shops to find a suitable option.

### Admin

- As an admin, I want to sign in and sign out securely.
- As an admin, I want to create tailor accounts.
- As an admin, I want to create provider accounts.

### Tailor

- As a tailor, I want to sign in and sign out securely.
- As a tailor, I want to view all orders assigned to me and their statuses.
- As a tailor, I want to view material orders that have been delivered or are awaiting delivery.
- As a tailor, I want to accept or reject incoming orders.
- As a tailor, I want to propose a price and delivery deadline for an order.
- As a tailor, I want to update my availability status to open, closed, or busy.
- As a tailor, I want to update order statuses throughout the tailoring process.
- As a tailor, I want to view a summary of my assigned orders.
- As a tailor, I want to add materials available in my inventory.
- As a tailor, I want to mark materials as available or unavailable.
- As a tailor, I want to mark a material order as delivered.

### Provider

- As a provider, I want to sign in and sign out securely.
- As a provider, I want to add materials to my inventory.
- As a provider, I want to view material orders sent to me.
- As a provider, I want to accept or reject incoming material orders.
- As a provider, I want to update an order's status from pending to accepted.
- As a provider, I want to update an order's status from accepted to on the way.
- As a provider, I want to update the information of materials in my inventory.
- As a provider, I want to mark materials as deleted when they are no longer offered.
- As a provider, I want to mark specific materials as unavailable.

---

## Entity Relationship Diagram

The following ERD illustrates the main entities and their relationships within the Thobic platform.

![Thobic Entity Relationship Diagram](./Image/erd.png)

---

## Wireframes

The following wireframes illustrate the planned user interfaces and workflows for clients, tailors, providers, and administrators.

![Thobic Wireframes](./Image/ThobicW.png)

---

## Frontend Architecture

The frontend provides the user interface through which clients, tailors, providers, and administrators interact with the platform.

### Components Hierarchy

![Thobic Components Hierarchy](./Image/c1.png)

### Frontend Component Structure

![Thobic Frontend Architecture](./Image/co2.png)

For implementation details, visit the [Thobic Frontend Repository](https://github.com/AhKhamis/Thobic-Frontend).

---

## Backend Architecture

The backend is responsible for server-side business logic, API endpoints, authentication, authorization, and database operations.

### Main Responsibilities

- User registration and authentication.
- Token-based authentication and access control.
- User and profile management.
- Client measurement management.
- Thawb order management.
- Tailoring shop and tailor management.
- Material inventory management.
- Material order management.
- Order status management.
- Database connectivity and persistence.
- Configuration and database migrations.

The backend is built with FastAPI and SQLAlchemy, with PostgreSQL used for data persistence.

---

## Project Structure

The following is a simplified overview of the backend's main files and directories.

```text
Thobic-Backend/
│
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

_Note: This is a simplified overview. The exact files and subdirectories may vary as the project evolves._

---

## Technologies Used

### Backend

- **Python** — Primary backend programming language.
- **FastAPI** — Building REST API endpoints.
- **Uvicorn** — Running the ASGI application server.
- **SQLAlchemy** — Database ORM and database operations.
- **Alembic** — Database schema migrations.
- **Pydantic** — Data validation and serialization.
- **PyJWT** — JSON Web Token handling.
- **Passlib and bcrypt** — Password hashing.
- **python-dotenv** — Environment variable management.
- **python-multipart** — Handling multipart form data.
- **Pipenv** — Python dependency and virtual environment management.

### Database

- **PostgreSQL** — Relational database.
- **psycopg2-binary** — PostgreSQL database driver.

### Frontend

- **React**
- **Vite**
- **React Router**
- **Axios**
- **JavaScript**
- **CSS**

For the complete frontend implementation, see the [frontend repository](https://github.com/AhKhamis/Thobic-Frontend).

### Development and Deployment

- **Git and GitHub** — Version control and collaboration.
- **Render** — Backend deployment.
- **Vercel** — Frontend deployment.
- **Swagger UI** — Interactive API documentation.

---

## Getting Started

Follow these steps to run the backend locally.

### Prerequisites

Make sure the following tools are installed:

- Python compatible with the project's Pipfile.
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

Create a `.env` file in the project root and configure the required variables.

See the [Environment Variables](#environment-variables) section below.

### 4. Apply Database Migrations

```bash
pipenv run alembic upgrade head
```

Ensure your database connection is configured correctly before running migrations.

### 5. Start the Development Server

```bash
pipenv run uvicorn main:app --reload
```

The local API should now be available at:

- **API Base URL:** `http://127.0.0.1:8000`
- **Swagger UI:** `http://127.0.0.1:8000/docs`
- **ReDoc:** `http://127.0.0.1:8000/redoc`

---

## Environment Variables

The backend uses environment variables to configure its database connection, authentication, and allowed frontend origins.

Configure the variables required by your local setup in a `.env` file.

| Variable       | Purpose                                                               |
| -------------- | --------------------------------------------------------------------- |
| `DATABASE_URL` | PostgreSQL database connection string.                                |
| `JWT_SECRET`   | Secret used for signing or validating authentication tokens.          |
| `CORS_ORIGINS` | Comma-separated list of frontend origins permitted to access the API. |

Example format:

```env
DATABASE_URL=your_postgresql_connection_string
JWT_SECRET=your_secret_key
CORS_ORIGINS=http://localhost:5173,https://thobic.vercel.app
```

**Security note:** Never commit real database credentials, JWT secrets, or other sensitive environment values to GitHub. Keep `.env` excluded from version control.

---

## API Documentation

Thobic's backend provides interactive API documentation through FastAPI.

- **Production API Documentation:** [Open Swagger UI](https://thobic-backend.onrender.com/docs)
- **Production ReDoc:** [Open ReDoc](https://thobic-backend.onrender.com/redoc)

Swagger UI allows developers to inspect available endpoints, review request and response schemas, and test supported API operations.

---

## User Roles

Thobic is designed around four primary user roles.

| Role         | Description                                                                       |
| ------------ | --------------------------------------------------------------------------------- |
| **Client**   | Creates Thawb orders, selects materials, manages measurements, and tracks orders. |
| **Tailor**   | Manages tailoring orders, inventory, pricing, deadlines, and order statuses.      |
| **Provider** | Manages material inventory and handles material orders from tailors.              |
| **Admin**    | Creates and manages tailor and provider accounts.                                 |

Access to specific operations depends on the permissions and functionality implemented in the backend.

---

## Future Development

Potential future enhancements include:

- Online payment integration.
- Notifications for order and delivery updates.
- Real-time order tracking.
- Advanced material search and filtering.
- Customer reviews and ratings.
- Delivery management.
- Analytics and reporting dashboards.
- Appointment booking and management.
- Mobile application support.

These items represent potential enhancements and should not be considered implemented features unless they are available in the current application.

---

## Team

Thobic is a software engineering project focused on simplifying the traditional Thawb ordering and tailoring process through a centralized digital platform.

The project brings together frontend development, backend engineering, database design, and deployment to support a more convenient digital experience for clients, tailors, and material providers.

---

**Project Links**

- [Live Website](https://thobic.vercel.app)
- [Frontend Repository](https://github.com/AhKhamis/Thobic-Frontend)
- [Backend Repository](https://github.com/AhKhamis/Thobic-Backend)
- [API Documentation](https://thobic-backend.onrender.com/docs)
