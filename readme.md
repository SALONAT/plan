# Saloonat Reservation System

## Backend (Laravel)

- **User Authentication and Authorization**
  - User Roles (Admin, Salon Owner, Customer)
  - Login, Registration, Password Reset
  - Role-Based Access Control
- **Salon Management**
  - CRUD Operations for Salons
  - Salon Details (Name, Location, Contact, Photos)
  - Category Management (e.g., Hair, Nails, Skincare)
- **Service Management**
  - CRUD Operations for Services
  - Service Details (Description, Duration, Price)
  - Link Services to Salons and Categories
- **Advanced Search system**
  - Search By location {nearesr location will server first}
  - Search by service
  - Apply filters for search
- **Appointment Booking System**
  - Available Time Slots (Based on Salon Hours)
  - Appointment Booking API for Customers
  - Booking Status (Pending, Confirmed, Canceled)
- **Payment Gateway Integration**
  - Secure Payment Endpoints
  - Transaction History and Refunds
  - Payment Gateway (e.g., Stripe, PayPal)
- **Notifications**
  - Email/SMS Notifications (Confirmation, Reminders)
  - Notifications Table for History
- **Admin Panel**
  - Dashboard (Bookings, Active Salons)
  - Manage Salons, Services, Users
  - Reports (Bookings, Revenue, Popular Services)
- **Rating and Review System**
  - Customer Ratings and Reviews
  - Review Moderation and Display of Average Ratings

## Frontend (React)

- **User Interface for Salon Listing**
  - Salon Details, Services, Ratings
  - Filters (Location, Service Type, Price Range)
- **User Dashboard**
  - Upcoming Appointments
  - Booking History
  - Profile Management
- **Appointment Booking Flow**
  - Calendar Interface for Time Slots
  - Backend Integration for Slot Availability
  - Payment Handling
- **Salon Owner Dashboard**
  - Manage Salon Details and Services
  - Available Slots Management
  - View Appointments, Confirm Bookings, Income Reports
- **Admin Panel (Frontend)**
  - Manage Salons, Services, Users, Payments
  - Statistics and Insights

## Mobile App (Flutter)

- **User Authentication**
  - Login and Registration
  - Account Management
- **Salon Search and Discovery**
  - Nearby Salons
  - Service Filters, Salon Details
- **Booking System**
  - Calendar Selection for Services
  - Booking Status Updates
  - Cancellations Handling
- **Notifications and Reminders**
  - Push Notifications
  - Appointment Confirmations, Reminders, Offers
- **User Profile and Booking History**
  - Profile Updates
  - Past Bookings
  - Appointment Cancellation/Rescheduling
- **Rating and Reviews**
  - Rate and Review Salons
- **Salon Management for Owners (Optional)**
  - Salon Listings Update
  - Availability Management
  - Appointment Schedules Overview
