# Data Flow Diagram (DFD) - Level 1

## Entities:

1. **User (Customer, Admin, Salon Owner)**
2. **System (Saloonat)**

## Processes:

1. **User Authentication and Authorization**
2. **Salon Management**
3. **Service Management**
4. **Appointment Booking**
5. **Payment Processing**
6. **Notification System**
7. **Review Management**

## Data Stores:

1. **D1: User Data**
2. **D2: Salon Data**
3. **D3: Service Data**
4. **D4: Appointment Data**
5. **D5: Transaction Data**
6. **D6: Notification Data**
7. **D7: Review Data**

---

## Diagram Structure

### 1. **User Authentication and Authorization**

- **User** → [Authenticate/Authorize] → **System**
- **System** ↔ **D1: User Data**

### 2. **Salon Management**

- **Admin/Salon Owner** → [Manage Salon] → **System**
- **System** ↔ **D2: Salon Data**

### 3. **Service Management**

- **Salon Owner** → [Manage Services] → **System**
- **System** ↔ **D3: Service Data**

### 4. **Appointment Booking**

- **Customer** → [Book Appointment] → **System**
- **System** ↔ **D4: Appointment Data**

### 5. **Payment Processing**

- **Customer** → [Make Payment] → **System**
- **System** ↔ **D5: Transaction Data**

### 6. **Notification System**

- **System** → [Send Notification] → **User (Customer, Salon Owner)**
- **System** ↔ **D6: Notification Data**

### 7. **Review Management**

- **Customer** → [Submit Review] → **System**
- **System** ↔ **D7: Review Data**
- **System** → [Display Reviews] → **Customer/Admin**

---

## Explanation of Main Flows

1. **User Authentication and Authorization**

   - Customers, salon owners, and admins authenticate to gain access to respective functionalities.
   - User data is stored and retrieved from **D1: User Data**.

2. **Salon Management**

   - Admins and salon owners manage salon details (create, update, delete).
   - Salon data is stored in **D2: Salon Data**.

3. **Service Management**

   - Salon owners create and manage services offered by their salons.
   - Service information is saved in **D3: Service Data**.

4. **Appointment Booking**

   - Customers search for salons and book services by selecting a date and time.
   - Appointment information is saved in **D4: Appointment Data**.

5. **Payment Processing**

   - Customers make payments for booked appointments.
   - Transaction records are stored in **D5: Transaction Data**.

6. **Notification System**

   - The system sends notifications for booking confirmations, reminders, and updates.
   - Notifications are stored in **D6: Notification Data** and delivered to users as needed.

7. **Review Management**
   - Customers submit reviews for salons and services.
   - Review data is stored in **D7: Review Data** and displayed to other users.

---

This high-level DFD represents the overall data flow and main processes for the **Saloonat** reservation system, including interactions with data stores and key operations.
