# Healthcare System - Sample Data Documentation

## Overview
This document describes the comprehensive sample dataset that is automatically initialized when the application starts with an empty database.

## Data Initialization Summary

The `DataInitializer` class automatically creates sample data for all database schemas/collections in the system.

---

## 1. Users Collection

### Admin Users
- **Email**: admin@healthcare.com
- **Password**: admin123
- **Role**: ADMIN
- **Name**: Healthcare Manager
- **Gender**: Male
- **Contact**: 0771234567

### Staff Users
- **Email**: staff@healthcare.com
- **Password**: staff123
- **Role**: STAFF
- **Name**: Reception Staff
- **Gender**: Female
- **Contact**: 0774567890

### Doctor Users (8 doctors with different specializations)

| Name | Email | Password | Specialization | Gender | Contact |
|------|-------|----------|----------------|--------|---------|
| Dr. John Smith | doctor1@healthcare.com | doctor123 | Cardiology | Male | 0772345678 |
| Dr. Sarah Johnson | doctor2@healthcare.com | doctor123 | Pediatrics | Female | 0773456789 |
| Dr. Michael Chen | doctor3@healthcare.com | doctor123 | Dermatology | Male | 0774567890 |
| Dr. Emily Rodriguez | doctor4@healthcare.com | doctor123 | Orthopedics | Female | 0775678901 |
| Dr. David Kumar | doctor5@healthcare.com | doctor123 | Neurology | Male | 0776789012 |
| Dr. Priya Patel | doctor6@healthcare.com | doctor123 | General Medicine | Female | 0777890123 |
| Dr. Robert Williams | doctor7@healthcare.com | doctor123 | Oncology | Male | 0778901234 |
| Dr. Lisa Anderson | doctor8@healthcare.com | doctor123 | Psychiatry | Female | 0779012345 |

### Patient Users (2 sample patients)

| Name | Email | Password | Gender | Date of Birth | Contact | Address |
|------|-------|----------|--------|---------------|---------|---------|
| Alice Perera | alice@example.com | patient123 | Female | 1990-04-12 | 0771112223 | 12 Flower Road, Colombo |
| Bimal Fernando | bimal@example.com | patient123 | Male | 1985-09-03 | 0772223334 | 34 Lake View, Kandy |

---

## 2. Hospitals Collection

### Hospital 1: City Medical Center (Private)
- **Type**: PRIVATE
- **Hospital Charges**: Rs. 5,000.00
- **Location**: 
  - Address: 123 Main Street
  - City: Colombo
  - State: Western Province
- **Contact**:
  - Phone: 0112345678
  - Email: info@citymedical.lk
  - Website: www.citymedical.lk
- **Doctors**: 
  - Dr. John Smith (Cardiology)
  - Dr. Michael Chen (Dermatology)
  - Dr. Emily Rodriguez (Orthopedics)

### Hospital 2: General Hospital (Government)
- **Type**: GOVERNMENT
- **Hospital Charges**: Rs. 0.00
- **Location**: 
  - Address: 456 Hospital Road
  - City: Kandy
  - State: Central Province
- **Contact**:
  - Phone: 0812345678
  - Email: info@generalhospital.gov.lk
  - Website: www.generalhospital.gov.lk
- **Doctors**: 
  - Dr. Sarah Johnson (Pediatrics)
  - Dr. David Kumar (Neurology)
  - Dr. Priya Patel (General Medicine)

### Hospital 3: National Hospital (Government)
- **Type**: GOVERNMENT
- **Hospital Charges**: Rs. 0.00
- **Location**: 
  - Address: 789 Regent Street
  - City: Colombo
  - State: Western Province
- **Contact**:
  - Phone: 0114567890
  - Email: info@nationalhospital.gov.lk
  - Website: www.nationalhospital.gov.lk
- **Doctors**: 
  - Dr. Robert Williams (Oncology)
  - Dr. Lisa Anderson (Psychiatry)

---

## 3. Appointments Collection

### Sample Appointments Created
- **2 appointments** for the sample patients
- Appointments scheduled with different doctors
- **Status**: SCHEDULED
- Various appointment dates and times in the future

**Example:**
- Patient: Alice Perera
- Doctor: Dr. John Smith
- Date/Time: 3 days from initialization at 10:00 AM
- Purpose: General consultation
- Status: SCHEDULED

---

## 4. Medical Records Collection

### Medical Records Overview
- **Multiple records** created for each patient (2-3 records per patient)
- Records distributed across different doctors and specializations
- Each record includes:
  - Diagnosis specific to doctor's specialization
  - Detailed prescription
  - Clinical notes and follow-up instructions
  - Record date (backdated to show history)

### Sample Record by Specialization

#### Cardiology
- **Diagnosis**: Hypertension - Stage 1
- **Prescription**: Lisinopril 10mg (Once daily), Aspirin 81mg (Once daily)
- **Notes**: Monitor blood pressure daily, follow-up in 3 months, lifestyle changes recommended

#### Pediatrics
- **Diagnosis**: Common Cold with mild fever
- **Prescription**: Paracetamol 250mg (Every 6 hours), Vitamin C supplements
- **Notes**: Keep hydrated, rest advised, return if symptoms persist beyond 7 days

#### Dermatology
- **Diagnosis**: Atopic Dermatitis (Eczema)
- **Prescription**: Hydrocortisone cream 1% (twice daily), Moisturizer
- **Notes**: Avoid allergens, use fragrance-free products, follow-up in 2 weeks

#### Orthopedics
- **Diagnosis**: Lower back pain - Muscle strain
- **Prescription**: Ibuprofen 400mg (three times daily), Physical therapy
- **Notes**: Apply heat/ice, avoid heavy lifting, core strengthening exercises

#### Neurology
- **Diagnosis**: Tension-type headache
- **Prescription**: Paracetamol 500mg (as needed), Relaxation techniques
- **Notes**: Stress management, regular sleep schedule, follow-up if headaches increase

#### General Medicine
- **Diagnosis**: Annual Health Checkup - All parameters normal
- **Prescription**: Multivitamin supplements (once daily)
- **Notes**: Patient in good health, continue exercise and balanced diet, next checkup in 12 months

#### Oncology
- **Diagnosis**: Routine cancer screening - No abnormalities detected
- **Prescription**: No medication required
- **Notes**: All screening tests normal, continue healthy lifestyle, next screening in 12 months

#### Psychiatry
- **Diagnosis**: Mild anxiety disorder
- **Prescription**: Sertraline 50mg (once daily), Cognitive Behavioral Therapy sessions
- **Notes**: Patient responding well, continue weekly therapy, review medication in 6 weeks

---

## 5. Payments Collection

### Payment Records
- **Multiple payment records** created for appointments and consultations
- Variety of payment methods and statuses

### Payment Types:

#### Card Payments
- Payment Method: CARD
- Transaction ID: Generated unique IDs
- Status: COMPLETED or PENDING
- Amount: Varies by hospital type and consultation

#### Insurance Payments
- Payment Method: INSURANCE
- Insurance Provider: National Insurance Company
- Policy Number: POL-100000 series
- Status: COMPLETED or PENDING

#### Cash Payments
- Payment Method: CASH
- Status: COMPLETED
- No transaction ID required

### Payment Amounts:
- **Government Hospitals**: Rs. 500.00 (nominal fee)
- **Private Hospitals**: Rs. 7,000.00 (Rs. 5,000 hospital charge + Rs. 2,000 consultation)
- **Standalone Consultations**: Rs. 1,500.00

---

## 6. Health Cards Collection

### Health Card Features
- **One health card per patient**
- Contains QR code (base64 encoded image)
- Card validity: 1 year from creation date
- **Status**: Either ACTIVE or INACTIVE

### Sample Health Card:
- Patient ID: Linked to patient
- Patient Name: Full name
- QR Code: Base64 encoded image for identification
- Create Date: 6+ months ago (backdated)
- Expire Date: 1 year from creation
- Status: ACTIVE (75% cards) or INACTIVE (25% cards)

---

## 7. Time Slot Reservations Collection

### Reservation Types Created:

#### Active Reservations (3)
- **Status**: ACTIVE
- **Purpose**: Ongoing booking process (within 5-minute window)
- Reserved for future appointments (2-4 days ahead)
- Session ID tracked for user verification

#### Confirmed Reservations (4)
- **Status**: CONFIRMED
- **Purpose**: Successfully booked appointments
- Slots confirmed and locked for appointments
- Created 6+ hours ago

#### Expired Reservations (2)
- **Status**: EXPIRED
- **Purpose**: User didn't complete booking within 5 minutes
- Slots released back to availability
- Created 10+ minutes ago

#### Cancelled Reservations (1)
- **Status**: CANCELLED
- **Purpose**: User cancelled before confirming
- Slot released for other patients
- Created 1 hour ago

### Time Slot Details:
- Linked to specific doctors and patients
- Scheduled at various times (9:00 AM, 2:30 PM, 4:00 PM, etc.)
- Session ID for tracking user sessions
- Creation timestamps for expiry management

---

## 8. Analytics Reports Collection

### Note:
Analytics reports are **not pre-populated** during initialization. They are generated on-demand by administrators through the analytics service based on the current data in the system.

The analytics service can generate various types of reports:
- Patient Summary Reports
- Doctor Performance Reports
- Hospital Overview Reports
- Appointment Statistics Reports
- Medical Records Summary Reports
- System Overview Reports

---

## Database Collections Summary

| Collection | Records Created | Key Features |
|------------|----------------|--------------|
| **users** | 11 | 1 Admin, 1 Staff, 8 Doctors, 2 Patients |
| **hospitals** | 3 | 1 Private, 2 Government hospitals |
| **appointments** | 2+ | Scheduled appointments |
| **medical_records** | 15+ | 2-3 records per patient across specializations |
| **payments** | 8+ | Mix of card, insurance, and cash payments |
| **health_cards** | 2+ | One card per patient |
| **time_slot_reservations** | 10 | Active, confirmed, expired, and cancelled slots |
| **analytics_reports** | 0 | Generated on-demand |

---

## How to Use Sample Data

### Login Credentials:

1. **Admin Access**:
   - Email: `admin@healthcare.com`
   - Password: `admin123`

2. **Staff Access**:
   - Email: `staff@healthcare.com`
   - Password: `staff123`

3. **Doctor Access** (any doctor 1-8):
   - Email: `doctor1@healthcare.com` (or doctor2, doctor3, etc.)
   - Password: `doctor123`

4. **Patient Access**:
   - Email: `alice@example.com` or `bimal@example.com`
   - Password: `patient123`

---

## Data Initialization Behavior

### First Run (Empty Database):
- All sample data is created automatically
- Comprehensive dataset covering all schemas
- Ready to use immediately after startup

### Subsequent Runs (Existing Data):
- Skips initialization if data already exists
- Checks for missing medical records and creates them if needed
- Prevents duplicate data creation

### Manual Data Reset:
If you need to reset the database:
1. Clear all collections in MongoDB
2. Restart the application
3. Sample data will be recreated automatically

---

## Technical Notes

### MongoDB ObjectIds:
- All references use MongoDB-generated ObjectIds
- Proper referencing between collections
- DBRef used for lazy-loaded relationships

### Data Relationships:
- Doctors → Hospitals (hospitalId)
- Patients → Hospitals (hospitalId)
- Appointments → Doctors + Patients
- Medical Records → Doctors + Patients
- Payments → Appointments + Hospitals + Doctors + Patients
- Health Cards → Patients
- Time Slot Reservations → Doctors + Patients

### Timestamps:
- All records include `createdAt` and `updatedAt` timestamps
- Backdated entries for realistic historical data
- Future-dated entries for appointments and reservations

---

## Example Queries

### Find all doctors at a specific hospital:
```java
doctorRepository.findByHospitalId(hospitalId);
```

### Find all appointments for a patient:
```java
appointmentRepository.findByPatientId(patientId);
```

### Find all medical records for a patient:
```java
medicalRecordRepository.findByPatientId(patientId);
```

### Find all active reservations:
```java
timeSlotReservationRepository.findByStatus(TimeSlotReservation.ReservationStatus.ACTIVE);
```

---

## Logging

During initialization, the system provides detailed logs:

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

---

## Support

For any issues with data initialization:
1. Check application logs for error messages
2. Verify MongoDB connection in application.properties
3. Ensure all required dependencies are installed
4. Clear database and restart for fresh initialization

---

**Last Updated**: October 17, 2025
**Version**: 1.0.0
**System**: Smart Healthcare System for Urban Hospitals in Sri Lanka

