# AirBnB Clone Project

## Project Overview

This project is a backend implementation of an AirBnB clone, providing a robust and scalable foundation for managing user interactions, property listings, bookings, and payments.

## Project Goals

- User Management: Implement secure user registration, authentication, and profile management
- Property Management: Develop features for property listing creation, updates, and retrieval
- Booking System: Create a booking mechanism for users to reserve properties
- Payment Processing: Integrate a payment system to handle transactions
- Review System: Allow users to leave reviews and ratings for properties
- Data Optimization: Ensure efficient data retrieval and storage

## Technology Stack

- **Django**: A high-level Python web framework that encourages rapid development and clean, pragmatic design. Used as the foundation for building our backend application, handling URL routing, view logic, and ORM functionality.

- **Django REST Framework**: A powerful and flexible toolkit for building Web APIs on top of Django. Provides serialization, authentication, and viewsets to create RESTful endpoints for our application.

- **PostgreSQL**: An advanced open-source relational database that provides robustness, performance, and advanced features. Stores all application data including user profiles, property listings, bookings, and reviews.

- **GraphQL**: A query language for APIs that enables clients to request exactly the data they need. Provides a more flexible alternative to REST for complex data fetching requirements.

- **Celery**: A distributed task queue system that handles asynchronous processing. Used for background tasks like sending email notifications, processing payments, and generating reports.

- **Redis**: An in-memory data structure store used as a database, cache, and message broker. Supports Celery as a message broker and provides caching to improve application performance.

- **Docker**: A platform for developing, shipping, and running applications in containers. Ensures consistent environments across development, testing, and production.

- **CI/CD Pipelines**: Automated workflows for continuous integration and deployment. Automates testing, building, and deploying the application to ensure code quality and streamline releases.

- **JWT Authentication**: JSON Web Tokens for secure authentication and authorization. Provides stateless authentication for API requests.

- **Nginx**: A high-performance web server that acts as a reverse proxy. Handles load balancing, SSL termination, and serves static files.

## Database Design

### Users
- **Fields**:
  - user_id (Primary Key)
  - email (Unique)
  - password (Hashed)
  - name
  - profile_picture
- **Relationships**:
  - One user can have multiple properties (as a host)
  - One user can have multiple bookings (as a guest)
  - One user can write multiple reviews

### Properties
- **Fields**:
  - property_id (Primary Key)
  - host_id (Foreign Key to Users)
  - title
  - description
  - price_per_night
  - location
- **Relationships**:
  - Each property belongs to one user (host)
  - One property can have multiple bookings
  - One property can have multiple reviews

### Bookings
- **Fields**:
  - booking_id (Primary Key)
  - property_id (Foreign Key to Properties)
  - guest_id (Foreign Key to Users)
  - check_in_date
  - check_out_date
  - total_price
- **Relationships**:
  - Each booking belongs to one property
  - Each booking belongs to one user (guest)
  - One booking can have one payment

### Reviews
- **Fields**:
  - review_id (Primary Key)
  - property_id (Foreign Key to Properties)
  - user_id (Foreign Key to Users)
  - rating (1-5 stars)
  - comment
  - date_posted
- **Relationships**:
  - Each review belongs to one property
  - Each review is written by one user
  - Each review is associated with one booking

### Payments
- **Fields**:
  - payment_id (Primary Key)
  - booking_id (Foreign Key to Bookings)
  - amount
  - payment_date
  - payment_status
- **Relationships**:
  - Each payment belongs to one booking
  - Each payment is made by one user (indirectly through booking)

### Amenities
- **Fields**:
  - amenity_id (Primary Key)
  - name
  - icon
  - category
- **Relationships**:
  - Many amenities can belong to many properties (Many-to-Many)

## Team Roles

- **Backend Developer**: Responsible for implementing API endpoints, database schemas, and business logic. They develop the core functionality of the application using Django and Django REST Framework.

- **Database Administrator**: Manages database design, schema creation, indexing, and optimizations. They ensure efficient data storage and retrieval through PostgreSQL and implement caching strategies with Redis.

- **DevOps Engineer**: Handles deployment, monitoring, and scaling of the backend services. They set up Docker containers, configure CI/CD pipelines, and ensure the system runs smoothly in production environments.

- **QA Engineer**: Ensures the backend functionalities are thoroughly tested and meet quality standards. They develop and execute test cases, perform integration testing, and identify bugs before deployment.

- **Project Manager**: Coordinates the team's efforts, manages timelines, and ensures project goals are met. They facilitate communication between team members and stakeholders.

- **UI/UX Designer**: Although primarily a backend project, they provide input on API design to ensure it meets frontend requirements and delivers a seamless user experience.

- **Security Specialist**: Reviews code and infrastructure for security vulnerabilities, implements authentication and authorization mechanisms, and ensures data protection compliance.