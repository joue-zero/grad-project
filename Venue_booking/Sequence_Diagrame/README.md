# Venue Booking - Sequence Diagram Documentation

## Overview

This folder contains the **Sequence Diagram** for the Venue Booking process in our Event Planning Platform. The sequence diagram illustrates the interactions between different system components and actors during the venue booking workflow.

## 📋 Contents

- `Editor _ Mermaid Chart-2025-06-21-164547.mmd` - Mermaid source code for the sequence diagram
- `Venue_booking.svg` - Vector graphics version of the diagram
- `Venue_Booking.png` - PNG image version of the diagram

## 🎯 Purpose

The sequence diagram demonstrates how the **cart-based, event-first booking system** works, showing the communication flow between:

- **Customer** - The end user booking venues and services
- **Frontend UI** - The web interface
- **Backend API** - Server-side business logic
- **Database** - Data persistence layer
- **Cart Service** - Shopping cart management
- **Payment Gateway** - Payment processing
- **Venue Owner** - Service provider receiving bookings
- **Notification Service** - Communication system

## 🔄 Process Flow

### 1. **Venue Discovery Phase**
- Customer searches for venues with filters (location, date, capacity, price)
- System queries database for available venues
- Results are displayed to the customer

### 2. **Venue Selection Phase**
- Customer selects a specific venue
- System fetches detailed venue information
- Real-time availability check for the desired date
- Available time slots are presented

### 3. **Event Management Phase**
- **Key Innovation**: Before adding to cart, system checks for customer events
- Customer can either:
  - **Select existing event** - Link venue to an existing event
  - **Create new event** - Create a new event with the selected venue
- This ensures all bookings are organized by events

### 4. **Cart Addition Phase**
- Venue is added to cart with associated event ID
- Cart service stores the item in the database
- Customer receives confirmation that item was added
- **No immediate payment** - customer can continue shopping

### 5. **Shopping Continuation**
- Customer can browse and add services (catering, DJ, photography, etc.)
- All items are added to the same cart for the event
- **One-stop shopping experience**

### 6. **Checkout Phase**
- Customer reviews all cart items (venues + services)
- System creates pending bookings for all cart items
- **Single payment transaction** for the entire cart
- Payment is processed through the payment gateway

### 7. **Completion Phase**
#### Payment Successful:
- All bookings are confirmed in the database
- Customer cart is cleared
- Booking confirmations are sent to:
  - Customer (email confirmation)
  - All vendors/venue owners (booking notifications)
- Success confirmation is displayed

#### Payment Failed:
- All bookings are marked as failed
- Cart is preserved for customer to retry
- Error message is displayed with retry option

## 🚀 Key Features Highlighted

### **Cart-Based System**
- **Multiple items**: Add venues and services before payment
- **Single transaction**: Pay once for everything
- **Cart persistence**: Items remain if payment fails
- **Bulk processing**: All bookings confirmed together

### **Event-First Approach**
- **Event organization**: All bookings are tied to specific events
- **Flexible association**: Link to existing events or create new ones
- **Better management**: Customers can organize multiple events

### **Real-Time Capabilities**
- **Availability checking**: Instant venue availability verification
- **Dynamic pricing**: Real-time pricing information
- **Live updates**: Cart updates and notifications

### **Robust Error Handling**
- **Payment failures**: Graceful handling with retry options
- **Validation**: Form validation and error feedback
- **Cart preservation**: No data loss on payment failures

## 🔄 Alternative Flows

The diagram includes several alternative flows using `alt` blocks:

1. **Event Selection**:
   - Select existing event OR create new event
   - Both paths merge back to cart addition

2. **Payment Processing**:
   - Success path: Complete all bookings and send notifications
   - Failure path: Preserve cart and allow retry

## 🎨 Diagram Notation

- **Solid arrows (→)**: Synchronous calls/requests
- **Dashed arrows (--→)**: Response/return messages
- **Alt blocks**: Alternative/conditional flows
- **Notes**: Additional context and explanations
- **Participants**: Different system components and actors

## 🔄 Improvements Over Traditional Systems

| **Traditional Booking** | **Our Cart-Based System** |
|------------------------|---------------------------|
| Pay per item | Pay once for all items |
| Immediate payment required | Flexible cart management |
| Fragmented bookings | Event-organized bookings |
| Multiple transactions | Single bulk transaction |
| Limited error recovery | Robust retry mechanisms |

## 📝 Technical Details

### **API Endpoints Shown**
- `GET /venues` - Search venues with filters
- `GET /venue/{id}/details` - Fetch venue details
- `GET /venue/{id}/availability` - Check availability
- `GET /customer/{id}/events` - Get customer events
- `POST /events/{eventId}/add-venue` - Link venue to event
- `POST /events/create-with-venue` - Create event with venue
- `POST /cart/add-venue` - Add venue to cart
- `GET /cart/{customerId}` - Retrieve cart contents
- `POST /checkout/process-cart` - Process cart checkout
- `POST /cart/clear` - Clear customer cart

### **Database Interactions**
- Venue queries and availability checks
- Event creation and linking
- Cart item storage and retrieval
- Booking status management
- Transaction processing

### **External Integrations**
- **Payment Gateway**: Secure payment processing
- **Notification Service**: Email and SMS communications

## 🎯 Use Cases Covered

1. **First-time user**: No existing events - creates first event
2. **Returning user**: Has existing events - can choose or create new
3. **Multiple services**: Add various services to same event
4. **Payment issues**: Handles failures gracefully with retry options
5. **Bulk booking**: Confirms multiple items in single transaction

## 📈 Benefits for Stakeholders

### **For Customers**:
- Streamlined booking process
- Single payment for everything
- Better event organization
- Error recovery options

### **For Vendors**:
- Bulk booking notifications
- Organized event information
- Reduced payment processing overhead

### **For System**:
- Reduced transaction costs
- Better data organization
- Improved user experience
- Scalable architecture

---

*This sequence diagram represents the core booking functionality of our Event Planning Platform, demonstrating a modern, user-friendly approach to event service booking with robust error handling and efficient payment processing.* 