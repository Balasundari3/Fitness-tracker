# Fitness Tracker - Spring Boot Application

A comprehensive fitness center management system built with Spring Boot, Oracle Database, and modern web interface.

## Features

### 🔐 Admin Authentication
- Secure login system with username and password
- Default admin credentials: `admin` / `admin123`

### 👥 Member Management
- **Add Member**: Register new gym members with details like:
  - User ID (unique identifier)
  - Full Name
  - Phone Number
  - Weight and Height
  - Workout Schedule
- **Manage Member**: 
  - Search members by User ID
  - View complete member details
  - Update workout type and duration
  - View all members list

### 💰 Payment Management
- **Add Payment**: Record payment transactions with:
  - User ID
  - Amount
  - Payment Date
  - Description
- **Payment History**: Filter payments by:
  - Today
  - Yesterday
  - This Month
  - All Payments

### 🎨 Modern UI
- Responsive design with gradient backgrounds
- Interactive cards and hover effects
- Clean and professional interface
- Mobile-friendly layout

## Technology Stack

- **Backend**: Spring Boot 2.x
- **Database**: Oracle Database
- **ORM**: JPA/Hibernate
- **Frontend**: HTML5, CSS3, JavaScript
- **Build Tool**: Maven

## Prerequisites

- Java 8 or higher
- Oracle Database (XE or higher)
- Maven 3.6+
- Spring Tool Suite (STS) or any Java IDE

## Setup Instructions

### 1. Database Setup
1. Install Oracle Database (XE recommended for development)
2. Create a new user/schema for the application
3. Grant necessary privileges to the user

### 2. Application Configuration
1. Open `src/main/resources/application.properties`
2. Update the database connection details:
   ```properties
   spring.datasource.url=jdbc:oracle:thin:@localhost:1521:XE
   spring.datasource.username=your_username
   spring.datasource.password=your_password
   ```

### 3. Dependencies
Add the following dependencies to your `pom.xml`:

```xml
<dependencies>
    <!-- Spring Boot Starter Web -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    
    <!-- Spring Boot Starter Data JPA -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    
    <!-- Oracle JDBC Driver -->
    <dependency>
        <groupId>com.oracle.database.jdbc</groupId>
        <artifactId>ojdbc8</artifactId>
        <scope>runtime</scope>
    </dependency>
    
    <!-- Spring Boot Starter Test -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>
```

### 4. Import to Spring Tool Suite
1. Open Spring Tool Suite
2. Go to File → Import → Existing Maven Projects
3. Browse to the project directory
4. Select the project and click Finish
5. Wait for Maven to download dependencies

### 5. Run the Application
1. Right-click on the project
2. Select Run As → Spring Boot App
3. The application will start on `http://localhost:8080`

## API Endpoints

### Admin
- `POST /api/admin/login` - Admin login
- `POST /api/admin/create` - Create new admin

### Members
- `POST /api/members/add` - Add new member
- `GET /api/members/all` - Get all members
- `GET /api/members/{userId}` - Get member by User ID
- `PUT /api/members/update` - Update member
- `PUT /api/members/workout` - Update workout details
- `DELETE /api/members/{id}` - Delete member

### Payments
- `POST /api/payments/add` - Add new payment
- `GET /api/payments/all` - Get all payments
- `GET /api/payments/user/{userId}` - Get payments by User ID
- `GET /api/payments/today` - Get today's payments
- `GET /api/payments/yesterday` - Get yesterday's payments
- `GET /api/payments/this-month` - Get this month's payments
- `GET /api/payments/filter?filter={filter}` - Filter payments

## Database Schema

The application automatically creates the following tables:
- `ADMIN` - Admin user credentials
- `MEMBERS` - Member information
- `PAYMENTS` - Payment transactions

## Testing with Postman

### Admin Login
```
POST http://localhost:8080/api/admin/login
Content-Type: application/json

{
    "username": "admin",
    "password": "admin123"
}
```

### Add Member
```
POST http://localhost:8080/api/members/add
Content-Type: application/json

{
    "userId": "M001",
    "name": "John Doe",
    "phoneNumber": "1234567890",
    "weight": 70.5,
    "height": 175.0,
    "workoutSchedule": "Morning (6AM-9AM)"
}
```

### Add Payment
```
POST http://localhost:8080/api/payments/add
Content-Type: application/json

{
    "userId": "M001",
    "amount": 50.00,
    "paymentDate": "2024-01-15",
    "description": "Monthly membership fee"
}
```

## File Structure

```
src/
├── main/
│   ├── java/com/fitness/
│   │   ├── FitnessTrackerApplication.java
│   │   ├── config/
│   │   │   └── DataInitializer.java
│   │   ├── controller/
│   │   │   ├── AdminController.java
│   │   │   ├── MemberController.java
│   │   │   └── PaymentController.java
│   │   ├── entity/
│   │   │   ├── Admin.java
│   │   │   ├── Member.java
│   │   │   └── Payment.java
│   │   ├── repository/
│   │   │   ├── AdminRepository.java
│   │   │   ├── MemberRepository.java
│   │   │   └── PaymentRepository.java
│   │   └── service/
│   │       ├── AdminService.java
│   │       ├── MemberService.java
│   │       └── PaymentService.java
│   └── resources/
│       ├── application.properties
│       └── static/
│           ├── index.html
│           ├── dashboard.html
│           ├── add-member.html
│           ├── manage-member.html
│           └── payment-history.html
```

## Troubleshooting

### Common Issues

1. **Database Connection Error**
   - Verify Oracle Database is running
   - Check connection details in `application.properties`
   - Ensure Oracle JDBC driver is in classpath

2. **Port Already in Use**
   - Change port in `application.properties`: `server.port=8081`

3. **Maven Dependencies**
   - Right-click project → Maven → Update Project
   - Clean and rebuild project

## Support

For any issues or questions, please check:
1. Application logs in console
2. Database connection status
3. Maven dependency resolution

## License

This project is for educational purposes. Feel free to modify and use as needed. 