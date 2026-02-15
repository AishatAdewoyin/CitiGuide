# 📍 CitiGuide Mobile Application

CitiGuide is a mobile application designed to help residents and tourists explore cities efficiently.  
The app provides information about attractions, restaurants, hotels, and events, along with reviews, maps, and personalized user features.

---

## 🏗 Tech Stack

### Frontend (Mobile)
- Flutter
- Dart
- Google Maps SDK
- HTTP (REST API integration)

### Backend (API Server)
- Java 17
- Spring Boot
- Spring Security (JWT Authentication)
- Spring Data JPA (Hibernate)
- MySQL Database
- Maven

### Database
- MySQL 8+

---

## 🧱 System Architecture

Flutter Mobile App  
⬇ (REST API – JSON over HTTP)  
Spring Boot Backend  
⬇  
MySQL Database

---

## 📂 Project Structure

### Flutter (Frontend)
```
lib/
 ├── main.dart
 ├── models/
 ├── services/
 ├── screens/
 ├── widgets/
 └── utils/
```

### Spring Boot (Backend)
```
src/main/java/com/cityguide/
 ├── controller/
 ├── service/
 ├── repository/
 ├── model/
 ├── security/
 └── config/
```

---

## 🔐 Features

### 1. User Authentication
- Register
- Login
- JWT-based authentication
- Password reset
- Secure role-based access (User/Admin)

### 2. City Selection
- Browse available cities
- View city descriptions and images

### 3. Attractions
- List attractions by city
- Filter by category (restaurant, hotel, event, landmark)
- Sort by rating
- View detailed information

### 4. Reviews & Ratings
- Leave reviews
- 1–5 star rating system
- Like helpful reviews

### 5. Maps Integration
- Google Maps markers
- Directions from current location

### 6. Search
- Search by name or keywords
- Category filtering

### 7. User Profile
- Update profile info
- Manage favorites
- Notification preferences

### 8. Admin Dashboard (Web)
- Add/Edit/Delete attractions
- Moderate reviews
- Manage notifications

---

## 🗄 Database Schema

### Users
| Field | Type |
|-------|------|
| id | BIGINT (PK) |
| name | VARCHAR |
| email | VARCHAR (Unique) |
| password | VARCHAR |
| role | VARCHAR |
| profile_picture | VARCHAR |
| created_at | TIMESTAMP |

### Cities
| Field | Type |
|-------|------|
| id | BIGINT (PK) |
| name | VARCHAR |
| description | TEXT |
| image_url | VARCHAR |
| country | VARCHAR |

### Attractions
| Field | Type |
|-------|------|
| id | BIGINT (PK) |
| city_id | BIGINT (FK) |
| name | VARCHAR |
| category | VARCHAR |
| description | TEXT |
| image_url | VARCHAR |
| address | VARCHAR |
| latitude | DOUBLE |
| longitude | DOUBLE |
| contact_info | VARCHAR |
| opening_hours | VARCHAR |
| website_url | VARCHAR |
| average_rating | DOUBLE |

### Reviews
| Field | Type |
|-------|------|
| id | BIGINT (PK) |
| user_id | BIGINT (FK) |
| attraction_id | BIGINT (FK) |
| rating | INT |
| comment | TEXT |
| likes_count | INT |
| created_at | TIMESTAMP |

### Favorites
| Field | Type |
|-------|------|
| id | BIGINT (PK) |
| user_id | BIGINT (FK) |
| attraction_id | BIGINT (FK) |

---

## ⚙️ Backend Setup (Spring Boot)

### 1️⃣ Clone Repository
```bash
git clone https://github.com/your-username/city-guide-backend.git
cd CitiGuide-backend
```

### 2️⃣ Configure Database

Update `application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/cityguide
spring.datasource.username=root
spring.datasource.password=yourpassword

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

jwt.secret=your_secret_key
jwt.expiration=86400000
```

### 3️⃣ Run Application

```bash
mvn spring-boot:run
```

Backend runs at:
```
http://localhost:8080
```

---

## 📱 Flutter Setup

### 1️⃣ Navigate to Flutter Project

```bash
cd CitiGuide
```

### 2️⃣ Install Dependencies

```bash
flutter pub get
```

### 3️⃣ Configure API Base URL

Inside `lib/utils/constants.dart`:

```dart
const String baseUrl = "http://10.0.2.2:8080/api";
```

(Use your local IP if testing on physical device)

### 4️⃣ Run App

```bash
flutter run
```

---

## 🔑 API Endpoints (Sample)

### Authentication
- `POST /api/auth/register`
- `POST /api/auth/login`

### Cities
- `GET /api/cities`
- `GET /api/cities/{id}`

### Attractions
- `GET /api/attractions?cityId=1`
- `GET /api/attractions/{id}`
- `POST /api/attractions` (Admin)

### Reviews
- `POST /api/reviews`
- `GET /api/reviews/{attractionId}`

---

## 🚀 Deployment

### Backend
- Deploy on:
    - Render
    - AWS EC2
    - Railway

### Database
- MySQL Cloud (PlanetScale / AWS RDS)

### Mobile
- Build APK:
```bash
flutter build apk
```

---

## 📈 Non-Functional Requirements Implementation

- JWT authentication for secure access
- Indexed database columns for faster queries
- Pagination on listing endpoints
- Lazy image loading
- Input validation and exception handling
- Role-based authorization

---

## 📚 Documentation

- User Guide included in `/docs/user-guide.md`
- Developer API Documentation via Swagger:
```
http://localhost:8080/swagger-ui.html
```

---

## 🎥 Demonstration Video

We have complete demonstration video showcasing:
- User Registration & Login
- City selection
- Attraction browsing
- Review submission
- Admin management features

(Video file included in our submission package)

---

## 👩‍💻 Authors

- Aishat Adewoyin
- Hauwa Abubakar
- Daniela

---

## 📜 License

This project is developed for as our semester 3 project in the Aptech Nigeria's ADSE(AI/ML - Java) Program.