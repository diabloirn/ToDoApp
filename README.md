# ToDo App - Framework Layer Architecture 

<div align="center">

**A Modern Task Management Application implementing Framework Layer Architecture with Java Spring Boot Backend and Kotlin Android Frontend**

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Framework Layer Architecture](#framework-layer-architecture)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Features](#features)
- [Architecture Layers](#architecture-layers)
- [Installation & Setup](#installation--setup)
- [Backend Setup (Spring Boot)](#backend-setup-spring-boot)
- [Frontend Setup (Android)](#frontend-setup-android)
- [API Documentation](#api-documentation)
- [Database Schema](#database-schema)
- [Design Patterns](#design-patterns)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)

---

## 🎯 Overview

**ToDo App** adalah aplikasi manajemen tugas modern yang dibangun untuk mendemonstrasikan implementasi **Framework Layer Architecture (FLA)** dalam pengembangan software profesional. Aplikasi ini mengintegrasikan backend REST API menggunakan **Java Spring Boot** dengan frontend mobile menggunakan **Kotlin** di platform Android.

Proyek ini dirancang sebagai pembelajaran mendalam tentang:
- ✅ Layered Architecture (Presentasi, Bisnis, Data)
- ✅ Design Patterns (Factory, Builder, Strategy, Adapter)
- ✅ SOLID Principles
- ✅ RESTful API Design
- ✅ Clean Code Architecture
- ✅ Security Best Practices

---

## 🏗️ Framework Layer Architecture

### Penjelasan FLA

**Framework Layer Architecture** adalah pola desain yang mengorganisir aplikasi ke dalam lapisan-lapisan yang terpisah dan independen. Setiap lapisan memiliki tanggung jawab spesifik dan berinteraksi dengan lapisan lain melalui interface yang jelas.

### Komponen Utama FLA:

```
┌─────────────────────────────────────────┐
│     PRESENTATION LAYER (UI)             │
│  (Android Activities, Fragments, VM)    │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│   APPLICATION LAYER (Orchestration)     │
│  (Controllers, Use Cases, Presenters)   │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│    BUSINESS LOGIC LAYER (Domain)        │
│  (Services, Validators, Processors)     │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│   DATA ACCESS LAYER (Persistence)       │
│  (Repositories, DAO, Database Access)   │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│    INFRASTRUCTURE LAYER (Technical)     │
│  (Database, API Calls, Cache, Config)   │
└─────────────────────────────────────────┘
```

---

## 💻 Technology Stack

### Backend (Spring Boot)
| Teknologi | Versi | Keterangan |
|-----------|-------|-----------|
| **Java** | 21+ | Bahasa pemrograman utama backend |
| **Spring Boot** | 4.1.0-SNAPSHOT | Framework web dan IoC |
| **Spring Data JPA** | Latest | ORM dan database abstraction |
| **Spring Security** | Latest | Authentication & Authorization |
| **Spring Validation** | Latest | Input validation & constraints |
| **PostgreSQL** | Latest | Database relasional |
| **Lombok** | Latest | Code generation & boilerplate reduction |
| **Maven** | 3.8+ | Build tool & dependency management |

### Frontend (Android)
| Teknologi | Versi | Keterangan |
|-----------|-------|-----------|
| **Kotlin** | 1.9+ | Bahasa pemrograman utama frontend |
| **Java** | 21+ | Support untuk legacy code |
| **Android SDK** | 33+ | Target Android platform |
| **Retrofit** | 2.9+ | HTTP client library |
| **MVVM Architecture** | - | Architectural pattern |
| **Material Design 3** | Latest | UI/UX design system |
| **Navigation Component** | Latest | In-app navigation |
| **Room Database** | Latest | Local data persistence |

### Tools & Infrastructure
- **Git** - Version control
- **Docker** - Containerization (Backend)
- **Gradle** - Android build system
- **Docker Compose** - Multi-container orchestration
- **Postman** - API testing
- **Android Studio** - IDE development

---

## 📁 Project Structure

```
ToDoApp/
├── README.md                          # Main documentation
│
├── ToDoApp_FLA/                       # Android Frontend (Kotlin)
│   ├── app/
│   │   ├── src/
│   │   │   ├── main/
│   │   │   │   ├── java/id/hanifalfaqih/todoapp/
│   │   │   │   │   ├── MainActivity.kt
│   │   │   │   │   ├── MainApplication.kt
│   │   │   │   │   ├── ui/
│   │   │   │   │   │   ├── activity/       # Activities
│   │   │   │   │   │   ├── fragment/       # Fragments (Presentation Layer)
│   │   │   │   │   │   └── viewmodel/      # ViewModels
│   │   │   │   │   ├── data/
│   │   │   │   │   │   ├── model/          # Data Models (DTO)
│   │   │   │   │   │   ├── repository/     # Repository Pattern (Data Layer)
│   │   │   │   │   │   ├── local/          # Local Database (Room)
│   │   │   │   │   │   └── remote/         # Remote API (Retrofit)
│   │   │   │   │   ├── domain/
│   │   │   │   │   │   ├── model/          # Domain Models
│   │   │   │   │   │   ├── repository/     # Repository Interfaces
│   │   │   │   │   │   └── usecase/        # Use Cases
│   │   │   │   │   ├── di/                 # Dependency Injection
│   │   │   │   │   ├── mapper/             # Data Mappers
│   │   │   │   │   └── util/               # Utilities
│   │   │   │   ├── res/
│   │   │   │   │   ├── drawable/           # Icons & Images
│   │   │   │   │   ├── layout/             # XML Layouts
│   │   │   │   │   ├── values/             # String, Colors, Themes
│   │   │   │   │   └── navigation/         # Navigation Graphs
│   │   │   │   └── AndroidManifest.xml
│   │   │   ├── androidTest/                # Instrumentation Tests
│   │   │   └── test/                       # Unit Tests
│   │   └── build.gradle.kts                # Android build configuration
│   ├── gradle/                             # Gradle wrapper files
│   ├── build.gradle.kts                    # Root build configuration
│   ├── settings.gradle.kts
│   └── README.md
│
├── TodoApp-SpringBoot/                     # Java Spring Boot Backend
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/TodoApp/
│   │   │   │   ├── TodoAppApplication.java # Main Spring Boot Application
│   │   │   │   ├── controller/             # REST Controllers (Presentation Layer)
│   │   │   │   │   ├── AuthController.java
│   │   │   │   │   ├── TaskController.java
│   │   │   │   │   └── TestController.java
│   │   │   │   ├── service/                # Business Logic Layer
│   │   │   │   │   ├── TaskService.java
│   │   │   │   │   ├── UserService.java
│   │   │   │   │   └── AuthService.java
│   │   │   │   ├── repository/             # Data Access Layer (JPA Repositories)
│   │   │   │   │   ├── TaskRepository.java
│   │   │   │   │   └── UserRepository.java
│   │   │   │   ├── entity/                 # JPA Entity Classes
│   │   │   │   │   ├── Task.java
│   │   │   │   │   ├── User.java
│   │   │   │   │   └── Role.java
│   │   │   │   ├── dto/                    # Data Transfer Objects
│   │   │   │   │   ├── TaskDTO.java
│   │   │   │   │   ├── UserDTO.java
│   │   │   │   │   └── AuthRequestDTO.java
│   │   │   │   ├── mapper/                 # DTO <-> Entity Mappers
│   │   │   │   │   ├── TaskMapper.java
│   │   │   │   │   └── UserMapper.java
│   │   │   │   ├── config/                 # Configuration Classes
│   │   │   │   │   ├── SecurityConfig.java
│   │   │   │   │   ├── WebConfig.java
│   │   │   │   │   └── DatabaseConfig.java
│   │   │   │   ├── security/               # Security & JWT
│   │   │   │   │   ├── JwtTokenProvider.java
│   │   │   │   │   ├── JwtAuthenticationFilter.java
│   │   │   │   │   └── SecurityUtil.java
│   │   │   │   ├── exception/              # Custom Exceptions
│   │   │   │   │   ├── ResourceNotFoundException.java
│   │   │   │   │   ├── UnauthorizedException.java
│   │   │   │   │   └── ValidationException.java
│   │   │   │   ├── builder/                # Builder Pattern
│   │   │   │   │   ├── TaskBuilder.java
│   │   │   │   │   └── UserBuilder.java
│   │   │   │   ├── factory/                # Factory Pattern
│   │   │   │   │   ├── EntityFactory.java
│   │   │   │   │   └── ServiceFactory.java
│   │   │   │   ├── strategy/               # Strategy Pattern
│   │   │   │   │   ├── SortStrategy.java
│   │   │   │   │   └── FilterStrategy.java
│   │   │   │   └── util/                   # Utility Classes
│   │   │   └── resources/
│   │   │       └── application.properties   # Spring configuration
│   │   └── test/
│   │       └── java/                       # Unit Tests
│   ├── pom.xml                             # Maven configuration
│   ├── docker-compose.yml                  # Docker environment setup
│   ├── data.sql                            # Initial database data
│   ├── mvnw & mvnw.cmd                     # Maven wrapper
│   └── README.md
│
└── docker-compose.yml                      # Root Docker Compose (if applicable)
```

---

## ✨ Features

### 🔐 Authentication & Authorization
- ✅ User Registration dengan validasi
- ✅ User Login dengan JWT Token
- ✅ Role-based Access Control (Admin, User)
- ✅ Secure password hashing (BCrypt)
- ✅ Token refresh mechanism
- ✅ Session management

### 📝 Task Management
- ✅ Create new tasks dengan deadline
- ✅ Edit existing tasks
- ✅ Delete tasks
- ✅ Mark tasks as complete/incomplete
- ✅ Set task priorities (High, Medium, Low)
- ✅ Add task descriptions & notes
- ✅ Assign tags to tasks
- ✅ Filter tasks by priority, status, tags
- ✅ Search tasks by keywords
- ✅ Sort tasks by date, priority

### 👤 User Profile Management
- ✅ View user profile
- ✅ Edit profile information
- ✅ Change password
- ✅ Upload profile picture
- ✅ View task statistics
- ✅ Export tasks data

### 📊 Dashboard & Analytics
- ✅ Task statistics overview
- ✅ Completion rate tracking
- ✅ Priority distribution chart
- ✅ Calendar view for scheduled tasks
- ✅ Recent activity log
- ✅ Task completion timeline

### 🔔 Notifications
- ✅ Task deadline reminders
- ✅ Task completion notifications
- ✅ Push notifications (Android)
- ✅ In-app notifications

---

## 🏛️ Architecture Layers

### 1. **Presentation Layer** (UI/UX)
**Lokasi:** Backend: `controller/`, Frontend: `ui/`

**Tanggung Jawab:**
- Menampilkan data kepada pengguna
- Mengumpulkan input dari pengguna
- Format data untuk ditampilkan
- Handle user interactions

**Komponen Utama:**
```
Backend:
├── AuthController - Endpoint authentikasi
├── TaskController - Endpoint manajemen tugas
└── TestController - Endpoint testing

Frontend:
├── Activities - Screen utama aplikasi
├── Fragments - Sub-screens/components
├── ViewModels - State management
└── UI Components - Custom views
```

**Tanggung Jawab:**
- REST API endpoints
- HTTP request/response handling
- Input validation untuk HTTP requests
- Exception handling dan error responses

### 2. **Application/Business Logic Layer**
**Lokasi:** Backend: `service/`, Frontend: `domain/usecase/`

**Tanggung Jawab:**
- Implementasi business rules
- Orchestration antara layers
- Data transformation & processing
- Use case handling

**Komponen Utama:**
```
Backend (Services):
├── TaskService - Business logic untuk tasks
├── UserService - User management logic
└── AuthService - Authentication logic

Frontend:
├── TaskUseCase - Business rules untuk tasks
├── UserUseCase - User management rules
└── AuthUseCase - Authentication rules
```

**Key Points:**
- Independent dari framework
- Testable dan reusable
- Contains core business logic
- Orchestrates data flow

### 3. **Data Access Layer (Persistence)**
**Lokasi:** Backend: `repository/`, Frontend: `data/repository/`

**Tanggung Jawab:**
- CRUD operations untuk database
- Query database
- Transaction management
- Data consistency

**Komponen Utama:**
```
Backend:
├── TaskRepository - Interface JPA untuk Task
├── UserRepository - Interface JPA untuk User
└── Custom Query Methods

Frontend:
├── TaskLocalRepository - Local database access
├── TaskRemoteRepository - API calls
└── TaskDataStore - Cache layer
```

**Implementasi:**
- JPA/Spring Data repositories (Backend)
- Room Database (Frontend Local)
- Retrofit (Frontend Remote)

### 4. **Entity/Model Layer**
**Lokasi:** Backend: `entity/`, Frontend: `domain/model/`

**Tanggung Jawab:**
- Represent data structure
- Database mapping
- Domain model representation

**Komponen Utama:**
```
Backend (JPA Entities):
├── @Entity Task
├── @Entity User
└── @Entity Role

Frontend (Domain Models):
├── Task
├── User
└── TaskTag
```

### 5. **Infrastructure/Technical Layer**
**Lokasi:** Backend: `config/`, `security/`, Frontend: `data/local/`, `data/remote/`

**Tanggung Jawab:**
- Database configuration
- Security setup
- API client configuration
- Logging & monitoring
- Cache management

**Komponen Utama:**
```
Backend:
├── SecurityConfig - Spring Security setup
├── DatabaseConfig - JPA & Hibernate config
└── WebConfig - Web layer configuration

Frontend:
├── RetrofitClient - HTTP client setup
├── RoomDatabase - Local database setup
└── NetworkConfig - Network configuration
```

### 6. **Cross-Cutting Concerns**
**Lokasi:** `mapper/`, `util/`, `exception/`

**Tanggung Jawab:**
- Data transformation (DTOs ↔ Entities)
- Exception handling
- Utility functions
- Logging

**Komponen Utama:**
```
Mappers:
├── TaskMapper - DTO ↔ Entity conversion
└── UserMapper - User data mapping

Exception Handling:
├── ResourceNotFoundException
├── UnauthorizedException
└── ValidationException

Utilities:
├── DateUtils
├── ValidationUtils
└── FormatUtils
```

---

### Data Flow Diagram

```
Frontend (Android):
┌──────────────┐
│  UI/Fragment │
└──────┬───────┘
       │
┌──────▼────────────┐
│ ViewModel/UseCase │
└──────┬────────────┘
       │
┌──────▼──────────────┐
│    Repository       │
├─────────┬───────────┤
│ Local   │  Remote   │
│(Room)   │(Retrofit) │
└──────┬──┴────┬──────┘
       │       │
       │    ┌──▼────────────────────┐
       │    │ Backend (Spring Boot)  │
       │    └──┬────────────────────┘
       │       │
       │    ┌──▼─────────────────┐
       │    │ Controller (REST)   │
       │    └──┬──────────────────┘
       │       │
       │    ┌──▼──────────────────┐
       │    │ Service (Business)   │
       │    └──┬──────────────────┘
       │       │
       │    ┌──▼────────────────────┐
       │    │ Repository (Data)     │
       │    └──┬───────────────────┘
       │       │
       └───────┼───────┐
               │       │
            ┌──▼──┐  ┌─▼────────┐
            │ Cache│  │Database  │
            └──────┘  └──────────┘
```

---

## 🚀 Installation & Setup

### Prerequisites

**Minimum Requirements:**
- Git 2.30+
- JDK 21 LTS atau lebih baru
- Android Studio 2023.3+
- PostgreSQL 12+
- Maven 3.8+ atau Gradle 7.0+
- Docker & Docker Compose (optional)

### Step 1: Clone Repository

```bash
# Clone repository
git clone https://github.com/hrry6/TodoApp-SpringBoot.git
cd ToDoApp

# Verify folder structure
ls -la
# Output: ToDoApp_FLA, TodoApp-SpringBoot
```

### Step 2: Environment Configuration

```bash
# Create .env files untuk konfigurasi
cd TodoApp-SpringBoot
cp .env.example .env

# Edit .env dengan credentials Anda
nano .env  # atau gunakan text editor pilihan Anda
```

---

## 🔧 Backend Setup (Spring Boot)

### Prerequisites Instalasi Backend
- JDK 21+
- PostgreSQL 12+
- Maven 3.8+
- Git

### Langkah-Langkah Setup

#### 1. Navigate ke Backend Directory
```bash
cd TodoApp-SpringBoot
```

#### 2. Database Setup

**Option A: Local PostgreSQL Installation**
```bash
# Windows (PowerShell)
# Install PostgreSQL via chocolatey
choco install postgresql

# Create database
psql -U postgres
postgres=# CREATE DATABASE tododb;
postgres=# CREATE USER todoapp WITH PASSWORD 'todoapp123';
postgres=# ALTER ROLE todoapp SET client_encoding TO 'utf8';
postgres=# ALTER ROLE todoapp SET default_transaction_isolation TO 'read committed';
postgres=# ALTER ROLE todoapp SET default_transaction_deferrable TO on;
postgres=# ALTER ROLE todoapp SET timezone TO 'UTC';
postgres=# GRANT ALL PRIVILEGES ON DATABASE tododb TO todoapp;
postgres=# \q
```

**Option B: Docker Container**
```bash
# Run PostgreSQL dalam Docker
docker run --name todoapp-postgres \
  -e POSTGRES_USER=todoapp \
  -e POSTGRES_PASSWORD=todoapp123 \
  -e POSTGRES_DB=tododb \
  -p 5432:5432 \
  -d postgres:15-alpine

# Verify
docker ps
```

**Option C: Docker Compose (Recommended)**
```bash
# Using docker-compose.yml
docker-compose up -d

# Verify services
docker-compose ps
```

#### 3. Configure Application Properties

**File:** `src/main/resources/application.properties`

```properties
# ==========================================
# Server Configuration
# ==========================================
server.port=8080
server.servlet.context-path=/api

# ==========================================
# Database Configuration
# ==========================================
spring.datasource.url=jdbc:postgresql://localhost:5432/tododb
spring.datasource.username=todoapp
spring.datasource.password=todoapp123
spring.datasource.driver-class-name=org.postgresql.Driver

# Hibernate/JPA Configuration
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=false
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.properties.hibernate.jdbc.batch_size=20
spring.jpa.properties.hibernate.order_inserts=true

# ==========================================
# Security Configuration
# ==========================================
app.jwtSecret=your-jwt-secret-key-min-32-chars-long
app.jwtExpirationInMs=86400000
app.jwtRefreshExpirationInMs=604800000

# ==========================================
# Logging Configuration
# ==========================================
logging.level.root=INFO
logging.level.com.example.TodoApp=DEBUG
logging.pattern.console=%d{yyyy-MM-dd HH:mm:ss} - %msg%n

# ==========================================
# Actuator Configuration (Monitoring)
# ==========================================
management.endpoints.web.exposure.include=health,metrics,info
management.endpoint.health.show-details=when-authorized
```

#### 4. Install Dependencies
```bash
# Using Maven
mvn clean install

# Or using Maven wrapper
./mvnw clean install

# Download dependencies
mvn dependency:resolve
```

#### 5. Build Project
```bash
# Compile code
mvn clean compile

# Package application
mvn clean package -DskipTests

# Output: target/TodoApp-0.0.1-SNAPSHOT.jar
```

#### 6. Run Application

```bash
# Option 1: Run dengan Maven
mvn spring-boot:run

# Option 2: Run JAR file
java -jar target/TodoApp-0.0.1-SNAPSHOT.jar

# Option 3: Run dengan IDE (Android Studio)
- Open TodoApp-SpringBoot folder
- Run TodoAppApplication.java
```

**Expected Output:**
```
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_|\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v4.1.0-SNAPSHOT)

2024-XX-XX 10:00:00.000  INFO 12345 --- [           main] c.example.TodoApp.TodoAppApplication    : 
Starting TodoAppApplication using Java 21
2024-XX-XX 10:00:05.000  INFO 12345 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : 
Tomcat initialized with port(s): 8080 (http)
2024-XX-XX 10:00:07.000  INFO 12345 --- [           main] c.example.TodoApp.TodoAppApplication    : 
Started TodoAppApplication in 7.123 seconds
```

#### 7. Verify Backend

```bash
# Test health endpoint
curl http://localhost:8080/api/health

# Expected response:
# {"status":"UP"}

# Test API
curl -X GET http://localhost:8080/api/test
```

#### 8. Load Initial Data (Optional)

```bash
# Gunakan data.sql untuk seed data
# File: src/main/resources/data.sql
# Akan otomatis diload saat spring startup

# Atau manual via psql
psql -U todoapp -d tododb -f data.sql
```

---

## 📱 Frontend Setup (Android)

### Prerequisites Instalasi Frontend
- Android Studio 2023.3+
- JDK 21+
- Kotlin Plugin 1.9+
- Android SDK 33+
- Gradle 7.0+

### Langkah-Langkah Setup

#### 1. Open Project di Android Studio

```bash
# Method 1: Command Line
cd ToDoApp_FLA
open -a "Android Studio" .  # macOS
# atau gunakan Android Studio untuk open folder

# Method 2: Android Studio GUI
- File → Open
- Select: ToDoApp_FLA folder
- Wait for Gradle sync
```

#### 2. Configure Gradle

**File:** `gradle.properties`
```properties
# ==========================================
# Gradle Configuration
# ==========================================
org.gradle.jvmargs=-Xmx2048m -XX:MaxPermSize=512m

# Enable parallel builds
org.gradle.parallel=true

# Use daemon
org.gradle.daemon=true

# Kotlin settings
kotlin.version=1.9.10
```

**File:** `gradle/libs.versions.toml`
```toml
[versions]
minSdk = "33"
targetSdk = "34"
compileSdk = "34"
kotlin = "1.9.10"
coroutines = "1.7.1"
retrofit = "2.9.0"
okhttp = "4.10.0"
```

#### 3. Configure API Endpoint

**File:** `app/src/main/java/id/hanifalfaqih/todoapp/config/ApiConfig.kt`

```kotlin
object ApiConfig {
    // Change based on your backend setup
    const val BASE_URL = "http://192.168.1.5:8080/api/"  // For emulator use
    // const val BASE_URL = "http://10.0.2.2:8080/api/"  // For Android emulator
    // const val BASE_URL = "http://localhost:8080/api/"  // For physical device on same network
    
    const val JWT_SECRET = "your-jwt-secret-key"
    const val CONNECTION_TIMEOUT = 30L
    const val READ_TIMEOUT = 30L
    const val WRITE_TIMEOUT = 30L
}
```

**Note:** Untuk emulator Android:
- Gunakan `10.0.2.2` untuk localhost
- Untuk physical device, gunakan IP internal (misal: 192.168.1.x)

#### 4. Install Dependencies

```bash
# Gradle akan otomatis download dependencies
# Proses dilakukan saat Android Studio syncing

# Atau manual:
cd ToDoApp_FLA
./gradlew dependencies

# Clean dan sync
./gradlew clean
./gradlew sync
```

#### 5. Build Project

```bash
# Build debug APK
./gradlew assembleDebug

# Build release APK
./gradlew assembleRelease

# Build and run
./gradlew installDebug
```

#### 6. Run Application

**Option 1: Via Android Studio**
- Click "Run" button atau tekan `Shift + F10`
- Select device/emulator
- Wait untuk build dan install

**Option 2: Via Command Line**
```bash
# Setup emulator
emulator -avd Pixel_5_API_33

# Run aplikasi
./gradlew installDebug
adb shell am start -n id.hanifalfaqih.todoapp/.MainActivity
```

#### 7. Configure AndroidManifest

**File:** `app/src/main/AndroidManifest.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <!-- Internet Permission untuk API calls -->
    <uses-permission android:name="android.permission.INTERNET" />
    
    <!-- Push Notifications -->
    <uses-permission android:name="android.permission.POST_NOTIFICATIONS" />
    
    <!-- Media Access -->
    <uses-permission android:name="android.permission.READ_MEDIA_IMAGES" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" 
        android:maxSdkVersion="32" />

    <application
        android:name=".MainApplication"
        android:allowBackup="true"
        android:label="@string/app_name"
        android:theme="@style/Theme.ToDoApp">
        
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

#### 8. Test Application

```bash
# Run unit tests
./gradlew testDebugUnitTest

# Run instrumented tests
./gradlew connectedAndroidTest

# Check test results
# Reports: build/test-results/
```

---

## 📡 API Documentation

### Base URL
```
http://localhost:8080/api
```

### Authentication
Semua endpoint (kecuali login & register) membutuhkan JWT token di header:

```
Authorization: Bearer <your-jwt-token>
```

### Response Format
Semua responses dalam format JSON:

```json
{
  "success": true,
  "message": "Operation successful",
  "data": {},
  "timestamp": "2024-01-15T10:30:00Z"
}
```

---

### 1. Authentication Endpoints

#### Register User
```http
POST /api/auth/register
Content-Type: application/json

{
  "username": "john_doe",
  "email": "john@example.com",
  "password": "SecurePass123!",
  "firstName": "John",
  "lastName": "Doe"
}
```

**Response (201 Created):**
```json
{
  "success": true,
  "message": "User registered successfully",
  "data": {
    "id": "123",
    "username": "john_doe",
    "email": "john@example.com",
    "firstName": "John",
    "lastName": "Doe",
    "createdAt": "2024-01-15T10:00:00Z"
  }
}
```

#### Login User
```http
POST /api/auth/login
Content-Type: application/json

{
  "username": "john_doe",
  "password": "SecurePass123!"
}
```

**Response (200 OK):**
```json
{
  "success": true,
  "message": "Login successful",
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "expiresIn": 86400,
    "user": {
      "id": "123",
      "username": "john_doe",
      "email": "john@example.com",
      "role": "USER"
    }
  }
}
```

#### Refresh Token
```http
POST /api/auth/refresh
Content-Type: application/json
Authorization: Bearer <your-refresh-token>

{}
```

---

### 2. Task Endpoints

#### Get All Tasks
```http
GET /api/tasks
Authorization: Bearer <token>
```

**Query Parameters:**
- `page` (default: 0) - Page number
- `size` (default: 20) - Items per page
- `sort` - Sort field (createdAt, priority, dueDate)
- `priority` - Filter by priority (HIGH, MEDIUM, LOW)
- `status` - Filter by status (TODO, IN_PROGRESS, COMPLETED)

**Response (200 OK):**
```json
{
  "success": true,
  "data": {
    "content": [
      {
        "id": "task-001",
        "title": "Complete project documentation",
        "description": "Write comprehensive documentation for the project",
        "priority": "HIGH",
        "status": "IN_PROGRESS",
        "dueDate": "2024-02-01",
        "tags": ["documentation", "important"],
        "completed": false,
        "completedAt": null,
        "createdAt": "2024-01-15T10:00:00Z",
        "updatedAt": "2024-01-15T12:00:00Z"
      }
    ],
    "totalElements": 15,
    "totalPages": 1,
    "currentPage": 0,
    "size": 20
  }
}
```

#### Get Task by ID
```http
GET /api/tasks/{taskId}
Authorization: Bearer <token>
```

**Response (200 OK):**
```json
{
  "success": true,
  "data": {
    "id": "task-001",
    "title": "Complete project documentation",
    "description": "Write comprehensive documentation for the project",
    "priority": "HIGH",
    "status": "IN_PROGRESS",
    "dueDate": "2024-02-01",
    "tags": ["documentation", "important"],
    "completed": false,
    "completedAt": null,
    "assignee": {
      "id": "user-123",
      "username": "john_doe",
      "email": "john@example.com"
    },
    "createdAt": "2024-01-15T10:00:00Z",
    "updatedAt": "2024-01-15T12:00:00Z"
  }
}
```

#### Create Task
```http
POST /api/tasks
Content-Type: application/json
Authorization: Bearer <token>

{
  "title": "Complete project documentation",
  "description": "Write comprehensive documentation for the project",
  "priority": "HIGH",
  "dueDate": "2024-02-01",
  "tags": ["documentation", "important"]
}
```

**Response (201 Created):**
```json
{
  "success": true,
  "message": "Task created successfully",
  "data": {
    "id": "task-001",
    "title": "Complete project documentation",
    "description": "Write comprehensive documentation for the project",
    "priority": "HIGH",
    "status": "TODO",
    "dueDate": "2024-02-01",
    "tags": ["documentation", "important"],
    "completed": false,
    "createdAt": "2024-01-15T10:00:00Z"
  }
}
```

#### Update Task
```http
PUT /api/tasks/{taskId}
Content-Type: application/json
Authorization: Bearer <token>

{
  "title": "Complete project documentation - UPDATED",
  "description": "Updated description",
  "priority": "MEDIUM",
  "status": "IN_PROGRESS",
  "dueDate": "2024-02-05",
  "tags": ["documentation", "updated"]
}
```

**Response (200 OK):**
```json
{
  "success": true,
  "message": "Task updated successfully",
  "data": {
    "id": "task-001",
    "title": "Complete project documentation - UPDATED",
    "description": "Updated description",
    "priority": "MEDIUM",
    "status": "IN_PROGRESS",
    "updatedAt": "2024-01-15T13:00:00Z"
  }
}
```

#### Delete Task
```http
DELETE /api/tasks/{taskId}
Authorization: Bearer <token>
```

**Response (204 No Content):**
```
(empty body)
```

#### Mark Task as Complete
```http
PATCH /api/tasks/{taskId}/complete
Authorization: Bearer <token>

{}
```

**Response (200 OK):**
```json
{
  "success": true,
  "message": "Task marked as completed",
  "data": {
    "id": "task-001",
    "status": "COMPLETED",
    "completed": true,
    "completedAt": "2024-01-15T13:30:00Z"
  }
}
```

#### Search Tasks
```http
GET /api/tasks/search?keyword=documentation&priority=HIGH
Authorization: Bearer <token>
```

---

### 3. User Profile Endpoints

#### Get Current User Profile
```http
GET /api/users/profile
Authorization: Bearer <token>
```

**Response (200 OK):**
```json
{
  "success": true,
  "data": {
    "id": "user-123",
    "username": "john_doe",
    "email": "john@example.com",
    "firstName": "John",
    "lastName": "Doe",
    "profilePicture": "https://api.example.com/images/profile-123.jpg",
    "createdAt": "2024-01-01T10:00:00Z",
    "updatedAt": "2024-01-15T10:00:00Z"
  }
}
```

#### Update User Profile
```http
PUT /api/users/profile
Content-Type: application/json
Authorization: Bearer <token>

{
  "firstName": "Jonathan",
  "lastName": "Doe",
  "email": "jonathan@example.com"
}
```

#### Change Password
```http
POST /api/users/change-password
Content-Type: application/json
Authorization: Bearer <token>

{
  "oldPassword": "OldPass123!",
  "newPassword": "NewPass123!",
  "confirmPassword": "NewPass123!"
}
```

---

### 4. Dashboard Endpoints

#### Get Task Statistics
```http
GET /api/dashboard/statistics
Authorization: Bearer <token>
```

**Response (200 OK):**
```json
{
  "success": true,
  "data": {
    "totalTasks": 25,
    "completedTasks": 15,
    "inProgressTasks": 7,
    "todoTasks": 3,
    "completionRate": 60.0,
    "highPriorityTasks": 5,
    "mediumPriorityTasks": 10,
    "lowPriorityTasks": 10,
    "tasksDueToday": 2,
    "tasksOverdue": 1,
    "tasksUpcoming": 3
  }
}
```

---

### Error Responses

#### 400 Bad Request
```json
{
  "success": false,
  "message": "Invalid input",
  "errors": {
    "title": "Title is required",
    "priority": "Priority must be HIGH, MEDIUM, or LOW"
  },
  "timestamp": "2024-01-15T10:00:00Z"
}
```

#### 401 Unauthorized
```json
{
  "success": false,
  "message": "Unauthorized - Invalid or expired token",
  "timestamp": "2024-01-15T10:00:00Z"
}
```

#### 403 Forbidden
```json
{
  "success": false,
  "message": "Forbidden - Insufficient permissions",
  "timestamp": "2024-01-15T10:00:00Z"
}
```

#### 404 Not Found
```json
{
  "success": false,
  "message": "Resource not found",
  "timestamp": "2024-01-15T10:00:00Z"
}
```

#### 500 Internal Server Error
```json
{
  "success": false,
  "message": "Internal server error",
  "error": "java.lang.NullPointerException: ...",
  "timestamp": "2024-01-15T10:00:00Z"
}
```

---

## 💾 Database Schema

### Entity Relationship Diagram

```
┌─────────────────┐          ┌──────────────────┐
│     Users       │          │     Roles        │
├─────────────────┤         ├──────────────────┤
│ id (PK)         │         │ id (PK)          │
│ username (UQ)   │         │ name (UQ)        │
│ email (UQ)      │◄────────┤ description      │
│ password_hash   │ (1)  (M) │ created_at       │
│ first_name      │         │ updated_at       │
│ last_name       │         └──────────────────┘
│ profile_picture │
│ is_active       │
│ created_at      │
│ updated_at      │
└─────────────────┘
        │
        │ (1)
        │
        ▼ (M)
┌─────────────────────┐
│     Tasks           │
├─────────────────────┤
│ id (PK)             │
│ user_id (FK) ◄──────┤
│ title               │
│ description         │
│ priority            │
│ status              │
│ due_date            │
│ completed           │
│ completed_at        │
│ created_at          │
│ updated_at          │
└─────────────────────┘
        │
        │ (1)
        │
        ▼ (M)
┌──────────────────┐
│   TaskTags       │
├──────────────────┤
│ id (PK)          │
│ task_id (FK)     │
│ tag_name         │
│ created_at       │
└──────────────────┘
```

### Tabel Users
```sql
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  username VARCHAR(50) UNIQUE NOT NULL,
  email VARCHAR(100) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  profile_picture VARCHAR(255),
  role_id UUID NOT NULL REFERENCES roles(id),
  is_active BOOLEAN DEFAULT true,
  last_login TIMESTAMP,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Tabel Tasks
```sql
CREATE TABLE tasks (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  title VARCHAR(255) NOT NULL,
  description TEXT,
  priority VARCHAR(20) DEFAULT 'MEDIUM' CHECK (priority IN ('HIGH', 'MEDIUM', 'LOW')),
  status VARCHAR(20) DEFAULT 'TODO' CHECK (status IN ('TODO', 'IN_PROGRESS', 'COMPLETED')),
  due_date DATE,
  completed BOOLEAN DEFAULT false,
  completed_at TIMESTAMP,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  CONSTRAINT check_completed_at CHECK (
    (completed = true AND completed_at IS NOT NULL) OR 
    (completed = false AND completed_at IS NULL)
  )
);
```

### Tabel Roles
```sql
CREATE TABLE roles (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(50) UNIQUE NOT NULL,
  description VARCHAR(255),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Sample Data
```sql
-- Insert Roles
INSERT INTO roles (name, description) VALUES
('ADMIN', 'Administrator with full access'),
('USER', 'Regular user with limited access');

-- Insert Users
INSERT INTO users (username, email, password_hash, first_name, last_name, role_id) VALUES
('admin', 'admin@example.com', '$2a$10$...', 'Admin', 'User', (SELECT id FROM roles WHERE name='ADMIN')),
('john_doe', 'john@example.com', '$2a$10$...', 'John', 'Doe', (SELECT id FROM roles WHERE name='USER'));

-- Insert Tasks
INSERT INTO tasks (user_id, title, description, priority, status, due_date) VALUES
((SELECT id FROM users WHERE username='john_doe'), 'Complete project documentation', '...', 'HIGH', 'IN_PROGRESS', '2024-02-01');
```

---

## 🎨 Design Patterns

### 1. **Repository Pattern**
**Purpose:** Abstraksi data access logic

**Implementation (Backend):**
```java
// Interface
public interface TaskRepository extends JpaRepository<Task, UUID> {
    List<Task> findByUserIdAndStatus(UUID userId, TaskStatus status);
    Page<Task> findByUserId(UUID userId, Pageable pageable);
}

// Implementation (Spring Data JPA handles this)
// Usage in Service:
@Service
public class TaskService {
    @Autowired
    private TaskRepository taskRepository;
    
    public List<Task> getUserTasks(UUID userId) {
        return taskRepository.findByUserId(userId);
    }
}
```

### 2. **Dependency Injection Pattern**
**Purpose:** Loose coupling dan testability

**Implementation:**
```java
@Service
public class TaskService {
    private final TaskRepository taskRepository;
    private final TaskMapper taskMapper;
    
    // Constructor Injection (preferred)
    public TaskService(TaskRepository taskRepository, TaskMapper taskMapper) {
        this.taskRepository = taskRepository;
        this.taskMapper = taskMapper;
    }
    
    // Or Annotation Injection
    @Autowired
    private NotificationService notificationService;
}
```

### 3. **Builder Pattern**
**Purpose:** Complex object construction

**Implementation:**
```java
public class TaskBuilder {
    private UUID id;
    private String title;
    private String description;
    private TaskPriority priority = TaskPriority.MEDIUM;
    private TaskStatus status = TaskStatus.TODO;
    
    public TaskBuilder withTitle(String title) {
        this.title = title;
        return this;
    }
    
    public TaskBuilder withPriority(TaskPriority priority) {
        this.priority = priority;
        return this;
    }
    
    public Task build() {
        return new Task(id, title, description, priority, status);
    }
}

// Usage
Task task = new TaskBuilder()
    .withTitle("My Task")
    .withPriority(TaskPriority.HIGH)
    .build();
```

### 4. **Factory Pattern**
**Purpose:** Object creation abstraction

**Implementation:**
```java
public class ServiceFactory {
    public static TaskService createTaskService(
            TaskRepository taskRepository, 
            TaskMapper taskMapper) {
        return new TaskService(taskRepository, taskMapper);
    }
}
```

### 5. **Strategy Pattern**
**Purpose:** Interchangeable algorithms

**Implementation:**
```java
public interface SortStrategy {
    List<Task> sort(List<Task> tasks);
}

public class SortByDueDateStrategy implements SortStrategy {
    @Override
    public List<Task> sort(List<Task> tasks) {
        return tasks.stream()
            .sorted(Comparator.comparing(Task::getDueDate))
            .collect(Collectors.toList());
    }
}

public class SortByPriorityStrategy implements SortStrategy {
    @Override
    public List<Task> sort(List<Task> tasks) {
        return tasks.stream()
            .sorted(Comparator.comparing(Task::getPriority).reversed())
            .collect(Collectors.toList());
    }
}

// Usage
SortStrategy strategy = new SortByDueDateStrategy();
List<Task> sortedTasks = strategy.sort(tasks);
```

### 6. **Adapter/Mapper Pattern**
**Purpose:** Data transformation between layers

**Implementation:**
```java
@Component
public class TaskMapper {
    
    public TaskDTO toDTO(Task task) {
        return TaskDTO.builder()
            .id(task.getId())
            .title(task.getTitle())
            .description(task.getDescription())
            .priority(task.getPriority())
            .status(task.getStatus())
            .dueDate(task.getDueDate())
            .build();
    }
    
    public Task toEntity(TaskDTO dto) {
        Task task = new Task();
        task.setTitle(dto.getTitle());
        task.setDescription(dto.getDescription());
        task.setPriority(dto.getPriority());
        task.setStatus(dto.getStatus());
        task.setDueDate(dto.getDueDate());
        return task;
    }
}
```

### 7. **Singleton Pattern**
**Purpose:** Single instance throughout application

**Implementation:**
```java
@Configuration
public class AppConfig {
    
    @Bean
    @Scope("singleton")
    public TaskService taskService(TaskRepository repository) {
        return new TaskService(repository);
    }
}
```

### 8. **Observer Pattern** (Event-Driven)
**Purpose:** Event handling dan notifications

**Implementation:**
```java
@Component
@EventListener
public class TaskEventListener {
    
    @EventListener
    public void onTaskCreated(TaskCreatedEvent event) {
        // Send notification
        notificationService.sendNotification(
            event.getTask().getUserId(), 
            "Task created successfully"
        );
    }
    
    @EventListener
    public void onTaskCompleted(TaskCompletedEvent event) {
        // Log completion
        logger.info("Task {} completed", event.getTask().getId());
    }
}
```

---

## ⚙️ Configuration

### Application Properties

**Production Configuration:** `application-prod.properties`
```properties
server.port=8080
spring.datasource.url=jdbc:postgresql://prod-db.example.com:5432/tododb
spring.jpa.hibernate.ddl-auto=validate
logging.level.root=WARN
app.jwtExpirationInMs=3600000
```

**Development Configuration:** `application-dev.properties`
```properties
server.port=8080
spring.datasource.url=jdbc:postgresql://localhost:5432/tododb
spring.jpa.hibernate.ddl-auto=update
logging.level.root=DEBUG
logging.level.com.example.TodoApp=DEBUG
app.jwtExpirationInMs=86400000
```

### Run dengan Profile Tertentu

```bash
# Development
java -jar target/TodoApp-0.0.1-SNAPSHOT.jar --spring.profiles.active=dev

# Production
java -jar target/TodoApp-0.0.1-SNAPSHOT.jar --spring.profiles.active=prod

# Via Maven
mvn spring-boot:run -Dspring-boot.run.arguments="--spring.profiles.active=dev"
```

---

## 🐳 Docker Deployment

### Build Docker Image

**Dockerfile:**
```dockerfile
FROM openjdk:21-slim

ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "/app.jar"]
```

**Build & Run:**
```bash
# Build image
docker build -t todoapp-backend:1.0 .

# Run container
docker run -d \
  --name todoapp-backend \
  -p 8080:8080 \
  -e SPRING_DATASOURCE_URL=jdbc:postgresql://db:5432/tododb \
  -e SPRING_DATASOURCE_USERNAME=todoapp \
  -e SPRING_DATASOURCE_PASSWORD=todoapp123 \
  todoapp-backend:1.0

# View logs
docker logs -f todoapp-backend
```

### Docker Compose Setup

**docker-compose.yml:**
```yaml
version: '3.8'

services:
  database:
    image: postgres:15-alpine
    container_name: todoapp-postgres
    environment:
      POSTGRES_DB: tododb
      POSTGRES_USER: todoapp
      POSTGRES_PASSWORD: todoapp123
    volumes:
      - postgres_data:/var/lib/postgresql/data
    ports:
      - "5432:5432"
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U todoapp"]
      interval: 10s
      timeout: 5s
      retries: 5

  backend:
    image: todoapp-backend:1.0
    container_name: todoapp-backend
    depends_on:
      database:
        condition: service_healthy
    environment:
      SPRING_DATASOURCE_URL: jdbc:postgresql://database:5432/tododb
      SPRING_DATASOURCE_USERNAME: todoapp
      SPRING_DATASOURCE_PASSWORD: todoapp123
      SPRING_JPA_HIBERNATE_DDL_AUTO: update
      APP_JWT_SECRET: ${JWT_SECRET}
    ports:
      - "8080:8080"
    volumes:
      - ./logs:/app/logs

volumes:
  postgres_data:

networks:
  default:
    name: todoapp-network
```

**Usage:**
```bash
# Start services
docker-compose up -d

# View status
docker-compose ps

# Stop services
docker-compose down

# View logs
docker-compose logs -f backend
```

---

## 🐛 Troubleshooting

### Backend Issues

#### Problem: "Connection refused" saat connect ke database

**Solution:**
```bash
# Check PostgreSQL status
sudo service postgresql status

# Verify connection
psql -U todoapp -h localhost -d tododb

# Check Spring logs
tail -f target/logs/spring.log | grep -i "connection\|error"
```

#### Problem: JWT token expired

**Solution:**
```java
// Increase token expiration in application.properties
app.jwtExpirationInMs=604800000  # 7 days

// Or use refresh token
POST /api/auth/refresh
```

#### Problem: "403 Forbidden" error

**Solution:**
```java
// Check CORS configuration
@Configuration
public class WebConfig implements WebMvcConfigurer {
    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/api/**")
            .allowedOrigins("http://localhost:3000")
            .allowedMethods("GET", "POST", "PUT", "DELETE", "PATCH")
            .allowCredentials(true);
    }
}
```

### Frontend Issues

#### Problem: "Connection timeout" saat call API

**Solution:**
```kotlin
// Check API endpoint configuration
object ApiConfig {
    const val BASE_URL = "http://10.0.2.2:8080/api/"  // For emulator
    const val CONNECTION_TIMEOUT = 60L
    const val READ_TIMEOUT = 60L
}
```

#### Problem: Gradle sync failed

**Solution:**
```bash
# Clear cache dan sync ulang
./gradlew clean
./gradlew --refresh-dependencies sync

# Or via Android Studio
File → Sync Now
```

#### Problem: "Cannot connect to localhost:8080" dari emulator

**Solution:**
```bash
# Gunakan IP yang benar untuk emulator
# 10.0.2.2 = localhost dari emulator's perspective

# Atau test dengan physical device:
adb devices  # List connected devices
adb reverse tcp:8080 tcp:8080  # Port forwarding
```

---

## 🚀 Performance Optimization

### Backend Optimization

```java
// 1. Database Query Optimization
@Entity
@Table(name = "tasks", indexes = {
    @Index(name = "idx_user_id", columnList = "user_id"),
    @Index(name = "idx_status", columnList = "status")
})
public class Task { }

// 2. Caching
@Configuration
@EnableCaching
public class CacheConfig { }

@Service
public class TaskService {
    @Cacheable(value = "tasks", key = "#userId")
    public List<Task> getUserTasks(UUID userId) {
        return taskRepository.findByUserId(userId);
    }
}

// 3. Lazy Loading
@Entity
public class User {
    @OneToMany(fetch = FetchType.LAZY)
    private List<Task> tasks;
}

// 4. Pagination
Page<Task> page = taskRepository.findByUserId(userId, PageRequest.of(0, 20));
```

### Frontend Optimization

```kotlin
// 1. Coroutines untuk async operations
lifecycleScope.launch {
    val tasks = viewModel.fetchTasks()
}

// 2. View recycling
RecyclerView.Adapter<TaskViewHolder>()

// 3. Image loading library
Glide.with(context).load(imageUrl).into(imageView)

// 4. Pagination
val pagingData = viewModel.getTasksPaging()
```

---

## 📚 Learning Resources

### Official Documentation
- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Android Developers Guide](https://developer.android.com)
- [Kotlin Official Documentation](https://kotlinlang.org/docs)
- [PostgreSQL Documentation](https://www.postgresql.org/docs)

### Architecture & Design Patterns
- [Clean Architecture by Robert C. Martin](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
- [SOLID Principles](https://en.wikipedia.org/wiki/SOLID)
- [Design Patterns Gang of Four](https://en.wikipedia.org/wiki/Design_Patterns)

### Spring Boot Resources
- [Spring Security Tutorial](https://spring.io/guides/gs/securing-web/)
- [Spring Data JPA](https://spring.io/projects/spring-data-jpa)
- [Building REST APIs](https://spring.io/guides/gs/rest-service/)

### Android & Kotlin
- [Kotlin Coroutines](https://kotlinlang.org/docs/coroutines-overview.html)
- [Android Architecture Components](https://developer.android.com/jetpack/androidx)
- [MVVM Architecture Pattern](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel)

---

## 👥 Contributing

### Code of Conduct
Kami percaya pada kolaborasi yang hormat dan inklusif. Silakan:
- ✅ Lapor bugs dengan detail
- ✅ Usulkan fitur baru dengan jelas
- ✅ Bantu improve dokumentasi
- ✅ Share best practices

### Steps untuk Contribute

1. **Fork Repository**
   ```bash
   git clone https://github.com/your-username/ToDoApp.git
   cd ToDoApp
   ```

2. **Create Feature Branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```

3. **Make Your Changes**
   - Follow code style guidelines
   - Add/update tests
   - Update documentation

4. **Commit dengan Message Deskriptif**
   ```bash
   git commit -m 'Add amazing feature: description'
   ```

5. **Push ke Branch**
   ```bash
   git push origin feature/amazing-feature
   ```

6. **Open Pull Request**
   - Deskripsi perubahan
   - Link issue related
   - Screenshot jika UI changes

### Coding Guidelines

**Java/Kotlin:**
- Follow Google Java Style Guide
- Use meaningful variable names
- Add JavaDoc untuk public methods
- Write unit tests untuk logic baru

**SQL:**
- Use meaningful table/column names
- Add proper constraints
- Document schema changes

**Git:**
- Atomic commits
- Clear commit messages
- Descriptive branch names

---

<div align="center">

**Made by Ceritanya Setim**

**1. Gabriella Agatha Uktolseja**
**2. Rachel Dhia Maharani**
**3. Maulana Hanif Al Faqih Rojichan**
**4. Hilyatul Aulia**
**5. Harry Siloam Sidabalok**
**6. Muhamad Nabhan Fadhlurrohman**

[⬆ kembali ke atas](#tabel-of-contents)

</div>
