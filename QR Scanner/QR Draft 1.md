# 📱 QR-Based Restaurant Ordering System

**Production-Ready Requirement Specification**

## 1. Overview

A QR-based digital ordering system for restaurants that allows customers to browse the menu, place orders, and request bills seamlessly. Orders flow through **Waiter → Kitchen → Delivery**, with full control and visibility for **Admin**.

The system is designed to be:

* Fast & intuitive for customers
* Operationally efficient for staff
* Configurable and scalable for admins
* AI-assisted for better customer experience

---

## 2. User Roles & Permissions

### 2.1 Roles

1. **Customer**
2. **Waiter**
3. **Kitchen Staff**
4. **Admin**

Each role has **strict permission boundaries** to avoid misuse and confusion.

---

## 3. Customer Flow (QR → Order → Bill)

### 3.1 QR Scan & Menu Access

* Customer scans a **table-specific QR code**
* QR contains:

  * Table Number
  * Restaurant ID
  * Session ID (auto-generated)

**Customer can view without login:**

* Menu items
* Prices
* Cuisine categories
* Item availability
* Ratings (only if enabled by Admin)

---

### 3.2 Item Browsing & Cart

* Items displayed with:

  * Name
  * Image
  * Price
  * Veg / Non-Veg indicator
  * Rating (optional)
* Customer can:

  * Add items to cart
  * Increase/decrease quantity
  * View live cart total

---

### 3.3 Login via Mobile OTP (Only When Ordering)

* OTP login is required **only when user clicks “Place Order”**
* After OTP verification:

  * User is redirected back to the same page
  * Cart state is preserved
* Mobile number is linked to the session

---

### 3.4 Order Placement

* Customer places order
* Order is:

  * Linked to the same session
  * Visible only to **Waiter & Admin**
* Customer can place **multiple orders** within the same session

---

### 3.5 Bill Generation

* “Request Bill” button available
* Confirmation modal:

  * Shows all ordered items
  * Shows total payable amount
* Once confirmed:

  * Bill is generated
  * Prices become visible to Admin & Waiter

---

### 3.6 Customer Visibility Rules

* Customer can always see:

  * Item-wise price
  * Total order amount
  * Previous orders in the same session
* Session data auto-expires after **20 minutes** (configurable by Admin)

---

## 4. Waiter Dashboard

### 4.1 Order Visibility

* Waiter can see orders:

  * Only after customer places them
  * Grouped by **Table Number**
* Waiter sees:

  * Item name
  * Quantity
  * Add-ons / instructions
* Waiter **cannot see price** until bill is generated

---

### 4.2 Order Actions

* Approve Order (within 2 minutes)
* Cancel Order (within 2 minutes)
* Add item-level comments:

  * “Less spicy”
  * “Extra cheese”
  * “No onion”

---

### 4.3 Table Management

* Search orders by:

  * Table number
  * Order status
* View:

  * Active orders
  * Bill requested tables
  * Pending delivery orders

---

## 5. Kitchen Dashboard

### 5.1 Order Visibility

* Orders appear **only after approval** by Waiter or Admin
* Kitchen staff sees:

  * Table number
  * Item name
  * Quantity
  * Add-ons / special requests

---

### 5.2 Order Status Management

Each item moves through:

1. Placed
2. Preparing
3. Prepared
4. Delivered

* Status updates are real-time
* Waiter & Admin see delivery-ready items in a separate section

---

## 6. Admin Panel (Full Control)

### 6.1 User & Staff Management

* Add / Edit / Delete:

  * Waiters
  * Kitchen staff
* View staff activity & history

---

### 6.2 Order & Revenue Management

* View:

  * Current orders
  * Past order history
  * Delivered tables
* Access:

  * Full bill amounts
  * Revenue summaries
  * Payment-related data

---

### 6.3 Feature Toggles (Critical)

Admin can enable/disable:

* Item ratings visibility
* AI assistant
* OTP login enforcement
* Session timeout duration
* Bill visibility rules
* Kitchen status tracking

---

## 7. AI Feature (New – User Friendly & Powerful)

### 7.1 AI Menu Assistant (Customer-Facing)

**Purpose:** Reduce confusion & improve ordering confidence.

#### How it works:

* On each menu item → “Ask AI” button
* AI can answer:

  * “Is this very spicy?”
  * “Is this good for kids?”
  * “What goes well with this?”
  * “Is this similar to butter chicken?”

#### AI Input Sources:

* Item description
* Ingredients
* Cuisine type
* Ratings & popularity (if enabled)

---

### 7.2 AI Restrictions

* No medical or allergy guarantees
* AI shows disclaimer:

  > “For allergies, please confirm with staff”

---

## 8. System Rules & Safeguards

### 8.1 Time-Based Rules

* Order cancel/approve window: **2 minutes**
* Session expiry: **20 minutes** (configurable)
* OTP retry limit & cooldown

---

### 8.2 Security & Reliability

* Role-based access control (RBAC)
* Session-based order isolation
* Immutable order logs for Admin
* Audit trail for cancellations & approvals

---

## 9. UX & Performance Suggestions (Recommended)

### UX Improvements

* Sticky cart button for customers
* Order status progress bar
* Real-time order updates (WebSockets)
* Offline QR fallback message

### Performance & Scalability

* Microservice-based order system
* Redis for session & cart caching
* Queue-based kitchen updates
* Fail-safe OTP provider fallback

---

## 10. Future Enhancements (Optional)

* Digital payment integration
* Loyalty points
* AI-based order recommendations
* Multi-restaurant support
* Language localization

