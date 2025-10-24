# 🔧 MongoDB Connection Setup Guide

## ⚠️ Issue: No Sample Data in Database

**Problem**: The `.env` file is missing, so the application cannot connect to MongoDB.

**Solution**: Create a `.env` file with your MongoDB credentials.

---

## 📝 Step 1: Create `.env` File

Create a new file named `.env` in the root directory of your project:
```
F:\Y3S1\Healthcare-System\.env
```

---

## 📋 Step 2: Add MongoDB Configuration

Copy this content into your `.env` file and **replace with your actual credentials**:

```properties
# MongoDB Configuration
# Replace these values with your actual MongoDB credentials
MONGO_DATABASE=healthcare_db
MONGO_USER=your_mongodb_username
MONGO_PASS=your_mongodb_password
MONGO_CLUSTER=your_cluster.mongodb.net

# Email Configuration (Optional - for email notifications)
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=your_email@gmail.com
MAIL_PASS=your_email_app_password

# Application Configuration
BASE_URL=http://localhost:8080
PORT=8080

# Stripe Configuration (Optional - for payment processing)
STRIPE_SECRET_KEY=
```

---

## 🔑 Step 3: Get Your MongoDB Credentials

### If using MongoDB Atlas (Cloud):

1. **Go to** [MongoDB Atlas](https://cloud.mongodb.com/)
2. **Login** to your account
3. **Select your cluster**
4. **Click "Connect"** button
5. **Choose "Connect your application"**
6. **Copy the connection string**

**Connection String Format:**
```
mongodb+srv://<username>:<password>@<cluster>.mongodb.net/<database>
```

**Extract the values:**
- **MONGO_USER**: Your MongoDB username (e.g., `admin`, `user123`)
- **MONGO_PASS**: Your MongoDB password
- **MONGO_CLUSTER**: Cluster address (e.g., `cluster0.abc123.mongodb.net`)
- **MONGO_DATABASE**: Database name (e.g., `healthcare_db`)

### If using Local MongoDB:

```properties
# For local MongoDB
MONGO_DATABASE=healthcare_db
MONGO_USER=
MONGO_PASS=
# Change the URI in application.properties to:
# spring.data.mongodb.uri=mongodb://localhost:27017/healthcare_db
```

---

## 📝 Step 4: Example Configuration

### Example 1: MongoDB Atlas
```properties
MONGO_DATABASE=healthcare_db
MONGO_USER=admin
MONGO_PASS=MySecurePassword123
MONGO_CLUSTER=cluster0.abc123.mongodb.net

MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=myemail@gmail.com
MAIL_PASS=myapppassword

BASE_URL=http://localhost:8080
PORT=8080

STRIPE_SECRET_KEY=
```

### Example 2: Local MongoDB (No Authentication)
```properties
MONGO_DATABASE=healthcare_db
MONGO_USER=
MONGO_PASS=
MONGO_CLUSTER=localhost:27017

MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=
MAIL_PASS=

BASE_URL=http://localhost:8080
PORT=8080

STRIPE_SECRET_KEY=
```

---

## ✅ Step 5: Verify Connection

After creating the `.env` file:

### 1. Clean and rebuild the project:
```bash
# Windows
.\mvnw.cmd clean install

# Linux/Mac
./mvnw clean install
```

### 2. Start the application:
```bash
# Windows
.\mvnw.cmd spring-boot:run

# Linux/Mac
./mvnw spring-boot:run
```

### 3. Watch for these logs:

#### ✅ Success Logs:
```
🚀 Initializing sample data...
✅ Admin user created - Email: admin@healthcare.com, Password: admin123
✅ Doctor 1 created - Email: doctor1@healthcare.com, Password: doctor123
✅ Doctor 2 created - Email: doctor2@healthcare.com, Password: doctor123
... (more doctors)
✅ Staff member created - Email: staff@healthcare.com, Password: staff123
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

#### ❌ Error Logs (Connection Failed):
```
Error connecting to MongoDB
Authentication failed
Connection timeout
```

---

## 🔍 Step 6: Test MongoDB Connection

### Option 1: Use MongoDB Compass
1. Download [MongoDB Compass](https://www.mongodb.com/products/compass)
2. Open Compass
3. Enter your connection string:
   ```
   mongodb+srv://<username>:<password>@<cluster>.mongodb.net/
   ```
4. Click "Connect"
5. You should see your databases

### Option 2: Use MongoDB Shell
```bash
mongosh "mongodb+srv://<username>:<password>@<cluster>.mongodb.net/"
```

---

## 🐛 Troubleshooting

### Problem 1: Authentication Failed
**Solution**: 
- Double-check your username and password
- Ensure no special characters need URL encoding
- Password with special characters might need encoding:
  - `@` → `%40`
  - `#` → `%23`
  - `$` → `%24`

### Problem 2: Connection Timeout
**Solution**:
- Check your internet connection
- Verify cluster address is correct
- Check MongoDB Atlas IP whitelist (allow 0.0.0.0/0 for testing)

### Problem 3: Database Not Found
**Solution**:
- The database will be created automatically when data is inserted
- Ensure `MONGO_DATABASE` name is correct
- No spaces or special characters in database name

### Problem 4: .env File Not Being Read
**Solution**:
- Ensure the file is named exactly `.env` (not `.env.txt`)
- File should be in the root directory: `F:\Y3S1\Healthcare-System\.env`
- Restart the application after creating/modifying `.env`
- Check if spring-dotenv dependency is in `pom.xml`:
  ```xml
  <dependency>
      <groupId>me.paulschwarz</groupId>
      <artifactId>spring-dotenv</artifactId>
      <version>2.5.4</version>
  </dependency>
  ```

### Problem 5: Still No Data in Database
**Solution**:
1. Stop the application
2. Delete all collections in MongoDB
3. Restart the application
4. Data will be recreated

---

## 📊 Verify Data in MongoDB

### Using MongoDB Compass:
1. Connect to your cluster
2. Find the `healthcare_db` database
3. Check these collections:
   - `users` (should have 11 documents)
   - `hospitals` (should have 3 documents)
   - `appointments` (should have 2+ documents)
   - `medical_records` (should have 15+ documents)
   - `payments` (should have 8+ documents)
   - `health_cards` (should have 2+ documents)
   - `time_slot_reservations` (should have 10 documents)

### Using MongoDB Shell:
```javascript
use healthcare_db

// Check users
db.users.countDocuments()
// Should return 11

// Check hospitals
db.hospitals.countDocuments()
// Should return 3

// Check all collections
db.getCollectionNames()
```

---

## 🔐 Security Notes

### ⚠️ Important:
1. **Never commit `.env` file to git** (it's in `.gitignore` by default)
2. **Use strong passwords** for MongoDB
3. **Restrict IP access** in MongoDB Atlas (not 0.0.0.0/0 in production)
4. **Rotate credentials** regularly

---

## 🎯 Quick Test Commands

### Test 1: Check if .env file exists
```bash
# Windows PowerShell
Test-Path .env

# Should return True
```

### Test 2: Start application and watch logs
```bash
.\mvnw.cmd spring-boot:run
```

### Test 3: Check MongoDB connection
```bash
# Try to connect using mongosh
mongosh "mongodb+srv://<username>:<password>@<cluster>.mongodb.net/"
```

---

## 📞 Still Having Issues?

### Checklist:
- [ ] `.env` file created in root directory
- [ ] MongoDB credentials are correct
- [ ] Internet connection is working
- [ ] MongoDB Atlas IP whitelist configured
- [ ] spring-dotenv dependency in pom.xml
- [ ] Application restarted after creating .env
- [ ] No typos in environment variable names

### Get More Help:
1. Check application logs for specific error messages
2. Test MongoDB connection with MongoDB Compass
3. Verify credentials in MongoDB Atlas dashboard
4. Check if MongoDB cluster is running

---

## 📚 Related Documentation

- **QUICK_START.md** - Quick start guide
- **DATA_IMPORT_README.md** - Data import documentation
- **SAMPLE_DATA_DOCUMENTATION.md** - Sample data details
- **application.properties** - Application configuration

---

**Last Updated**: October 17, 2025  
**Status**: Configuration Required ⚠️

