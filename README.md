## Smart Healthcare System (Spring Boot + MongoDB)

A full-stack healthcare management system built with Spring Boot 3, MongoDB, Thymeleaf, and Stripe. It supports patient appointments, payments, medical records, insurance workflows, staff tools, and email notifications.

### Features
- **User management & auth**: Registration, login, profiles
- **Appointments**: Booking, selection of doctor/time slot, cancellation, confirmations
- **Payments**: Card payments with Stripe; success/receipt flows
- **Insurance**: Request handling and pending collections
- **Medical records**: Viewing, PDF generation (iText), and QR code support (ZXing)
- **Staff tools**: Scanner view for staff operations
- **Email notifications**: Via Spring Mail
- **Server-rendered UI**: Thymeleaf templates for pages and flows

### Tech Stack
- **Language**: Java 17
- **Framework**: Spring Boot 3.5.6
- **Database**: MongoDB (Spring Data MongoDB)
- **View Layer**: Thymeleaf
- **Payments**: Stripe Java SDK
- **PDF/QR**: iText 7, ZXing
- **Env config**: spring-dotenv

### Project Structure
```
Healthcare-System-main/
├─ pom.xml
├─ mvnw, mvnw.cmd
├─ src/
│  ├─ main/
│  │  ├─ java/com/example/health_care_system/... (controllers, services, models, etc.)
│  │  └─ resources/
│  │     ├─ application.properties
│  │     └─ templates/ (Thymeleaf views: appointments, login, dashboard, etc.)
│  └─ test/...
├─ QUICK_START.md
├─ MONGODB_SETUP_GUIDE.md
├─ DATA_IMPORT_README.md
├─ SAMPLE_DATA_DOCUMENTATION.md
├─ IMPLEMENTATION_SUMMARY.md
├─ PAYMENT_TEST_CASES_SUMMARY.md
└─ TEST_MONGODB_CONNECTION.md
```

### Prerequisites
- Java 17
- MongoDB running locally or a connection URI
- Maven (or use the included Maven Wrapper `mvnw`/`mvnw.cmd`)

### Configuration
Most runtime configuration is handled via `application.properties` and environment variables (dotenv supported).

Common variables you may need to set (env or `.env`):
```
SPRING_DATA_MONGODB_URI=mongodb://localhost:27017/healthcare
STRIPE_API_KEY=sk_test_xxx
SPRING_MAIL_HOST=smtp.example.com
SPRING_MAIL_PORT=587
SPRING_MAIL_USERNAME=you@example.com
SPRING_MAIL_PASSWORD=your_password
```

See:
- `MONGODB_SETUP_GUIDE.md` for MongoDB configuration
- `TEST_MONGODB_CONNECTION.md` to verify database connectivity

### Quick Start (Dev)
Using Maven Wrapper (recommended on Windows PowerShell/CMD from project root):
```
./mvnw spring-boot:run
```
On Windows CMD you can also use:
```
mvnw.cmd spring-boot:run
```

The app will start on `http://localhost:8080` by default.

### Build
```
./mvnw clean package
```
The runnable JAR will be in `target/` (e.g., `health-care-system-0.0.1-SNAPSHOT.jar`).

### Run Packaged JAR
```
java -jar target/health-care-system-0.0.1-SNAPSHOT.jar
```

### Tests
```
./mvnw test
```

### Documentation and Guides
- Quick start guide: `QUICK_START.md`
- MongoDB setup: `MONGODB_SETUP_GUIDE.md`
- Sample/import data: `DATA_IMPORT_README.md`, `SAMPLE_DATA_DOCUMENTATION.md`
- Implementation notes: `IMPLEMENTATION_SUMMARY.md`
- Changes log: `CHANGES_SUMMARY.txt`
- Payment tests: `PAYMENT_TEST_CASES_SUMMARY.md`

### Notes
- Ensure your MongoDB instance is reachable and the database/collections are created per the setup guides.
- Set your Stripe secret key before testing payments.
- Email features require valid SMTP credentials.

### License
This project’s license has not been explicitly specified in the repository. Add a LICENSE file if you intend to open-source it.


