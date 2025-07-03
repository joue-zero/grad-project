# Event Planning Platform - Entity Relationship Diagram (ERD)

## Overview
This ERD represents the database design for a comprehensive event planning platform that connects customers, vendors, and administrators in a unified system for venue booking, service management, and event organization.

## Core Entities & Relationships

### **🔐 User Management**
- **User**: Central entity supporting three user types (Customer, Vendor, Admin)
- Supports role-based access control through `user_type` field
- Manages authentication and profile information

### **🎉 Event Management** 
- **Event**: Central organizing entity for customer activities
- **EventWebsite**: CMS functionality for custom event websites with RSVP
- **Invitation**: Guest management and automated invitation system
- **TodoItem**: Task management and planning tools
- **Budget**: Financial tracking (estimated vs actual expenses)

### **🏢 Venue & Service Management**
- **Venue**: Physical locations with capacity, pricing, and amenities
- **Service**: Additional services (catering, photography, DJ, etc.)
- **Package**: Bundled services with discount pricing
- **VenuePhoto/ServicePhoto**: Visual portfolio management
- **Availability**: Real-time calendar management for bookings

### **📋 Booking & Commerce**
- **Booking**: Unified booking entity for venues, services, and packages
- **Cart/CartItem**: Shopping cart functionality for multiple selections
- **Payment**: Secure payment processing and tracking
- **Transaction**: Gateway integration and financial records

### **⭐ Engagement & Quality**
- **Review**: Customer feedback and rating system
- **SiteVisit**: Free venue inspection bookings

## Key Design Decisions

### **🔄 Flexible Booking System**
- Single `Booking` entity handles venues, services, and packages
- Foreign keys allow null values for different booking types
- Supports both individual and bundled service bookings

### **🛒 Cart-Based Shopping**
- Enables customers to collect multiple items before checkout
- Links items to specific events for better organization
- Supports the activity diagram's cart workflow

### **📅 Availability Management**
- Unified availability system for both venues and services
- Supports time-slot management and real-time checking
- Enables holiday pricing through venue entity

### **💰 Financial Tracking**
- Complete payment flow from cart to confirmed booking
- Budget tracking per event with estimated vs actual costs
- Transaction records for audit and reconciliation

### **🌟 Event-Centric Design**
- All bookings tied to events for better organization
- Supports multiple events per customer
- Event websites and invitations linked to specific events

### **📊 Admin Management**
- Review moderation through `is_approved` field
- User account management through `is_active` field
- Content management for photos and descriptions

## Relationships Summary

### **One-to-Many Relationships**:
- User → Events (customers create multiple events)
- User → Venues (vendors own multiple venues)
- User → Services (vendors provide multiple services)
- Event → Bookings (events contain multiple bookings)
- Venue → Availability (venues have multiple time slots)

### **One-to-One Relationships**:
- User ↔ Cart (each customer has one active cart)
- Event ↔ EventWebsite (each event has one website)
- Booking ↔ Payment (each booking requires one payment)

### **Many-to-Many Relationships** (via junction tables):
- Package ↔ Service (packages include multiple services)
- Cart ↔ Venue/Service (cart contains multiple items)

## Scalability Considerations

### **Performance Optimization**:
- Primary keys as integers for fast indexing
- Datetime fields for temporal queries and reporting
- Status fields for efficient filtering

### **Data Integrity**:
- Foreign key constraints maintain referential integrity
- Boolean flags for simple state management
- Decimal types for precise financial calculations

### **Extensibility**:
- Generic review system for venues and services
- Flexible user types through string field
- Category-based service organization

## System Features Supported

✅ **Venue Search & Booking** - Availability, pricing, capacity management  
✅ **Service Marketplace** - Multiple vendors, categories, portfolios  
✅ **Event Management** - Dashboard, websites, invitations, budgets  
✅ **Shopping Cart** - Multiple items, event association  
✅ **Payment Processing** - Secure transactions, multiple methods  
✅ **Review System** - Customer feedback, moderation  
✅ **Site Visits** - Free venue inspections  
✅ **Package Deals** - Bundled services with discounts  
✅ **Real-time Availability** - Calendar management  
✅ **Admin Controls** - User management, content moderation

This ERD provides a solid foundation for the event planning platform, supporting all documented requirements while maintaining flexibility for future enhancements. 