# airbnb-clone-project

## Description
The backend for the Airbnb Clone project is designed to provide a robust and scalable foundation for managing user interactions, property listings, bookings, and payments. This backend will support various functionalities required to mimic the core features of Airbnb, ensuring a smooth experience for users and hosts.
## Project Goals
- **User Management**: Implement a secure system for user registration, authentication, and profile management.
- **Property Management**: Develop features for property listing creation, updates, and retrieval.
- **Booking System**: Create a booking mechanism for users to reserve properties and manage booking details.
- **Payment Processing**: Integrate a payment system to handle transactions and record payment details.
- **Review System**: Allow users to leave reviews and ratings for properties.
- **Data Optimization**: Ensure efficient data retrieval and storage through database optimizations.
## Technology Stack
- **Django**: A high-level Python web framework used for building the RESTful API.
- **Django REST Framework**: Provides tools for creating and managing RESTful APIs.
- **PostgreSQL**: A powerful relational database used for data storage.
- **GraphQL**: Allows for flexible and efficient querying of data.
- **Celery**: For handling asynchronous tasks such as sending notifications or processing payments.
- **Redis**: Used for caching and session management.
- **Docker**: Containerization tool for consistent development and deployment environments.
- **CI/CD Pipelines**: Automated pipelines for testing and deploying code changes.

## Team Roles and Responsibilities
- **Software Architect**: Responsible for designing high-level software architecture, selecting tools and platforms, setting up code quality standards and performing code reviews.
-  **Backend developer**: Responsible for implementing API endpoints, database schemas, and business logic.
-  **Database Administrator**: Manages database design, indexing, and optimizations.
-  **Quality Assuarance Engineer**: Ensures the backend functionalities are thoroughly tested and meet quality standards
-  **Test Automation Engineer**: Writes and mainatains tests scripts for automated testing.
-  **Devops Engineer**: Handles deployment, monitoring, and scaling of the backend services.


## Database Design 
The Airbnb Clone backend is structured to support key functionalities like user management, property listings, bookings, payments, and reviews. 
Below is an overview of the core entities and their relationships.

###  Key Entities

### **1. Users**

Represents both guests and hosts in the system.

**Important Fields:**
- `id`: Unique identifier for the user.
- `username`: Unique name chosen by the user.
- `email`: Email address for login and communication.
- `password_hash`: Encrypted password.
- `is_host`: Boolean indicating if the user can list properties.

**Relationships:**
- A user can **create multiple properties**.
- A user can **make multiple bookings**.
- A user can **write multiple reviews**.
- A user can **make payments** for bookings.

### **2. Properties**

Represents listings created by hosts.

**Important Fields:**
- `id`: Unique identifier for the property.
- `user_id`: References the host (User).
- `title`: Title of the property listing.
- `description`: Detailed description of the property.
- `price_per_night`: Cost to book the property per night.

**Relationships:**
- A property is **owned by one user (host)**.
- A property can **have multiple bookings**.
- A property can **have multiple reviews**.
- A property can **have multiple images**.

### **3. Bookings**

Represents a reservation made by a guest for a property.

**Important Fields:**
- `id`: Unique identifier for the booking.
- `user_id`: References the guest (User).
- `property_id`: References the property being booked.
- `check_in` / `check_out`: Booking period.
- `total_price`: Calculated price for the stay.

**Relationships:**
- A booking is **made by one user**.
- A booking is **linked to one property**.
- A booking can **have one payment**.

### **4. Payments**

Tracks transactions made for bookings.

**Important Fields:**
- `id`: Unique identifier for the payment.
- `booking_id`: References the associated booking.
- `user_id`: References the payer (User).
- `amount`: Total amount paid.
- `payment_status`: Status like “Paid” or “Failed”.

**Relationships:**
- A payment is **associated with one booking**.
- A payment is **made by one user**.

### **5. Reviews**

Allows users to review properties after a stay.

**Important Fields:**
- `id`: Unique identifier for the review.
- `user_id`: References the reviewer (User).
- `property_id`: References the reviewed property.
- `rating`: Numerical rating (e.g., 1–5).
- `comment`: Text feedback.

**Relationships:**
- A review is **written by one user**.
- A review is **about one property**.

### Entity Relationship Summary

- A **user** can own **many properties**.
- A **property** can have **many bookings** and **many reviews**.
- A **user** can make **many bookings**, **payments**, and **reviews**.
- A **booking** belongs to **one user** and **one property**, and can have **one payment**.


## Feature Breakdown

The Airbnb Clone backend includes a range of features that mirror the essential functionalities of the original Airbnb platform. Each feature is designed to support a seamless, secure, and scalable experience for users, hosts, and administrators.


### **1. User Authentication**

- **Endpoints**: `/users/`, `/users/{user_id}/`
- Allows new users to register, authenticate securely, and manage their profiles. Supports role-based access (e.g., guests vs hosts).


### **2. Property Management**

- **Endpoints**: `/properties/`, `/properties/{property_id}/`
- Hosts can create, update, retrieve, and delete property listings. Each listing includes metadata such as pricing, images, and location.


### **3. Booking System**

- **Endpoints**: `/bookings/`, `/bookings/{booking_id}/`
- Enables users to book available properties, manage check-in and check-out dates, and track booking status.


### **4. Payment Processing**

- **Endpoints**: `/payments/`
- Integrates with third-party payment gateways to handle transactions securely. Records payment status and booking associations.


### **5. Review System**

- **Endpoints**: `/reviews/`, `/reviews/{review_id}/`
- Allows users to leave feedback and rate properties. Reviews help build trust and improve platform transparency.


## API Security


## CI/CD Pipeline





