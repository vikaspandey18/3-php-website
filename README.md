# 3-php-website

# 1. SSH into the EC2 instance
ssh -i /path/to/your-key.pem ubuntu@your-ec2-instance-public-ip

# 2. Update Packages
```sudo apt update && sudo apt upgrade -y```

# 3. Install Apache
```sudo apt install apache2 -y```

```sudo systemctl start apache2```

```sudo systemctl enable apache2```

# 4. Install PHP
```sudo apt install php libapache2-mod-php php-mbstring php-xml php-cli php-curl -y```

```php -v```

# 5. Install MySQL
```sudo apt install mysql-server -y```

```sudo systemctl start mysql```

```sudo systemctl enable mysql```

# Secure MySQL
```sudo mysql_secure_installation```

# 6. Install phpMyAdmin
```sudo apt install phpmyadmin -y```

When it shows error

```sudo ln -s /usr/share/phpmyadmin /var/www/html/phpmyadmin```

# 7. Configure MySQL Access for phpMyAdmin
Option 1: Set root user access (testing only, not recommended for production)

```sudo mysql -u root -p```

You will get password when setting up phpmyadmin

# Run inside MySQL prompt:
```ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_password';```

```FLUSH PRIVILEGES;```

```EXIT;```

# Option 2: Create a new MySQL user for phpMyAdmin (recommended)
```sudo mysql -u root -p```

# Run inside MySQL prompt:
```CREATE USER 'admin'@'localhost' IDENTIFIED BY 'admin@456';```

```GRANT ALL PRIVILEGES ON *.* TO 'admin'@'localhost' WITH GRANT OPTION;```

```FLUSH PRIVILEGES;```

```EXIT;```

# 8. Restart Apache
```sudo systemctl restart apache2```

# 9. Enable File Permission
```sudo chown ubuntu /var/www/html```
