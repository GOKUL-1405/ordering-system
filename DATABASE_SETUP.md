# 🗄️ MySQL DATABASE SETUP GUIDE

## ✅ Current Status:
**Database:** MySQL configured  
**Database Name:** `dineat_db`  
**User:** root  
**Host:** localhost  
**Port:** 3306

---

## 📋 SETUP STEPS:

### 1️⃣ **MySQL Install பண்ணுங்க**

#### Windows:
```bash
# Download MySQL Installer from:
https://dev.mysql.com/downloads/installer/

# Or use chocolatey:
choco install mysql
```

#### Verify Installation:
```bash
mysql --version
```

---

### 2️⃣ **Database Create பண்ணுங்க**

```bash
# MySQL-ல் login பண்ணுங்க
mysql -u root -p

# Password கேட்டா enter பண்ணுங்க (empty-ஆ இருந்தா just Enter)
```

```sql
-- Database create பண்ணுங்க
CREATE DATABASE dineat_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Check பண்ணுங்க
SHOW DATABASES;

-- Exit பண்ணுங்க
EXIT;
```

---

### 3️⃣ **Python MySQL Driver Install பண்ணுங்க**

```bash
# mysqlclient install பண்ணுங்க
pip install mysqlclient

# Or PyMySQL (alternative):
pip install pymysql
```

---

### 4️⃣ **Environment File (.env) Configure பண்ணுங்க**

`.env` file already created with:
```env
DB_NAME=dineat_db
DB_USER=root
DB_PASSWORD=          # உங்க MySQL password இங்க போடுங்க
DB_HOST=localhost
DB_PORT=3306
```

**⚠️ Important:** If you have a MySQL password, update `DB_PASSWORD` in `.env` file!

---

### 5️⃣ **Django Migrations Run பண்ணுங்க**

```bash
# Backend folder-க்கு போங்க
cd c:\Users\Gokul Kumar\Desktop\pro\backend

# Migrations create பண்ணுங்க
python manage.py makemigrations

# Database-ல் apply பண்ணுங்க
python manage.py migrate

# Superuser create பண்ணுங்க
python manage.py createsuperuser
```

---

### 6️⃣ **Server Start பண்ணுங்க**

```bash
# Development server run பண்ணுங்க
python manage.py runserver

# Browser-ல் open பண்ணுங்க:
http://localhost:8000/
```

---

## 🔧 TROUBLESHOOTING:

### Error: "Can't connect to MySQL server"
```bash
# MySQL service check பண்ணுங்க
# Windows Services-ல் MySQL80 service running-ஆ இருக்கானு பாருங்க

# Or command line-ல்:
net start MySQL80
```

### Error: "mysqlclient not found"
```bash
# Install பண்ணுங்க
pip install mysqlclient

# If error, try PyMySQL:
pip install pymysql

# And add to settings.py (before DATABASES):
import pymysql
pymysql.install_as_MySQLdb()
```

### Error: "Access denied for user"
```bash
# Password correct-ஆ .env file-ல் இருக்கானு check பண்ணுங்க
# Or reset MySQL root password
```

---

## 📊 DATABASE VERIFICATION:

```bash
# MySQL-ல் login பண்ணி check பண்ணுங்க
mysql -u root -p

# Tables-ஐ பாருங்க
USE dineat_db;
SHOW TABLES;

# Should show Django tables like:
# - accounts_customuser
# - orders_order
# - orders_menuitem
# - orders_table
# - etc.
```

---

## ✅ CURRENT CONFIGURATION:

### settings.py:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'dineat_db',
        'USER': 'root',
        'PASSWORD': '',  # Update in .env if needed
        'HOST': 'localhost',
        'PORT': '3306',
        'OPTIONS': {
            'init_command': "SET sql_mode='STRICT_TRANS_TABLES'",
            'charset': 'utf8mb4',
        },
    }
}
```

---

## 🎯 NEXT STEPS:

1. ✅ MySQL installed
2. ✅ Database created (`dineat_db`)
3. ✅ mysqlclient installed
4. ✅ .env configured
5. ⏳ Run migrations
6. ⏳ Create superuser
7. ⏳ Start server

---

## 🚀 QUICK START (All-in-one):

```bash
# 1. Install MySQL client
pip install mysqlclient

# 2. Create database
mysql -u root -p
CREATE DATABASE dineat_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
EXIT;

# 3. Run migrations
cd backend
python manage.py makemigrations
python manage.py migrate

# 4. Create admin user
python manage.py createsuperuser

# 5. Start server
python manage.py runserver
```

---

## 📝 NOTES:

- **Database:** MySQL 8.0+ recommended
- **Python:** 3.10+ required
- **Django:** 5.0
- **Charset:** utf8mb4 (supports emojis and all Unicode)
- **Collation:** utf8mb4_unicode_ci

---

**MySQL connection ready! இப்போ migrations run பண்ணுங்க!** 🚀
