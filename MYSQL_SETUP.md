# 🗄️ MYSQL SETUP - Step by Step

**MySQL தான் வேணும்! Complete Setup Guide**

---

## ✅ CURRENT STATUS:
- ✅ settings.py - MySQL configured
- ✅ mysqlclient - Installed (v2.2.8)
- ✅ .env file - Created
- ⏳ MySQL Server - Need to install & setup

---

## 📥 STEP 1: INSTALL MYSQL SERVER

### Download & Install:
```
1. Visit: https://dev.mysql.com/downloads/installer/
2. Download: "mysql-installer-community-8.0.xx.msi"
3. Run installer
4. Choose: "Developer Default" or "Server Only"
5. Set root password (or keep empty)
6. Complete installation
```

**Important:** Installation-ல root password set பண்ணினா, அதை `.env` file-ல் update பண்ணுங்க!

---

## 🔧 STEP 2: VERIFY MYSQL INSTALLATION

```bash
# Check MySQL version
mysql --version

# Should show:
# mysql  Ver 8.0.xx for Win64
```

---

## 🗄️ STEP 3: CREATE DATABASE

### Option A: Using MySQL Command Line

```bash
# Login to MySQL
mysql -u root -p
# Enter password if set, or just press Enter

# Create database
CREATE DATABASE dineat_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

# Verify
SHOW DATABASES;
# You should see 'dineat_db' in the list

# Exit
EXIT;
```

### Option B: Using MySQL Workbench

```
1. Open MySQL Workbench
2. Connect to localhost
3. Click "Create Schema" icon
4. Name: dineat_db
5. Charset: utf8mb4
6. Collation: utf8mb4_unicode_ci
7. Apply
```

---

## 📝 STEP 4: UPDATE .ENV FILE (If Password Set)

Edit: `backend/.env`

```env
DB_NAME=dineat_db
DB_USER=root
DB_PASSWORD=your_mysql_password_here  ← Update this!
DB_HOST=localhost
DB_PORT=3306
```

**Note:** Password இல்லாட்டி empty-ஆ விடுங்க!

---

## 🚀 STEP 5: RUN DJANGO MIGRATIONS

```bash
# Backend folder-க்கு போங்க
cd "c:\Users\Gokul Kumar\Desktop\pro\backend"

# Create migration files
python manage.py makemigrations

# Apply migrations to MySQL
python manage.py migrate

# You should see:
# Running migrations:
#   Applying contenttypes.0001_initial... OK
#   Applying accounts.0001_initial... OK
#   Applying orders.0001_initial... OK
#   etc...
```

---

## 👤 STEP 6: CREATE SUPERUSER

```bash
python manage.py createsuperuser

# Enter details:
Username: admin
Email address: admin@dineat.com
Password: ********
Password (again): ********

# Superuser created successfully!
```

---

## 🎉 STEP 7: START SERVER!

```bash
python manage.py runserver

# Server starts at:
# http://127.0.0.1:8000/
```

---

## 🔍 VERIFY DATABASE

### Check Tables in MySQL:

```bash
mysql -u root -p
USE dineat_db;
SHOW TABLES;

# You should see:
# +------------------------------+
# | Tables_in_dineat_db          |
# +------------------------------+
# | accounts_customuser          |
# | django_admin_log             |
# | django_content_type          |
# | django_migrations            |
# | django_session               |
# | orders_menuitem              |
# | orders_order                 |
# | orders_orderitem             |
# | orders_table                 |
# +------------------------------+
```

---

## ⚡ QUICK COMMANDS (After Setup):

```bash
# 1. Start MySQL service (if stopped)
net start MySQL80

# 2. Start Django server
cd "c:\Users\Gokul Kumar\Desktop\pro\backend"
python manage.py runserver

# 3. Access
http://localhost:8000/
```

---

## ⚠️ TROUBLESHOOTING:

### Error: "Can't connect to MySQL server"
```bash
# Check MySQL service running
net start MySQL80

# Or restart
net stop MySQL80
net start MySQL80
```

### Error: "Access denied for user 'root'"
```bash
# Check password in .env file
# Or reset MySQL root password
```

### Error: "Unknown database 'dineat_db'"
```bash
# Create database again
mysql -u root -p
CREATE DATABASE dineat_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
EXIT;
```

---

## 📊 NEXT STEPS AFTER SERVER STARTS:

1. ✅ Visit http://localhost:8000/
2. ✅ Test all pages (15 pages migrated)
3. ✅ Login to admin: http://localhost:8000/admin/
4. ✅ Create menu items
5. ✅ Create tables
6. ✅ Test order flow

---

**MySQL setup complete பண்ணினா உங்க project production-ready!** 🚀
