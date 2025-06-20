# 🚀 Project Overview
This is a backend service that powers an Airbnb Clone Platform, providing a scalable, robust system for managing users, property listings, bookings, payments, and reviews. It is designed to ensure secure user management, streamline property and booking operations, handle payment processing, and support efficient data management and optimization.

## 🏆 Project Goals
- User Management: Secure user registration and authentication
- Property Management: Property listing management
- Booking System: Booking and reservation system
- Payment Processing: Payment processing
- Review System: User reviews and ratings
- Data Optimization: Optimized data storage and retrieval

## ⚙️ Technology Stack
- Django
- Django Restframework
- MySQL, PostgreSQL
- GraphQL
- Celery
- Redis
- Docker
- CI/CD Pipelines

## 👥 Team Roles
### Each role plays a crucial part in delivering a secure, scalable, and user-friendly Airbnb Clone platform. Below is a breakdown of the key team roles and their core responsibilities within the project:

## 🧠 Backend Developer

### Responsiblities
-  Responsible for implementing API endpoints, database schemas, and business logic.
-  Collaborate with the frontend team towards intergrating api
-  devise an app architecture or design and implement the necessary integrations.

## 📁 Database Administrator

### Responsiblities
-  Manages database design, indexing, and optimizations.
- Collaborates with developers and system architects to design the MySQL database schema.
-  Enforces security policies for protecting sensitive data.
-  Manages the entire database operations, backup, and cleanup.

## ⚙️ DevOps Engineer

### Responsiblities
-  Handles deployment, monitoring, and scaling of the backend services.
- Facilitates cooperation between development and operations teams
-  Builds and maintains CI/CD pipelines to automate code integration, testing, and deployment for faster and more reliable software delivery.
-  Monitors system performance and reliability using observability tools like Prometheus, Grafana, or Datadog to detect and resolve issues proactively.

##  🧪 QA Engineer

### Responsiblities
-  Makes sure an application performs according to requirements
-  Ensures the backend functionalities are thoroughly tested and meet quality standards.
-  Identifies functional and non-functional defects to ensure the application behaves as expected and meets performance, usability, and security standards.
-  Collaborates with developers and product teams to clarify requirements and report bugs or inconsistencies.


##  👨 Product owner (PO)

### Responsiblities
-  Defines and owns the product vision, ensuring it aligns with business goals and delivers value to customers.
-  Manages the product backlog, prioritizing features, enhancements, and bug fixes based on business value and customer needs.
-  Ensures the final product meets customer and stakeholder requirements by collaborating closely with development, design, and QA teams.

##  👨 Product Manager (PM)

### Responsiblities
-  Plans, organizes, and monitors project timelines, resources, and deliverables throughout the development lifecycle.
-  Manages and motivates the software development team, fostering collaboration, resolving conflicts, and maintaining productivity.
-  Maintains project documentation, including schedules, status reports, and post-project reviews.

## ⚙️ Technology Stack

This project leverages a modern backend technology stack to ensure performance, scalability, and ease of development. Below is a breakdown of the core technologies used and their roles in the project.

### 🐍 Django

A high-level web framework built with Python, designed to simplify the development of secure, scalable, and maintainable web applications. 
**Purpose**: Manages core backend functionality, including URL routing, database interactions, business logic, and built-in admin features.

### 🧰 Django REST Framework (DRF)

A robust and flexible library built on Django that simplifies the building of RESTful APIs.
**Purpose**: Powers the RESTful API endpoints that handle core functionalities such as user accounts, property listings, bookings, payments, and reviews.

### 🐘 PostgreSQL

A reliable and feature-rich open-source relational database system designed for scalability and data integrity.
**Purpose**: Manages structured data including user accounts, property listings, bookings, and payment information.

### 🔍 GraphQL

An API query language that enables clients to retrieve precisely the data they require, reducing over-fetching and improving efficiency.
**Purpose**: Provides flexible and efficient data retrieval by allowing clients to request exactly the data they need, minimizing over-fetching and under-fetching.

### 📦 Celery

A distributed task queue that handles asynchronous and scheduled tasks in the background.
**Purpose**: Handles background tasks like sending email notifications and processing payments.

### ⚡ Redis

An in-memory data structure store used for caching and message brokering, enabling fast data access and efficient communication between services.
**Purpose**: Stores session data, accelerates database performance through caching, and serves as a message broker for background task processing with Celery.

### 🐳 Docker
A containerization platform that enables developers to package applications and their dependencies into isolated containers, ensuring consistent environments across development, testing, and production.  
**Purpose**: Provides consistent development and deployment environments for the backend stack.

### 🔁 Docker Compose

Tool for defining and running multi-container Docker applications using a simple YAML configuration.
**Purpose**: Orchestrates multiple services like Django, PostgreSQL, MySQL, and Redis with a single command.

### 🔬 Pytest

A lightweight and powerful testing framework for writing simple and scalable tests in Python applications. 
**Purpose**: Enables thorough unit and integration testing to ensure system reliability.

### 📬 Postman

Tool for testing, documenting, and monitoring APIs in development.
**Purpose**: To test and validate RESTful API endpoints throughout development.


### 🔧 CI/CD Pipelines

Automated workflows that streamline the process of building, testing, and deploying code with speed and reliability. 
**Purpose**: Ensures code changes are validated and deployed efficiently and reliably.

##  🗂️ Database Design
The database schema is thoughtfully designed to handle the main features of the Airbnb Clone application — such as user accounts, property listings, bookings, payments, and reviews. It outlines the core entities, their key attributes, and the relationships that connect them.
### 👤 Users
### Represents both regular user and hosts

#### Key Fields
- `id` - Identifies an entry of a user or guest
- `first name` - First name of user
- `last name` - Last name or surname of the user
- `email` - email address of the user must be unique
- `password` - this is the hashed password for user
- `password`: Hashed password for authentication.
- `is_hosts`: Boolean indicating if the user can list properties.
**Relationships**:
- A **user** can create multiple **properties**.
- A **user** can place multiple **bookings**.
- A **user** can leave multiple **reviews**.

### 👤 Properties
### Represents the property listings provided by the property_vendors

#### Key Fields
- `id` - Identifies a property listing
- `property name` - Property listing name
- `Size` -This is the size or the property possibly in (acres)
- `description` - Short description of the property
- `location` - Address or location of the property (city, country)
- `password`- Hashed password for authentication.
- `is_hosts` - Boolean indicating if the user can list properties
- `owner_id` - This is a foreign key to users table

**Relationships**:
- A **property** is owned by one **user** (host or vendor).
- A **property** can have multiple **bookings**.
- A **property** can have multiple **reviews**.

### 📅 Bookings
### Represents reservations made by users for properties

#### Key Fields
- `id` - Unique identifier for each booking
- `user_id` - Foreign key referencing the user who made the booking
- `property_id` - Foreign key referencing the booked property
- `start_date` - Date when the booking starts
- `end_date` - Date when the booking ends
- `status` - Status of the booking (e.g., pending, confirmed, cancelled)
- `total_payment` - Total amount paid for the booking
- `created_at` - Timestamp when the booking was created
- `updated_at` - Timestamp when the booking was last updated

**Relationships**:
- A **booking** is made by one **user**
- A **booking** is for one **property**
- A **booking** can have one **payment** record

### 💳 Payments
### Represents payment transactions for bookings

#### Key Fields
- `id` - Unique identifier for each payment
- `booking_id` - Foreign key referencing the associated booking
- `user_id` - Foreign key referencing the user who made the payment
- `amount` - Amount paid in the transaction
- `payment_method` - Method used for payment (e.g., credit card, PayPal)
- `payment_status` - Status of the payment (e.g., pending, completed, failed)
- `transaction_id` - Unique identifier from the payment gateway
- `paid_at` - Timestamp when the payment was completed
- `created_at` - Timestamp when the payment record was created
- `updated_at` - Timestamp when the payment record was last updated

**Relationships**:
- A **payment** is linked to one **booking**
- A **payment** is made

### 📝 Reviews
### Represents user feedback and ratings for properties

#### Key Fields
- `id` - Unique identifier for each review
- `user_id` - Foreign key referencing the user who wrote the review
- `property_id` - Foreign key referencing the reviewed property
- `booking_id` - Foreign key referencing the related booking (optional, if reviews are tied to bookings)
- `rating` - Numeric rating given to the property (e.g., 1-5)
- `comment` - Textual feedback provided by the user
- `created_at` - Timestamp when the review was created
- `updated_at` - Timestamp when the review was last updated

**Relationships**:
- A **review** belongs to one **user**
- A **review** is for one **property**


**Legend:**
- `Users` ──▶ `Properties`: A user (host) owns many properties.
- `Users` ──▶ `Bookings`: A user (guest) can make many bookings.
- `Users` ──▶ `Reviews`: A user can leave many reviews.
- `Properties` ──▶ `Bookings`: A property can have many bookings.
- `Properties` ──▶ `Reviews`: A property can have many reviews.
- `Bookings` ──▶ `Payments`: Each booking can have one payment.
