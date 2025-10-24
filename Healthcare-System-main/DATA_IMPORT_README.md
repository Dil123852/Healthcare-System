# Healthcare System - Data Import & Initialization Guide

## 🎯 Overview

This Healthcare System automatically imports comprehensive example data covering **ALL database schemas** when the application starts with an empty database.

## ✅ What Has Been Implemented

### Enhanced Data Initializer (`DataInitializer.java`)

The `DataInitializer.java` configuration file has been enhanced to create sample data for **ALL 8 database collections**:

#### ✓ 1. Users Collection
- 1 Admin user
- 1 Staff member  
- 8 Doctors (various specializations)
- 2 Patients

#### ✓ 2. Hospitals Collection
- 1 Private hospital (City Medical Center)
- 2 Government hospitals (General Hospital, National Hospital)
- Complete location and contact information
- Doctors assigned to each hospital

#### ✓ 3. Appointments Collection
- Sample appointments for patients
- Various statuses (SCHEDULED, COMPLETED, CANCELLED, NO_SHOW)
- Linked to doctors and patients

#### ✓ 4. Medical Records Collection
- 15+ medical records
- 2-3 records per patient
- Diverse diagnoses matching doctor specializations
- Detailed prescriptions and clinical notes

#### ✓ 5. Payments Collection ⭐ **NEW**
- Multiple payment records (8+)
- Payment methods: CARD, INSURANCE, CASH
- Payment statuses: COMPLETED, PENDING, FAILED, REFUNDED
- Transaction IDs for card payments
- Insurance policy details
- Varied amounts based on hospital type

#### ✓ 6. Health Cards Collection ⭐ **NEW**
- One health card per patient
- QR codes for patient identification
- Active/Inactive statuses
- Card expiration dates
- Complete patient information

#### ✓ 7. Time Slot Reservations Collection ⭐ **NEW**
- 10 sample reservations
- Different statuses:
  - ACTIVE (3) - Ongoing booking process
  - CONFIRMED (4) - Successfully booked slots
  - EXPIRED (2) - Timed-out reservations
  - CANCELLED (1) - User-cancelled slot
- Linked to specific doctors and patients
- Session tracking for booking workflow

#### ⏳ 8. Analytics Reports Collection
- Generated on-demand by administrators
- Not pre-populated (created based on current data)

---

## 🚀 How to Use

### Starting the Application

1. **Ensure MongoDB is running** and accessible via the connection string in your `.env` file

2. **Start the Spring Boot application**:
   ```bash
   # Using Maven wrapper (Windows)
   .\mvnw.cmd spring-boot:run
   
   # Using Maven wrapper (Linux/Mac)
   ./mvnw spring-boot:run
   
   # Using Maven (if installed globally)
   mvn spring-boot:run
   ```

3. **Watch the initialization logs**:
   ```
   🚀 Initializing sample data...
   ✅ Admin user created
   ✅ Doctor 1-8 created
   ✅ Staff member created
   🏥 Creating sample hospitals...
      ✓ City Medical Center created with 3 doctors
      ✓ General Hospital created with 3 doctors
      ✓ National Hospital created with 2 doctors
   📋 Creating sample medical records...
      ✓ Created 15 medical records
   👥 Creating sample patients and appointments...
      ✓ Sample patients and appointments created
   💳 Creating sample payments...
      ✓ Created 8 payments
   🏥 Creating sample health cards...
      ✓ Created 2 health cards
   ⏰ Creating sample time slot reservations...
      ✓ Created 10 time slot reservations
   ✅ Data initialization completed!
   ```

### First Run (Empty Database)
- All sample data is automatically created
- Ready to use immediately
- No manual intervention required

### Subsequent Runs (Existing Data)
- Checks if data already exists
- Skips initialization to prevent duplicates
- Creates missing medical records if needed

---

## 👤 Login Credentials

### Admin Panel
```
Email: admin@healthcare.com
Password: admin123
Role: ADMIN
```

### Staff/Reception
```
Email: staff@healthcare.com
Password: staff123
Role: STAFF
```

### Doctors (8 available)
```
Email: doctor1@healthcare.com (through doctor8@healthcare.com)
Password: doctor123
Role: DOCTOR

Specializations:
- doctor1: Cardiology
- doctor2: Pediatrics
- doctor3: Dermatology
- doctor4: Orthopedics
- doctor5: Neurology
- doctor6: General Medicine
- doctor7: Oncology
- doctor8: Psychiatry
```

### Patients
```
Patient 1:
  Email: alice@example.com
  Password: patient123
  Name: Alice Perera

Patient 2:
  Email: bimal@example.com
  Password: patient123
  Name: Bimal Fernando
```

---

## 📊 Sample Data Details

### Hospitals

| Hospital | Type | Charges | City | Doctors |
|----------|------|---------|------|---------|
| City Medical Center | PRIVATE | Rs. 5,000 | Colombo | 3 (Cardiology, Dermatology, Orthopedics) |
| General Hospital | GOVERNMENT | Rs. 0 | Kandy | 3 (Pediatrics, Neurology, General Medicine) |
| National Hospital | GOVERNMENT | Rs. 0 | Colombo | 2 (Oncology, Psychiatry) |

### Payments

**Sample Payment Breakdown:**
- **Government Hospital Appointments**: Rs. 500 (nominal fee)
- **Private Hospital Appointments**: Rs. 7,000 (Rs. 5,000 hospital + Rs. 2,000 consultation)
- **Standalone Consultations**: Rs. 1,500

**Payment Methods Distribution:**
- Card payments with transaction IDs
- Insurance payments with policy numbers
- Cash payments (no additional details)

**Payment Statuses:**
- COMPLETED: Successfully processed payments
- PENDING: Awaiting payment completion
- FAILED: Failed transactions (sample data)
- REFUNDED: Refunded transactions (sample data)

### Health Cards

Each patient has a health card with:
- Unique QR code for identification
- Patient details (name, ID)
- Card status (ACTIVE/INACTIVE)
- Creation date (backdated 6+ months)
- Expiration date (1 year from creation)

**Card Status Distribution:**
- 75% ACTIVE
- 25% INACTIVE

### Time Slot Reservations

**Reservation Flow:**
1. **ACTIVE**: Patient is in booking process (5-minute window)
2. **CONFIRMED**: Patient completed booking
3. **EXPIRED**: 5 minutes passed without confirmation
4. **CANCELLED**: Patient cancelled before confirming

**Sample Reservations:**
- 3 Active (currently being booked)
- 4 Confirmed (successfully booked)
- 2 Expired (timed out)
- 1 Cancelled (user cancelled)

### Medical Records

Records cover all medical specializations:
- **Cardiology**: Hypertension management
- **Pediatrics**: Common cold treatment
- **Dermatology**: Eczema care
- **Orthopedics**: Back pain treatment
- **Neurology**: Headache management
- **General Medicine**: Annual checkups
- **Oncology**: Cancer screenings
- **Psychiatry**: Anxiety disorder treatment

Each record includes:
- Diagnosis
- Detailed prescription
- Clinical notes
- Follow-up instructions

---

## 🔧 Database Configuration

### Required Environment Variables (.env file)

```properties
# MongoDB Configuration
MONGO_DATABASE=healthcare_db
MONGO_USER=your_username
MONGO_PASS=your_password
MONGO_CLUSTER=your_cluster.mongodb.net

# Email Configuration
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=your_email@gmail.com
MAIL_PASS=your_app_password

# Application Configuration
BASE_URL=http://localhost:8080
PORT=8080

# Stripe Configuration (for payment processing)
STRIPE_SECRET_KEY=your_stripe_secret_key
```

---

## 🔄 Resetting the Database

If you want to reset and recreate all sample data:

### Option 1: Clear MongoDB Collections
```javascript
// In MongoDB shell or Compass
use healthcare_db

db.users.deleteMany({})
db.hospitals.deleteMany({})
db.appointments.deleteMany({})
db.medical_records.deleteMany({})
db.payments.deleteMany({})
db.health_cards.deleteMany({})
db.time_slot_reservations.deleteMany({})
db.analytics_reports.deleteMany({})
```

Then restart the application. Sample data will be recreated automatically.

### Option 2: Use a Fresh Database
1. Change `MONGO_DATABASE` in your `.env` file
2. Restart the application
3. New database will be created with all sample data

---

## 📝 Testing the Data

### Verify Data Import

You can verify the data was imported successfully by:

1. **Check Application Logs**: Look for success messages during startup

2. **MongoDB Compass**: Connect and view collections

3. **API Endpoints** (if available):
   ```bash
   # Get all doctors
   GET http://localhost:8080/api/doctors
   
   # Get all hospitals
   GET http://localhost:8080/api/hospitals
   
   # Get appointments for a patient
   GET http://localhost:8080/api/appointments?patientId=<id>
   ```

4. **Login to the Application**: Use any of the provided credentials

### Sample Queries

**Find all doctors at City Medical Center:**
```java
List<Doctor> doctors = doctorRepository.findByHospitalId(cityMedicalCenterId);
```

**Find all payments for a patient:**
```java
List<Payment> payments = paymentRepository.findByPatientId(patientId);
```

**Find active time slot reservations:**
```java
List<TimeSlotReservation> activeReservations = 
    timeSlotReservationRepository.findByStatus(ReservationStatus.ACTIVE);
```

**Find all health cards expiring soon:**
```java
LocalDate oneMonthFromNow = LocalDate.now().plusMonths(1);
List<HealthCard> expiringCards = 
    healthCardRepository.findByExpireDateBefore(oneMonthFromNow);
```

---

## 📋 Database Schema Coverage

✅ **All 8 Collections Covered:**

| Collection | Sample Records | Status |
|------------|----------------|--------|
| users | 11 | ✅ Complete |
| hospitals | 3 | ✅ Complete |
| appointments | 2+ | ✅ Complete |
| medical_records | 15+ | ✅ Complete |
| payments | 8+ | ✅ **NEW** |
| health_cards | 2+ | ✅ **NEW** |
| time_slot_reservations | 10 | ✅ **NEW** |
| analytics_reports | 0 (on-demand) | ✅ Complete |

---

## 🎨 Features Demonstrated

The sample data demonstrates:

✅ User role management (ADMIN, STAFF, DOCTOR, PATIENT)
✅ Hospital types (GOVERNMENT vs PRIVATE)
✅ Hospital charges and pricing
✅ Doctor-Hospital relationships
✅ Patient-Hospital registration
✅ Appointment booking and management
✅ Medical record keeping across specializations
✅ Payment processing (multiple methods)
✅ Health card issuance and management
✅ Time slot reservation system
✅ Complex relationships between entities
✅ Realistic timestamps and historical data
✅ Various status transitions

---

## 🐛 Troubleshooting

### Issue: Data not being created

**Solution:**
1. Check MongoDB connection in `.env` file
2. Verify database is accessible
3. Check application logs for errors
4. Ensure database is truly empty

### Issue: Duplicate key errors

**Solution:**
- Data already exists in database
- Clear the database or use a fresh one
- Check for unique email constraints

### Issue: Missing repositories

**Solution:**
- Ensure all repository interfaces are defined
- Check imports in `DataInitializer.java`
- Verify Spring Data MongoDB dependencies

### Issue: Compilation errors

**Solution:**
```bash
# Clean and rebuild
./mvnw clean install

# Skip tests if needed
./mvnw clean install -DskipTests
```

---

## 📚 Additional Documentation

- **SAMPLE_DATA_DOCUMENTATION.md**: Detailed breakdown of all sample data
- **pom.xml**: Project dependencies
- **application.properties**: Application configuration

---

## 🎯 Next Steps

After successful data import:

1. **Login** with provided credentials
2. **Explore** the application features
3. **Test** appointment booking
4. **Review** medical records
5. **Process** sample payments
6. **View** health cards
7. **Manage** time slot reservations
8. **Generate** analytics reports (as admin)

---

## 💡 Tips

- **Use different user roles** to see different perspectives
- **Inspect MongoDB** to understand data structure
- **Create new records** to test CRUD operations
- **Modify sample data** in `DataInitializer.java` as needed
- **Backup database** before making major changes

---

## ✨ What's New in This Update

### Added Comprehensive Sample Data:

1. **Payments Collection** 💳
   - Multiple payment records
   - All payment methods (CARD, INSURANCE, CASH)
   - Various payment statuses
   - Transaction tracking

2. **Health Cards Collection** 🏥
   - Patient identification cards
   - QR code support
   - Card expiration management
   - Active/Inactive statuses

3. **Time Slot Reservations Collection** ⏰
   - Booking workflow support
   - 5-minute reservation window
   - Status transitions
   - Session tracking

---

## 📞 Support

For issues or questions:
1. Check application logs
2. Review MongoDB connection
3. Verify environment variables
4. Consult the documentation files

---

**Version**: 1.0.0  
**Last Updated**: October 17, 2025  
**Project**: Smart Healthcare System for Urban Hospitals in Sri Lanka

