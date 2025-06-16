# airbnb-clone-project
## Overview
This is the backend for my Airbnb Clone project. It’s built to handle everything from user interactions and property listings to bookings and payments. The goal is to replicate the core functionality of Airbnb while keeping the system scalable and reliable for both users and hosts.

## 🏆 Project Goals

 **User Management**  
  Implement a secure system for user registration, authentication, and profile management.

 **Property Management**  
  Develop features for property listing creation, updates, and retrieval.

 **Booking System**  
  Create a booking mechanism for users to reserve properties and manage booking details.

 **Payment Processing**  
  Integrate a payment system to handle transactions and record payment details.

 **Review System**  
  Allow users to leave reviews and ratings for properties.

 **Data Optimization**  
  Ensure efficient data retrieval and storage through database optimizations.

## ⚙️ Technology Stack

**Django**: A high-level Python web framework used for building the RESTful API.

**PostgreSQL**: A powerful relational database used for data storage.

**GraphQL**: Allows for flexible and efficient querying of data.

**Celery**: For handling asynchronous tasks such as sending notifications or processing payments.

**Redis**: Used for caching and session management.

**Docker**: Containerization tool for consistent development and deployment environments.

**CI/CD Pipelines**: Automated pipelines for testing and deploying code changes.

## Team Roles

**Backend Developer**: Responsible for implementing API endpoints, database schemas, and business logic.

**Database Administrator**: Manages database design, indexing, and optimizations.

**DevOps Engineer**: Handles deployment, monitoring, and scaling of the backend services.

**QA Engineer**: Ensures the backend functionalities are thoroughly tested and meet quality standards.

## Database Design

## 1. 👤 User

**Represents people who use the platform—guests or hosts.**

### 🔑 Important Fields:
- `id`: Unique identifier (UUID or integer)
- `name`: Full name
- `email`: Unique email address
- `password_hash`: Hashed password
- `is_host`: Boolean to indicate if the user is a host

### 🔗 Relationships:
- A user can **host multiple properties**
- A user can **book multiple properties**
- A user can **leave multiple reviews**
- A user can **make multiple payments**

---

## 2. 🏠 Property

**Represents a listing on the platform (house, apartment, etc.).**

### 🔑 Important Fields:
- `id`: Unique identifier
- `title`: Short headline for the property
- `description`: Detailed description
- `location`: City, address, etc.
- `price_per_night`: Decimal

### 🔗 Relationships:
- A property **belongs to a host** (User)
- A property **can have many bookings**
- A property **can have many reviews**
- A property **can have many images** (optional `PropertyImage` entity)

---

## 3. 📅 Booking

**Represents a reservation of a property by a guest.**

### 🔑 Important Fields:
- `id`: Unique identifier
- `check_in`: Date
- `check_out`: Date
- `total_price`: Calculated from price * nights

### 🔗 Relationships:
- A booking **belongs to a guest** (User)
- A booking **is for one property**
- A booking **may have one payment**

---

## 4. 🌟 Review

**Users can leave reviews after staying at a property.**

### 🔑 Important Fields:
- `id`: Unique identifier
- `rating`: Integer (1 to 5)
- `comment`: Text
- `created_at`: DateTime

### 🔗 Relationships:
- A review **belongs to a user**
- A review **belongs to a property**

> ✅ Optional: Enforce that only guests who have booked can leave a review.

---

## 5. 💳 Payment

**Represents a completed payment for a booking.**

### 🔑 Important Fields:
- `id`: Unique identifier
- `amount`: Decimal
- `payment_method`: e.g., `'card'`, `'paypal'`
- `status`: e.g., `'completed'`, `'failed'`, `'pending'`
- `paid_at`: DateTime

### 🔗 Relationships:
- A payment **is linked to a booking**
- A payment **is made by a user**

---

## 6. 🖼️ PropertyImage *(Optional)*

**Handles multiple images for a single listing.**

### 🔑 Important Fields:
- `id`: Unique identifier
- `image_url`: Path to the image
- `caption`: Optional text

### 🔗 Relationships:
- Each image **belongs to a property**





