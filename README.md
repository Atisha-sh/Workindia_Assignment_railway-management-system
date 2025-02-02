# Workindia_Assignment_railway-management-system

A comprehensive railway management system developed with Django, enabling users to register, log in, check seat availability, book tickets, and view their booking details. This system includes role-based access control (Admin and User) and ensures smooth handling of concurrent seat reservations to avoid race conditions.



---

##  Features

- 👥 **User Roles:** Distinct functions for Admin and User, ensuring clear role differentiation.
- 🔒 **Secure Bookings:** Advanced mechanisms to avoid double-booking issues, preventing race conditions.
- 🔑 **Effortless Authentication:** Simple login and registration processes for a smooth user experience.
- 📖 **APIs:** Well-documented and easy-to-integrate API endpoints for use in frontend applications or other systems.
- 🗄️ **Database Support:** PostgreSQL ensures reliable, efficient, and scalable data storage.
- ⏱️ **Real-time Updates:** Live updates on seat availability as booking actions are processed.
- 🛡️ **Role-based Access Control:** Admin endpoints are secured with API key authentication for added security.
- 🚆 **Customizable Trains:** Admins can add new trains, specifying the source, destination, and seat capacity. 
- 💻 **Platform Independence:** The system runs seamlessly on Windows, macOS, and Linux.  
- 📈 **Scalability:** Designed to handle a large number of users and simultaneous booking requests.  
- 🔧 **Extensibility:** Built with Django’s modularity to easily integrate new features or systems.  


---

##  Installation Steps

1. **Clone the Repository:**

    ```bash
   https://github.com/Atisha-sh/Workindia_Assignment_railway-management-system
    cd workindia_assignment_railway_management_system
    ```

2. **Create and Activate a Virtual Environment:**

    ```bash
    python -m venv venv
    source venv/bin/activate  # For Windows: `venv\Scripts\activate`
    ```

3. **Install Dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

4. **Install PostgreSQL** if not already installed. Refer to the [PostgreSQL Documentation](https://www.postgresql.org/docs/) for installation instructions.

5. **Set Up PostgreSQL Database:**

    ```bash
    psql -U postgres -c "CREATE DATABASE railway_management_test;"
    ```

6. **Update Database Settings:**

    Edit the `DATABASES` section in `settings.py` with your PostgreSQL credentials:

    ```python
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': 'railway_management_test',
            'USER': 'your_postgres_username',
            'PASSWORD': 'your_postgres_password', # put your password
            'HOST': 'localhost',
            'PORT': '5432',
        }
    }
    ```

---

## 🧑‍💻 Project Setup

1. **Apply Migrations:**

    ```bash
    python manage.py migrate
    ```

2. **Create a Superuser:**

    ```bash
    python manage.py createsuperuser
    ```

3. **Start the Development Server:**

    ```bash
    python manage.py runserver
    ```

---

## 🌐 API Endpoints

Below are the available API endpoints for the Railway Management System, along with example payloads and responses using the dummy user credentials.

---

### 🛂 Authentication Endpoints

1. **Register User**  
   - **Endpoint:** `/register/`  
   - **Method:** `POST`  
   - **Description:** Allows a user to register with a username, password, and role (Admin/User).  
   - **Request Payload:**
     ```json
     {
       "username": "atisha_shrivas",
       "password": "Atisha@123",
       "is_admin": false
     }
     ```
   - **Response Example:**
     ```json
     {
       "message": "User registered successfully",
       "user_id": 1
     }
     ```

2. **Login User**  
   - **Endpoint:** `/login/`  
   - **Method:** `POST`  
   - **Description:** Authenticates a user and returns a session token for subsequent requests.  
   - **Request Payload:**
     ```json
     {
       "username": "atisha_shrivas",
       "password": "Atisha@123"
     }
     ```
   - **Response Example:**
     ```json
     {
       "message": "Login successful",
       "token": "abcd1234efgh5678"
     }
     ```

---

### 🚆 Train Management Endpoints

1. **Add Train**  
   - **Endpoint:** `/add_train/`  
   - **Method:** `POST`  
   - **Description:** Enables an admin to add a new train with source, destination, and total seats.  
   - **Request Payload (Admin Credentials):**
     ```json
     {
       "source": "Station_A",
       "destination": "Station_B",
       "total_seats": 100
     }
     ```
   - **Response Example:**
     ```json
     {
       "message": "Train added successfully",
       "train_id": 10
     }
     ```

2. **Check Seat Availability**  
   - **Endpoint:** `/check_availability/Bhopal/Indore/`  
   - **Method:** `GET`  
   - **Description:** Checks the seat availability for a train between the specified source and destination.  
   - **Response Example:**
     ```json
     {
       "source": "Station_A",
       "destination": "Station_B",
       "available_seats": 50
     }
     ```

---

### 🪑 Booking Endpoints

1. **Book Seat**  
   - **Endpoint:** `/book_seat/`  
   - **Method:** `POST`  
   - **Description:** Allows users to book a seat for a specific train.  
   - **Request Payload:**
     ```json
     {
       "train_id": 10,
       "seats_to_book": 2
     }
     ```
   - **Response Example:**
     ```json
     {
       "message": "Seats booked successfully",
       "booking_id": 201,
       "booked_seats": 2
     }
     ```

2. **View Booking Details**  
   - **Endpoint:** `/booking_details/`  
   - **Method:** `GET`  
   - **Description:** Retrieves the booking details for the authenticated user.  
   - **Response Example:**
     ```json
     {
       "user_id": 1,
       "bookings": [
         {
           "booking_id": 201,
           "train_id": 10,
           "source": "Station_A",
           "destination": "Station_B",
           "seats_booked": 2,
           "date": "2025-02-02"
         }
       ]
     }
     ```


2. **Authorization Header:**  
   Include your API key in the header for admin-specific actions:
   ```bash
   Token: "Token <token_of_admin>"

Attaching Images:
![image](https://github.com/user-attachments/assets/3f1a2041-f145-4da3-a27a-603d092c95de)
![image](https://github.com/user-attachments/assets/6703bb10-288f-4663-a2fb-7305f33e69a8)
![image](https://github.com/user-attachments/assets/328dccd9-71a6-49b5-b9e1-7c334f0255ab)
![image](https://github.com/user-attachments/assets/7014cc01-320a-4ad1-80ee-ac963097bbe3)
![image](https://github.com/user-attachments/assets/5d119fe2-ca5a-4ed2-b3ed-80a734de6efa)
![image](https://github.com/user-attachments/assets/e2b3b80b-0f01-4613-b70b-56b8293e9565)
![image](https://github.com/user-attachments/assets/1ebff90c-7615-44c5-9674-446a555fdb31)
![image](https://github.com/user-attachments/assets/e3da0040-dc93-400e-ae77-d1dccc087e87)







