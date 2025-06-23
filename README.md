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


**Feature Breakdown**

1._User Management_:
Handles registration, login, profile editing, and authentication.

  Description:
- This feature allows users to sign up as guests or hosts, log in securely, and manage their profile information. It supports authentication, session management, and access control for different roles (e.g., only hosts can list properties).

2._Property Management_:
Enables hosts to list, edit, and delete properties.

  Description:
- Hosts can create detailed property listings, including descriptions, photos, pricing, location, and availability. This feature makes it possible for guests to browse various accommodation options and filter based on preferences.

3._Search and Filter_
Allows users to search properties by location, price, date, and more.

  Description:
- Users can find suitable properties by entering their travel details and applying filters such as price range, number of guests, or amenities. This improves the user experience by narrowing down listings quickly.

4._Booking System_:
Lets guests make reservations and manage upcoming or past bookings.

  Description:
- Guests can select available dates and submit booking requests for properties. The system calculates total prices and ensures no date overlaps. Hosts may accept or auto-confirm bookings depending on the design.

5._Review System_:
Enables guests to leave reviews and ratings after their stay.

  Description:
- Guests can share feedback on properties they've stayed in, which helps future users make informed decisions. Reviews contribute to credibility and quality control on the platform.

6._Payment Integration_:
Handles secure transactions for bookings.

  Description:
- This feature enables users to pay for bookings using payment gateways (e.g., Stripe, PayPal). It tracks payment status and links payments to bookings, ensuring smooth financial flow between guests, the platform, and hosts.

7._Messaging System_:
Facilitates communication between hosts and guests.

  Description:
- A messaging feature allows users to ask questions or clarify details before booking. This improves trust, transparency, and user engagement.

8._Admin Dashboard_:
For platform administrators to monitor activities and manage data.

  Description:
- Admins can oversee users, properties, bookings, and flagged reviews or listings. This is crucial for maintaining the integrity and security of the platform.


**API Security**

1. _User Data_:
- Protecting identity, contact information, and private activity.

2. _Payments_:
- Preventing fraud and securing sensitive financial details.

4. _Bookings_:
- Avoiding conflicts, theft, or abuse of property access.

5. _Review & Listings_:
- Preventing fake content or manipulation of ratings.

6. _API & Server_:
- Guarding against system downtime or data breach.

  
**CI/CD Pipeline**

⚙️ _What Are CI/CD Pipelines?_

- _CI/CD_ stands for _Continuous Integration_ and _Continuous Deployment/Delivery_.

1. _Continuous Integration (CI)_:
        Automatically tests and integrates code changes (like new features or bug fixes) into the main codebase. This ensures new commits don’t break the app.

2. _Continuous Deployment (CD)_:
        Automatically builds, tests, and deploys your app to a server or cloud platform whenever changes are merged.

