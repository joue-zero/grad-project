An activity diagram for the "Book Venue" process.
Activity diagrams show the flow of activities and decision points in a business process.

## **Activity Diagram Components:**

### **🟢 Start/End Points:**
- **Green ovals**: Start and successful end points
- **Pink oval**: Cancelled booking end point

### **🔷 Decision Points (Diamond shapes):**
- **Venues found?** - Check if search returns results
- **Date available?** - Real-time availability check
- **Form valid?** - Validation of booking information
- **Confirm booking?** - Customer final confirmation
- **Payment successful?** - Payment processing result
- **Choose different date?** - Alternative date selection
- **Retry payment?** - Payment retry option

### **📋 Activities (Rectangles):**
- Search and filter venues
- View venue details
- Fill booking forms
- Process payments
- Send notifications
- Update system status

## **Key Process Flows:**

### **1. Happy Path (Success):**
Search → Find venues → Select → Check availability → Fill form → Confirm → Pay → Success

### **2. Alternative Paths:**
- **No venues found** → Update filters → Search again
- **Date unavailable** → Choose different date OR go back to venue list
- **Invalid form** → Show errors → Fix form
- **Payment fails** → Retry payment OR cancel booking

## **Key Differences from Sequence Diagram:**

| **Sequence Diagram** | **Activity Diagram** |
|---------------------|---------------------|
| Shows **WHO** does **WHAT** | Shows **WHAT** activities happen |
| Focus on **interactions** between actors | Focus on **workflow** and **decision points** |
| Time-based flow | Process-based flow |
| Object communication | Business logic flow |

The activity diagram provides a **customer-centric view** of the booking process, showing all the decisions and alternative paths a user might take during venue booking.
