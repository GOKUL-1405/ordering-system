# 🚀 HOW TO RUN - DineAt Project

**Quick Start Guide** - எப்படி run பண்றது

---

## ⚡ QUICK START (2 நிமிஷம்):

### Option 1: WITHOUT MySQL (SQLite - Instant Start)

```bash
# 1. Backend folder-க்கு போங்க
cd "c:\Users\Gokul Kumar\Desktop\pro\backend"

# 2. SQLite-க்கு மாத்துங்க (temporary)
# settings.py-ல் database config-ஐ மாத்தணும்

# 3. Migrations run பண்ணுங்க
python manage.py makemigrations
python manage.py migrate

# 4. Admin user create பண்ணுங்க
python manage.py createsuperuser

# 5. Server start!
python manage.py runserver
```

### Option 2: WITH MySQL (Production Setup)

```bash
# 1. MySQL install & database create (DATABASE_SETUP.md பாருங்க)
mysql -u root -p
CREATE DATABASE dineat_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
EXIT;

# 2. Backend folder-க்கு போங்க
cd "c:\Users\Gokul Kumar\Desktop\pro\backend"

# 3. Migrations run பண்ணுங்க
python manage.py makemigrations
python manage.py migrate

# 4. Admin user create பண்ணுங்க
python manage.py createsuperuser

# 5. Server start!
python manage.py runserver
```

---

## 📋 DETAILED STEPS:

### Step 1: Backend Folder-க்கு போங்க

```bash
cd "c:\Users\Gokul Kumar\Desktop\pro\backend"
```

### Step 2: Virtual Environment (Optional but Recommended)

```bash
# Create virtual environment
python -m venv venv

# Activate
venv\Scripts\activate

# Install requirements
pip install -r requirements.txt
```

### Step 3: Database Setup

#### For SQLite (Quick Test):
இப்போவே settings.py-ல் SQLite config uncomment பண்ணி இருக்கு, so direct-ஆ migrate பண்ணலாம்!

#### For MySQL (Production):
```bash
# MySQL create database
mysql -u root -p
CREATE DATABASE dineat_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
SHOW DATABASES;
EXIT;
```

### Step 4: Run Migrations

```bash
# Create migration files
python manage.py makemigrations

# Apply to database
python manage.py migrate
```

### Step 5: Create Admin User

```bash
python manage.py createsuperuser

# Enter details:
Username: admin
Email: admin@dineat.com
Password: ******** (strong password)
Password (again): ********
```

### Step 6: Run Server!

```bash
python manage.py runserver

# Server starts at:
# http://127.0.0.1:8000/
# http://localhost:8000/
```

---

## 🌐 ACCESS URLS:

```
Homepage:           http://localhost:8000/
Admin Panel:        http://localhost:8000/admin/
Customer Login:     http://localhost:8000/accounts/customer/login/
Kitchen Login:      http://localhost:8000/accounts/kitchen/login/
Admin Login:        http://localhost:8000/accounts/admin/login/
Kitchen Dashboard:  http://localhost:8000/dashboard/kitchen/
Admin Dashboard:    http://localhost:8000/dashboard/admin/
```

---

## ⚠️ COMMON ERRORS & FIXES:

### Error 1: "No module named 'decouple'"
```bash
pip install python-decouple
```

### Error 2: "No module named 'mysqlclient'"
```bash
pip install mysqlclient
# Or alternative:
pip install pymysql
```

### Error 3: "Can't connect to MySQL server"
**Fix:** MySQL server running இல்லை
```bash
# Check MySQL service
net start MySQL80

# Or switch to SQLite temporarily (see below)
```

### Error 4: "Table doesn't exist"
```bash
# Run migrations
python manage.py migrate
```

---

## 🔄 SWITCH TO SQLITE (Quick Fix):

If MySQL-ல் problem இருந்தா, SQLite use பண்ணலாம்:

**Edit:** `DineAt/settings.py` (line 85-107)

```python
# Comment MySQL config:
# DATABASES = {
#     'default': {
#         'ENGINE': 'django.db.backends.mysql',
#         ...
#     }
# }

# Uncomment SQLite config:
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

Then run:
```bash
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

---

## 🎯 ONE-COMMAND RUN (After First Setup):

```bash
cd "c:\Users\Gokul Kumar\Desktop\pro\backend" && python manage.py runserver
```

---

## 📸 WHAT YOU'LL SEE:

```
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
February 12, 2026 - 19:20:00
Django version 5.0, using settings 'DineAt.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```

---

## ✅ VERIFICATION:

### 1. Browser-ல் open பண்ணுங்க:
```
http://localhost:8000/
```

### 2. நீங்க இதை பார்க்கணும்:
- ✅ Beautiful homepage with hero section
- ✅ Navigation working
- ✅ Login buttons working
- ✅ All pages responsive

### 3. Admin Panel Check:
```
http://localhost:8000/admin/
Login: admin / your_password
```

---

## 🔧 TROUBLESHOOTING:

### Server won't start?
```bash
# Check Python version
python --version  # Should be 3.10+

# Check Django installed
pip show django

# Check port 8000 available
netstat -ano | findstr :8000
```

### Static files not loading?
```bash
# Collect static files
python manage.py collectstatic --noinput
```

### Database errors?
```bash
# Reset migrations (careful - deletes data!)
python manage.py flush
python manage.py migrate
```

---

## 📱 MOBILE TESTING:

```bash
# Run on network
python manage.py runserver 0.0.0.0:8000

# Access from phone:
http://YOUR_IP:8000/
# Example: http://192.168.1.100:8000/
```

---

## 🎉 SUCCESS CHECKLIST:

- ✅ Server starts without errors
- ✅ Homepage loads (http://localhost:8000/)
- ✅ Login pages accessible
- ✅ Admin panel working
- ✅ All 15 pages migrated
- ✅ CSS/JS loading correctly
- ✅ Database connected

---

**இப்போ run பண்ணலாம்! Simple-ஆ `python manage.py runserver` போட்டா போதும்!** 🚀
