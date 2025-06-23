# airbnb-clone-project
**Team Roles**

1._Front-end developers_:
Create the part of the application that users will interact with, ensuring that the app offers an equally smooth experience to all ~ no matter the device, platform, or operational system.

2._Back-end developers_:
Implement the core of the app.


**Technology Stack**

1._OpenAPI Standard_:
The backend API has been documented using the OpenAPI standard to ensure clarity and ease of integration.

2._Django REST Framework_:
Provide a comprehensive RESTful API, handling CRUD operations on user and property data.

3._GraphQL_:
Offer a flexible and efficient query mechanism for interacting with the backend


**Database Design**
1._Users_:
Represents people who use the platform (guests or hosts).

  Fields:

    id (Primary Key)
    
    name
    
    email (Unique)
    
    password_hash
    
    is_host (Boolean to distinguish between guest/host)

  Relationships:

- One user can own many properties.
- One user can make many bookings.
- One user can write many reviews.

2._Properties_:
Represents a place listed on the platform.

  Fields:

    id (Primary Key)
    
    title
    
    description
    
    location (could be city, state, country or a full address)
    
    price_per_night
    
    host_id (Foreign Key → Users.id)

  Relationships:
- One property belongs to one host (user).
- One property can have many bookings.
- One property can have many reviews.

3._Bookings_:
Represents a reservation made by a guest.

  Fields:

    id (Primary Key)
    
    user_id (Foreign Key → Users.id)
    
    property_id (Foreign Key → Properties.id)
    
    start_date
    
    end_date
    
    total_price

  Relationships:

- One booking belongs to one user.
- One booking belongs to one property.

4._Reviews_:
Represents a user's feedback about a property after a stay.

  Fields:

    id (Primary Key)
    
    user_id (Foreign Key → Users.id)
    
    property_id (Foreign Key → Properties.id)
    
    rating (e.g., 1–5 stars)
    
    comment

  Relationships:

- One review belongs to one user.
- One review belongs to one property.
- A user can only leave one review per booking/property (optional constraint).

5._Payments_:
Represents a payment made for a booking.

  Fields:

    id (Primary Key)
    
    booking_id (Foreign Key → Bookings.id)
    
    amount
    
    payment_method (e.g., card, PayPal)
    
    status (e.g., success, failed)

  Relationships:

- One payment is linked to one booking.
- One booking can have one or more payment attempts (depending on business rules).
