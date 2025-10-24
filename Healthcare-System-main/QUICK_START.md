# 🚀 Quick Start Guide - Healthcare System

## ✅ What's Ready

Your Healthcare System now has **complete sample data** for all database schemas!

---

## 🎯 Get Started in 3 Steps

### Step 1: Start MongoDB
Ensure your MongoDB is running and accessible via the connection string in your `.env` file.

### Step 2: Run the Application
```bash
# Windows
.\mvnw.cmd spring-boot:run

# Linux/Mac
./mvnw spring-boot:run
```

### Step 3: Login and Explore
Use any of these credentials to access the system:

---

## 🔑 Login Credentials

### 👨‍💼 Admin Access
```
Email: admin@healthcare.com
Password: admin123
```
**What you can do**: Manage entire system, view analytics, manage users

### 👩‍⚕️ Doctor Access
```
Email: doctor1@healthcare.com (through doctor8)
Password: doctor123
```
**Specializations Available**:
- doctor1: Cardiology
- doctor2: Pediatrics  
- doctor3: Dermatology
- doctor4: Orthopedics
- doctor5: Neurology
- doctor6: General Medicine
- doctor7: Oncology
- doctor8: Psychiatry

### 👤 Patient Access
```
Email: alice@example.com
Password: patient123

OR

Email: bimal@example.com
Password: patient123
```
**What you can do**: Book appointments, view medical records, manage health cards

### 👥 Staff Access
```
Email: staff@healthcare.com
Password: staff123
```
**What you can do**: Manage appointments, scan health cards, reception tasks

---

## 📊 What Sample Data is Available?

### ✅ Complete Database Coverage

| Data Type | Count | Description |
|-----------|-------|-------------|
| 👥 Users | 11 | Admins, Doctors, Staff, Patients |
| 🏥 Hospitals | 3 | Private & Government hospitals |
| 📅 Appointments | 2+ | Scheduled appointments |
| 📋 Medical Records | 15+ | Across all specializations |
| 💳 Payments | 8+ | Card, Insurance, Cash |
| 🎫 Health Cards | 2+ | With QR codes |
| ⏰ Time Slots | 10 | Active, Confirmed, Expired |

---

## 🎨 Sample Hospitals

### City Medical Center (Private)
- **Location**: Colombo
- **Charges**: Rs. 5,000
- **Doctors**: Cardiology, Dermatology, Orthopedics

### General Hospital (Government)
- **Location**: Kandy  
- **Charges**: Rs. 0 (Free)
- **Doctors**: Pediatrics, Neurology, General Medicine

### National Hospital (Government)
- **Location**: Colombo
- **Charges**: Rs. 0 (Free)
- **Doctors**: Oncology, Psychiatry

---

## 📱 What Can You Test?

### As Patient:
✅ Book appointments with doctors  
✅ View medical records  
✅ Check health card  
✅ Make payments  
✅ View appointment history  

### As Doctor:
✅ View scheduled appointments  
✅ Create medical records  
✅ Update patient information  
✅ Manage availability  

### As Admin:
✅ View all data  
✅ Manage users  
✅ View analytics  
✅ Manage hospitals  

### As Staff:
✅ Scan health cards  
✅ Manage appointments  
✅ Reception duties  

---

## 🔍 Verify Data Import

Watch for these log messages when starting:

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

If you see all these ✅ checkmarks, you're good to go!

---

## 🆘 Quick Troubleshooting

### Problem: Application won't start
**Solution**: Check `.env` file has all required variables

### Problem: No data in database
**Solution**: Check MongoDB connection string is correct

### Problem: Can't login
**Solution**: Use exact credentials listed above (case-sensitive)

### Problem: Duplicate key errors
**Solution**: Database already has data. Either use existing data or clear collections.

---

## 📚 More Information

### Detailed Documentation:
- **SAMPLE_DATA_DOCUMENTATION.md** - Complete data breakdown
- **DATA_IMPORT_README.md** - Detailed usage guide
- **IMPLEMENTATION_SUMMARY.md** - Technical details

### Quick Commands:

```bash
# Start application
.\mvnw.cmd spring-boot:run

# Clean build
.\mvnw.cmd clean install

# Skip tests
.\mvnw.cmd clean install -DskipTests
```

---

## 🎯 Common Use Cases

### 1. Book an Appointment
1. Login as patient (alice@example.com / patient123)
2. Navigate to appointments
3. Select doctor and time slot
4. Complete booking

### 2. Create Medical Record
1. Login as doctor (doctor1@healthcare.com / doctor123)
2. View appointments
3. Select patient
4. Create medical record

### 3. Process Payment
1. Login as patient
2. View appointments
3. Select appointment
4. Choose payment method (Card/Insurance/Cash)

### 4. View Analytics
1. Login as admin (admin@healthcare.com / admin123)
2. Navigate to analytics
3. Generate reports

---

## ✨ What's New

### Recently Added Sample Data:

#### 💳 Payments
- Multiple payment methods
- Transaction tracking
- Insurance integration
- Various statuses

#### 🎫 Health Cards
- QR code identification
- Expiration management
- Active/Inactive statuses

#### ⏰ Time Slot Reservations
- Booking workflow
- 5-minute hold mechanism
- Status transitions

---

## 🎊 You're All Set!

Your Healthcare System is ready with:

✅ Complete sample data for all schemas  
✅ Multiple user accounts to test  
✅ Realistic hospital and doctor data  
✅ Payment and booking workflows  
✅ Health card system  
✅ Medical records across specializations  

**Just start the app and login!** 🚀

---

## 💡 Pro Tips

1. **Try different user roles** to see different features
2. **Inspect MongoDB** to understand data structure  
3. **Create new records** to test CRUD operations
4. **Check logs** to debug any issues
5. **Read documentation** for in-depth understanding

---

## 🎓 Learning Path

1. **Start with Patient role** - Book an appointment
2. **Switch to Doctor role** - View and manage appointments
3. **Try Staff role** - Reception workflow
4. **Use Admin role** - System overview and analytics

---

## 📞 Need Help?

1. Check application logs
2. Review documentation files
3. Verify `.env` configuration
4. Check MongoDB connection

---

**Quick Reference**: Keep this file handy for immediate access to login credentials!

**Version**: 1.0.0  
**Last Updated**: October 17, 2025  
**Status**: Ready to Use ✅

