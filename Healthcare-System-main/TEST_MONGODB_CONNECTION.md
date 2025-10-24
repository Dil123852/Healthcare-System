# 🧪 Test MongoDB Connection - Quick Guide

## 🎯 Issue: No Sample Data in Database

**Root Cause**: Missing `.env` file with MongoDB credentials

---

## ✅ Quick Fix (5 Steps)

### Step 1: Create `.env` File

Create a file named `.env` in your project root folder:
```
F:\Y3S1\Healthcare-System\.env
```

**How to create:**
1. Right-click in the project root folder
2. New → Text Document
3. Name it `.env` (make sure to remove `.txt` extension)
4. Open with Notepad or VS Code

### Step 2: Add This Content to `.env`

```properties
# REQUIRED - MongoDB Configuration
MONGO_DATABASE=healthcare_db
MONGO_USER=YOUR_USERNAME_HERE
MONGO_PASS=YOUR_PASSWORD_HERE
MONGO_CLUSTER=YOUR_CLUSTER_HERE

# OPTIONAL - Email (can leave as-is for now)
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=
MAIL_PASS=

# REQUIRED - Application
BASE_URL=http://localhost:8080
PORT=8080

# OPTIONAL - Stripe
STRIPE_SECRET_KEY=
```

### Step 3: Replace with Your MongoDB Credentials

**If you're using MongoDB Atlas:**

Go to: https://cloud.mongodb.com/
1. Login to your account
2. Click your cluster
3. Click "Connect" button
4. Choose "Connect your application"
5. Copy the connection string

**Connection string looks like:**
```
mongodb+srv://admin:MyPassword123@cluster0.abc123.mongodb.net/myFirstDatabase
```

**Extract these values:**
- `MONGO_USER` = `admin`
- `MONGO_PASS` = `MyPassword123`
- `MONGO_CLUSTER` = `cluster0.abc123.mongodb.net`
- `MONGO_DATABASE` = `healthcare_db` (you can use any name)

**Example .env file:**
```properties
MONGO_DATABASE=healthcare_db
MONGO_USER=admin
MONGO_PASS=MyPassword123
MONGO_CLUSTER=cluster0.abc123.mongodb.net

MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=
MAIL_PASS=

BASE_URL=http://localhost:8080
PORT=8080

STRIPE_SECRET_KEY=
```

### Step 4: Verify `.env` File Location

**Check file location:**
```
F:\Y3S1\Healthcare-System\.env    ← Should be here!
```

**NOT here:**
```
F:\Y3S1\Healthcare-System\src\.env        ❌ Wrong location
F:\Y3S1\Healthcare-System\.env.txt        ❌ Wrong extension
```

### Step 5: Start the Application

```bash
.\mvnw.cmd spring-boot:run
```

---

## 🔍 What to Look For

### ✅ SUCCESS - You should see these logs:

```
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

2025-10-17 ... : Starting HealthCareSystemApplication

🚀 Initializing sample data...

✅ Admin user created - Email: admin@healthcare.com, Password: admin123
✅ Doctor 1 created - Email: doctor1@healthcare.com, Password: doctor123
✅ Doctor 2 created - Email: doctor2@healthcare.com, Password: doctor123
✅ Doctor 3 created - Email: doctor3@healthcare.com, Password: doctor123
✅ Doctor 4 created - Email: doctor4@healthcare.com, Password: doctor123
✅ Doctor 5 created - Email: doctor5@healthcare.com, Password: doctor123
✅ Doctor 6 created - Email: doctor6@healthcare.com, Password: doctor123
✅ Doctor 7 created - Email: doctor7@healthcare.com, Password: doctor123
✅ Doctor 8 created - Email: doctor8@healthcare.com, Password: doctor123
✅ Staff member created - Email: staff@healthcare.com, Password: staff123

🏥 Creating sample hospitals...
   ✓ City Medical Center created with 3 doctors
   ✓ General Hospital created with 3 doctors
   ✓ National Hospital created with 2 doctors
✅ All hospitals created successfully!

📋 Creating sample medical records...
   ✓ Created 15 medical records
✅ All medical records created successfully!

👥 Creating sample patients and appointments...
   ✓ Sample patients and appointments created.

💳 Creating sample payments...
   ✓ Created 8 payments
✅ All payments created successfully!

🏥 Creating sample health cards...
   ✓ Created 2 health cards
✅ All health cards created successfully!

⏰ Creating sample time slot reservations...
   ✓ Created 10 time slot reservations
✅ All time slot reservations created successfully!

✅ Data initialization completed!

2025-10-17 ... : Started HealthCareSystemApplication in 12.345 seconds
```

### ❌ FAILURE - Common Error Messages:

#### Error 1: Cannot load .env file
```
Error: Could not load environment variables
```
**Fix**: Create `.env` file in root directory

#### Error 2: Authentication failed
```
MongoSecurityException: Exception authenticating
```
**Fix**: Check your username and password in `.env`

#### Error 3: Connection timeout
```
MongoTimeoutException: Timed out after 30000 ms
```
**Fix**: 
- Check internet connection
- Verify cluster address
- Check MongoDB Atlas IP whitelist

#### Error 4: No database
```
Database not found
```
**Fix**: Database will be created automatically - this is not an error if data is being created

---

## 📊 Verify Data Created Successfully

### Option 1: Using MongoDB Compass (Recommended)

1. **Download MongoDB Compass**: https://www.mongodb.com/try/download/compass
2. **Install and open it**
3. **Connect using your connection string:**
   ```
   mongodb+srv://YOUR_USER:YOUR_PASS@YOUR_CLUSTER/healthcare_db
   ```
4. **Check for these collections in `healthcare_db`:**
   - ✅ `users` → Should have **11 documents**
   - ✅ `hospitals` → Should have **3 documents**
   - ✅ `appointments` → Should have **2+ documents**
   - ✅ `medical_records` → Should have **15+ documents**
   - ✅ `payments` → Should have **8+ documents**
   - ✅ `health_cards` → Should have **2+ documents**
   - ✅ `time_slot_reservations` → Should have **10 documents**

### Option 2: Using Application Logs

Look for these specific lines in the logs:
```
✅ Admin user created
✅ Doctor 1-8 created
✅ Staff member created
✓ City Medical Center created with 3 doctors
✓ General Hospital created with 3 doctors
✓ National Hospital created with 2 doctors
✓ Created 15 medical records
✓ Created 8 payments
✓ Created 2 health cards
✓ Created 10 time slot reservations
✅ Data initialization completed!
```

If you see ALL these messages, your data is successfully created! ✅

---

## 🐛 Troubleshooting Checklist

Run through this checklist:

### File Check:
- [ ] `.env` file exists in `F:\Y3S1\Healthcare-System\`
- [ ] File is named exactly `.env` (not `.env.txt`)
- [ ] File contains all required variables
- [ ] No spaces before/after `=` sign
- [ ] No quotes around values

### MongoDB Check:
- [ ] MongoDB Atlas account is active
- [ ] Cluster is running (not paused)
- [ ] Username and password are correct
- [ ] Database user has read/write permissions
- [ ] IP address is whitelisted (or use 0.0.0.0/0 for testing)

### Application Check:
- [ ] Application restarted after creating `.env`
- [ ] No other instance of application running
- [ ] Port 8080 is available
- [ ] Java is installed and configured

---

## 🎯 Quick Test Commands

### Test 1: Check if .env exists
```powershell
# Open PowerShell in project directory
Test-Path .env
# Should return: True
```

### Test 2: View .env content (without password)
```powershell
Get-Content .env | Select-String -Pattern "MONGO_DATABASE","MONGO_USER","MONGO_CLUSTER"
```

### Test 3: Start application
```powershell
.\mvnw.cmd spring-boot:run
```

### Test 4: Test MongoDB connection manually
**Download MongoDB Compass and try connecting with:**
```
mongodb+srv://YOUR_USER:YOUR_PASS@YOUR_CLUSTER/
```

---

## 💡 Pro Tips

### Tip 1: Use MongoDB Atlas (Free Tier)
- Go to: https://www.mongodb.com/cloud/atlas/register
- Create a free account (M0 Free Tier)
- Create a cluster (takes 3-5 minutes)
- Create a database user
- Add IP to whitelist: `0.0.0.0/0` (for testing)
- Get connection string

### Tip 2: Don't Commit .env File
The `.env` file is in `.gitignore` - this is correct!
Never commit credentials to Git.

### Tip 3: Test Connection First
Before running the app, test your MongoDB connection with MongoDB Compass.

### Tip 4: Clear Database if Needed
If data is partially created or corrupt:
```javascript
// In MongoDB Compass or Shell
use healthcare_db
db.dropDatabase()
// Then restart the application
```

---

## 🎓 Example: Complete Setup

**My MongoDB Atlas Connection String:**
```
mongodb+srv://admin:SecurePass123@cluster0.mongodb.net/myFirstDatabase
```

**My .env file should be:**
```properties
MONGO_DATABASE=healthcare_db
MONGO_USER=admin
MONGO_PASS=SecurePass123
MONGO_CLUSTER=cluster0.mongodb.net

MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=
MAIL_PASS=

BASE_URL=http://localhost:8080
PORT=8080

STRIPE_SECRET_KEY=
```

**Start the application:**
```bash
.\mvnw.cmd spring-boot:run
```

**Expected result:**
- Application starts successfully
- All 8 collections created
- Total 51+ documents created
- Ready to login!

---

## 📞 Still Not Working?

### Run this command and share the output:
```powershell
# Check if .env exists
Test-Path .env

# Check Java version
java -version

# Try to start application
.\mvnw.cmd spring-boot:run
```

**Share the error message and I can help you further!**

---

## ✨ Success Criteria

You'll know everything is working when:

1. ✅ Application starts without errors
2. ✅ You see "Data initialization completed!" in logs
3. ✅ MongoDB Compass shows 8 collections
4. ✅ You can login at http://localhost:8080
5. ✅ Login credentials work:
   - `admin@healthcare.com` / `admin123`
   - `doctor1@healthcare.com` / `doctor123`
   - `alice@example.com` / `patient123`

---

**Need the full guide?** See `MONGODB_SETUP_GUIDE.md` for detailed instructions.

**Ready to use the app?** See `QUICK_START.md` for login credentials and features.

