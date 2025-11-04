# Airbnb Clone — Backend Requirements

This document explains the main backend features of the Airbnb Clone project.  
It describes what each feature does, how the API works, and what rules or checks are needed.

---

## 1. User Authentication

### Description
Manages how users register, log in, and view their profiles.  
Supports three roles: guest, host, and admin.

### API Endpoints
| Method | Endpoint | Description |
|---------|-----------|-------------|
| POST | `/api/users/register` | Register a new user |
| POST | `/api/users/login` | Log in and get a token |
| GET | `/api/users/profile` | Get user profile details |

### Data
- **Input:** email, password, role (guest, host, admin)  
- **Output:** user info and authentication token  

### Rules
- Email must be unique and valid  
- Password must be at least 8 characters  

### Performance
- Response time under 300ms  
- Passwords stored securely (hashed)

---

## 2. Property Management

### Description
Lets hosts add, edit, or delete their property listings.

### API Endpoints
| Method | Endpoint | Description |
|---------|-----------|-------------|
| POST | `/api/properties` | Add a new property |
| GET | `/api/properties` | View all properties |
| PUT | `/api/properties/{id}` | Update a property |
| DELETE | `/api/properties/{id}` | Delete a property |

### Data
- **Input:** name, description, location, price_per_night, amenities  
- **Output:** property info with a unique ID  

### Rules
- Price must be a positive number  
- All required fields must be filled  

### Performance
- Retrieve up to 100 listings in under 500ms  
- Use indexes for faster searches  

---

## 3. Booking System

### Description
Handles property reservations between guests and hosts.

### API Endpoints
| Method | Endpoint | Description |
|---------|-----------|-------------|
| POST | `/api/bookings` | Create a booking |
| GET | `/api/bookings/{id}` | Get booking details |
| PUT | `/api/bookings/{id}` | Update booking status |
| DELETE | `/api/bookings/{id}` | Cancel a booking |

### Data
- **Input:** user_id, property_id, start_date, end_date  
- **Output:** booking details and total cost  

### Rules
- Check if property is available  
- Start date must come before end date  

### Performance
- Avoid double bookings  
- Response time under 400ms  

---

## Summary
This document covers the main backend features: user authentication, property management, and booking.  
It defines the endpoints, data rules, and performance goals for a reliable and scalable Airbnb Clone system.
