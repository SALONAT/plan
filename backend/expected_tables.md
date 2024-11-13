# Database Tables and Relationships

## 1. Users

- **Columns**: `id`, `name`, `email`, `password`, `role` (admin, salon owner, customer), `created_at`, `updated_at`
- **Relationships**:
  - One-to-Many with **Salons** (one user can own multiple salons)
  - One-to-Many with **Appointments** (one customer can book multiple appointments)
  - One-to-Many with **Reviews** (one user can leave multiple reviews)
  - One-to-Many with **Notifications** (each user receives multiple notifications)

## 2. Salons

- **Columns**: `id`, `user_id` (foreign key to Users), `name`, `location`, `contact`, `description`, `hours`, `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Users** (each salon has an owner)
  - One-to-Many with **Services** (one salon can offer multiple services)
  - One-to-Many with **Appointments** (appointments booked at the salon)
  - One-to-Many with **Reviews** (customers leave reviews for salons)

## 3. Services

- **Columns**: `id`, `salon_id` (foreign key to Salons), `name`, `description`, `duration`, `price`, `category`, `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Salons** (each service belongs to a salon)
  - One-to-Many with **Appointments** (each appointment is for a specific service)

## 4. Appointments

- **Columns**: `id`, `user_id` (foreign key to Users), `salon_id` (foreign key to Salons), `service_id` (foreign key to Services), `date`, `time`, `status` (pending, confirmed, canceled), `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Users** (each appointment is booked by a customer)
  - Many-to-One with **Salons** (each appointment is for a specific salon)
  - Many-to-One with **Services** (each appointment is for a specific service)

## 5. Transactions

- **Columns**: `id`, `appointment_id` (foreign key to Appointments), `amount`, `status` (completed, pending, refunded), `transaction_date`, `created_at`, `updated_at`
- **Relationships**:
  - One-to-One with **Appointments** (each appointment may have one associated transaction)

## 6. Notifications

- **Columns**: `id`, `user_id` (foreign key to Users), `content`, `type` (e.g., appointment confirmation, reminder), `status` (read, unread), `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Users** (each notification is for a specific user)

## 7. Reviews

- **Columns**: `id`, `user_id` (foreign key to Users), `salon_id` (foreign key to Salons), `rating`, `comment`, `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Users** (each review is left by a customer)
  - Many-to-One with **Salons** (each review is for a specific salon)

---

# Relationships Summary

- **Users**

  - Has Many → **Salons**
  - Has Many → **Appointments**
  - Has Many → **Reviews**
  - Has Many → **Notifications**

- **Salons**

  - Belongs To → **Users**
  - Has Many → **Services**
  - Has Many → **Appointments**
  - Has Many → **Reviews**

- **Services**

  - Belongs To → **Salons**
  - Has Many → **Appointments**

- **Appointments**

  - Belongs To → **Users**
  - Belongs To → **Salons**
  - Belongs To → **Services**
  - Has One → **Transactions**

- **Transactions**

  - Belongs To → **Appointments**

- **Notifications**

  - Belongs To → **Users**

- **Reviews**
  - Belongs To → **Users**
  - Belongs To → **Salons**
