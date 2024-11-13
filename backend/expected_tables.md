# Database Tables and Relationships

## 1. Admins

- **Columns**: `id`, `name`, `email`, `password`, `created_at`, `updated_at`
- **Relationships**:
  - One-to-Many with **Notifications** (each admin can receive notifications for system alerts)

## 2. Salon Owners

- **Columns**: `id`, `name`, `email`, `password`, `created_at`, `updated_at`
- **Relationships**:
  - One-to-Many with **Salons** (each salon owner can own multiple salons)
  - One-to-Many with **Notifications** (each salon owner receives notifications about their salons, bookings)

## 3. Customers

- **Columns**: `id`, `name`, `email`, `password`, `created_at`, `updated_at`
- **Relationships**:
  - One-to-Many with **Appointments** (each customer can book multiple appointments)
  - One-to-Many with **Reviews** (each customer can leave multiple reviews)
  - One-to-Many with **Notifications** (each customer receives notifications about their bookings)

---

## 4. Salons

- **Columns**: `id`, `owner_id` (foreign key to Salon Owners), `name`, `location`, `contact`, `description`, `hours`, `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Salon Owners** (each salon is owned by a salon owner)
  - One-to-Many with **Services** (each salon can offer multiple services)
  - One-to-Many with **Appointments** (appointments are booked for the salon)
  - One-to-Many with **Reviews** (customers leave reviews for salons)

## 5. Services

- **Columns**: `id`, `salon_id` (foreign key to Salons), `name`, `description`, `duration`, `price`, `category`, `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Salons** (each service is offered by a specific salon)
  - One-to-Many with **Appointments** (each appointment is for a specific service)

## 6. Appointments

- **Columns**: `id`, `customer_id` (foreign key to Customers), `salon_id` (foreign key to Salons), `service_id` (foreign key to Services), `date`, `time`, `status` (pending, confirmed, canceled), `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Customers** (each appointment is booked by a customer)
  - Many-to-One with **Salons** (each appointment is for a specific salon)
  - Many-to-One with **Services** (each appointment is for a specific service)
  - One-to-One with **Transactions** (each appointment can have one associated transaction)

## 7. Transactions

- **Columns**: `id`, `appointment_id` (foreign key to Appointments), `amount`, `status` (completed, pending, refunded), `transaction_date`, `created_at`, `updated_at`
- **Relationships**:
  - One-to-One with **Appointments** (each transaction is associated with one appointment)

## 8. Notifications

- **Columns**: `id`, `user_id` (foreign key to either Admins, Salon Owners, or Customers), `user_type` (to distinguish role type), `content`, `type` (e.g., booking confirmation, reminder), `status` (read, unread), `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Admins**, **Salon Owners**, or **Customers** (each notification is associated with a specific user)

## 9. Reviews

- **Columns**: `id`, `customer_id` (foreign key to Customers), `salon_id` (foreign key to Salons), `rating`, `comment`, `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Customers** (each review is left by a customer)
  - Many-to-One with **Salons** (each review is for a specific salon)

---

# Relationships Summary

- **Admins**

  - Has Many → **Notifications**

- **Salon Owners**

  - Has Many → **Salons**
  - Has Many → **Notifications**

- **Customers**

  - Has Many → **Appointments**
  - Has Many → **Reviews**
  - Has Many → **Notifications**

- **Salons**

  - Belongs To → **Salon Owners**
  - Has Many → **Services**
  - Has Many → **Appointments**
  - Has Many → **Reviews**

- **Services**

  - Belongs To → **Salons**
  - Has Many → **Appointments**

- **Appointments**

  - Belongs To → **Customers**
  - Belongs To → **Salons**
  - Belongs To → **Services**
  - Has One → **Transactions**

- **Transactions**

  - Belongs To → **Appointments**

- **Notifications**

  - Belongs To → **Admins**, **Salon Owners**, or **Customers**

- **Reviews**
  - Belongs To → **Customers**
  - Belongs To → **Salons**
