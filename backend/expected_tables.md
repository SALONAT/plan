# Enhanced Database Tables and Relationships for "Saloonat"

## 1. Admins

- **Columns**: `id`, `name`, `email`, `password`, `last_login`, `role`, `created_at`, `updated_at`
- **Relationships**:
  - One-to-Many with **Notifications** (to receive system alerts)

## 2. Salon Owners

- **Columns**: `id`, `name`, `email`, `password`, `created_at`, `updated_at`
- **Relationships**:
  - One-to-Many with **Salons** (ownership)
  - One-to-Many with **Notifications** (salon-specific notifications)

## 3. Customers

- **Columns**: `id`, `name`, `email`, `password`, `created_at`, `updated_at`
- **Relationships**:
  - One-to-Many with **Appointments** (booking multiple appointments)
  - One-to-Many with **Reviews** (writing reviews)
  - One-to-Many with **Notifications** (appointment and review notifications)

---

## 4. Salons

- **Columns**: `id`, `owner_id`, `name`, `street_address`, `city`, `state`, `postal_code`, `country`, `latitude`, `longitude`, `contact`, `description`, `rating`, `hours`, `status`, `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Salon Owners** (ownership)
  - One-to-Many with **Services** (offering services)
  - One-to-Many with **Appointments** (hosting appointments)
  - One-to-Many with **Reviews** (receiving customer feedback)

## 5. Services

- **Columns**: `id`, `salon_id`, `name`, `description`, `duration`, `price`, `category`, `status`, `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Salons** (offered by salons)
  - One-to-Many with **Appointments** (selected for appointments)

## 6. Availability

- **Columns**: `id`, `salon_id`, `day_of_week`, `start_time`, `end_time`, `is_recurring`, `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Salons** (each availability slot is linked to one salon)

## 7. Appointments

- **Columns**: `id`, `customer_id`, `salon_id`, `service_id`, `date`, `time`, `status`, `checked_in`, `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Customers** (booked by customers)
  - Many-to-One with **Salons** (held at salons)
  - Many-to-One with **Services** (service being provided)
  - One-to-One with **Transactions** (financial transactions)

## 8. Transactions

- **Columns**: `id`, `appointment_id`, `amount`, `payment_method`, `status`, `transaction_date`, `gateway_response`, `created_at`, `updated_at`
- **Relationships**:
  - One-to-One with **Appointments** (related to specific appointments)

## 9. Notifications

- **Columns**: `id`, `user_id`, `user_type`, `content`, `type`, `status`, `delivered_at`, `failed_at`, `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Admins**, **Salon Owners**, or **Customers** (targeted notifications)

## 10. Reviews

- **Columns**: `id`, `customer_id`, `salon_id`, `rating`, `comment`, `created_at`, `updated_at`
- **Relationships**:
  - Many-to-One with **Customers** (authored by customers)
  - Many-to-One with **Salons** (related to specific salons)

## 11. User Activity Logs (Optional)

- **Columns**: `id`, `user_id`, `activity_type`, `description`, `ip_address`, `session_id`, `created_at`
- **Relationships**:
  - Many-to-One with **Admins**, **Salon Owners**, or **Customers** (logs activity for security and audit purposes)

---

# Relationships Summary

- **Admins**:

  - Has Many → **Notifications**

- **Salon Owners**:

  - Has Many → **Salons**
  - Has Many → **Notifications**

- **Customers**:

  - Has Many → **Appointments**
  - Has Many → **Reviews**
  - Has Many → **Notifications**

- **Salons**:

  - Belongs To → **Salon Owners**
  - Has Many → **Services**
  - Has Many → **Appointments**
  - Has Many → **Reviews**
  - Has Many → **Availability** (managing all time slots for services)

- **Services**:

  - Belongs To → **Salons**
  - Has Many → **Appointments**

- **Appointments**:

  - Belongs To → **Customers**
  - Belongs To → **Salons**
  - Belongs To → **Services**
  - Has One → **Transactions**

- **Transactions**:

  - Belongs To → **Appointments**

- **Notifications**:

  - Belongs To → **Admins**, **Salon Owners**, or **Customers**

- **Reviews**:

  - Belongs To → **Customers**
  - Belongs To → **Salons**

- **User Activity Logs**:
  - Belongs To → **Admins**, **Salon Owners**, or **Customers**
