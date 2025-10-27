# Java Swing Logistics Management System: Courier Cost & Time Predictor

## Overview
This is a full-featured desktop logistics/courier management system built with Java Swing.
- Predicts and compares delivery times and costs from various courier companies.
- Two user roles: Customer and Admin
- Integrates with a Weather API for real-world delivery time prediction.
- Uses a relational database (MySQL/SQLite/PostgreSQL via JDBC).

---

## Setup Instructions

### 1. Prerequisites

- Java JDK 11 or newer installed
- MySQL (or SQLite/PostgreSQL, adjust `db.properties` accordingly)
- [Download the JDBC driver for your DB and add to classpath](https://dev.mysql.com/downloads/connector/j/)

### 2. Database Setup

1. Create a new database (e.g., `logistics_db`)
2. Run the `schema.sql` script to create tables.
3. Run the `data.sql` script to insert test companies and users.

#### Example (MySQL CLI):

```sh
mysql -u root -p
CREATE DATABASE logistics_db;
USE logistics_db;
SOURCE schema.sql;
SOURCE data.sql;
```

### 3. Configure Application

- Edit `resources/db.properties` to match your DB config (`url`, `username`, `password`).
- Edit `com/project/service/WeatherService.java` to insert your Weather API key.

### 4. Build and Run

- Compile all Java files:

```sh
javac -cp ".;path/to/mysql-connector-java.jar" com/project/**/*.java
```

- Run the application:

```sh
java -cp ".;path/to/mysql-connector-java.jar" com.project.Main
```

### 5. Default Logins

- **Admin:**  
  Username: `admin1`  
  Password: `Admin@123`
- **User:**  
  Username: `user1`  
  Password: `User@123`

---

## Project Structure

- `com.project`  
  - `gui` - All Swing UI classes  
  - `db` - Database connection and DAOs  
  - `service` - Business logic, API integration  
  - `model` - Java Beans for entities

- `resources/` - Configuration files

---

## Weather API

- Uses [OpenWeatherMap](https://openweathermap.org/current)
- Free API key required. Insert key in `WeatherService.java` as explained in code comments.

---

## Notes

- Passwords are securely hashed using SHA-256.
- You can switch the DB to SQLite/PostgreSQL by changing the JDBC URL and driver.

---

## License

MIT (public domain educational starter)
