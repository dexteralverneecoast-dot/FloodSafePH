# Coffee Shop Web Application - XAMPP Installation Guide

A professional, modern coffee shop ordering system with customer and seller dashboards.

## Features

### Customer Side
- 📱 QR Code / URL access
- ☕ Professional menu display with images and prices
- 🛒 Shopping cart with quantity management
- 📝 Order summary with unique order numbers
- 🔔 Real-time notifications when order is ready

### Seller Dashboard
- 📊 Real-time order management
- 📈 Live statistics (pending, ready, completed)
- 🔄 Order status updates
- 🔔 Notification system for new orders
- ⚡ Auto-refresh every 5 seconds

## Installation Instructions

### Step 1: Install XAMPP
1. Download XAMPP from https://www.apachefriends.org/
2. Install XAMPP on your computer
3. Start Apache and MySQL services from XAMPP Control Panel

### Step 2: Setup Project Files
1. Copy the entire `coffee-shop` folder to:
   ```
   C:\xampp\htdocs\coffee-shop
   ```
   (On Mac/Linux: `/Applications/XAMPP/htdocs/coffee-shop`)

2. Your folder structure should look like:
   ```
   htdocs/
   └── coffee-shop/
       ├── index.html
       ├── seller.html
       ├── css/
       │   ├── style.css
       │   └── seller.css
       ├── js/
       │   ├── app.js
       │   └── seller.js
       ├── api/
       │   ├── place_order.php
       │   ├── get_orders.php
       │   ├── update_order_status.php
       │   └── send_notification.php
       └── database/
           └── schema.sql
   ```

### Step 3: Setup Database
1. Open your browser and go to: `http://localhost/phpmyadmin`
2. Click on "Import" tab
3. Click "Choose File" and select `database/schema.sql`
4. Click "Go" to execute the SQL
5. The database `coffee_shop` will be created with all necessary tables

**OR** manually create database:
1. Click "New" in phpMyAdmin
2. Database name: `coffee_shop`
3. Click "Create"
4. Click on the database, then "SQL" tab
5. Copy and paste the contents of `database/schema.sql`
6. Click "Go"

### Step 4: Access the Application

#### Customer Interface
Open your browser and go to:
```
http://localhost/coffee-shop/
```

#### Seller Dashboard
Open your browser and go to:
```
http://localhost/coffee-shop/seller.html
```

### Step 5: Testing the System

1. **Place an Order (Customer Side)**:
   - Click "View Menu"
   - Add items to cart
   - Click on the floating cart or cart icon
   - Click "Place Order"
   - Note the order number

2. **Manage Orders (Seller Side)**:
   - Open seller dashboard
   - See the new order appear
   - Click "Mark as Ready"
   - Customer receives notification (simulated)

## Database Configuration

If you need to change database credentials, edit these files:
- `api/place_order.php`
- `api/get_orders.php`
- `api/update_order_status.php`

Change these lines:
```php
$servername = "localhost";
$username = "root";
$password = "";  // Add password if you set one
$dbname = "coffee_shop";
```

## Mobile Access (QR Code Setup)

To access from mobile devices on the same network:

1. Find your computer's IP address:
   - Windows: Open CMD, type `ipconfig`
   - Mac/Linux: Open Terminal, type `ifconfig`
   - Look for IPv4 address (e.g., 192.168.1.100)

2. Access from mobile:
   ```
   http://YOUR_IP_ADDRESS/coffee-shop/
   ```
   Example: `http://192.168.1.100/coffee-shop/`

3. Generate QR Code:
   - Use any QR code generator online
   - Input your URL: `http://YOUR_IP_ADDRESS/coffee-shop/`
   - Print and place QR code at tables

## Customization

### Change Menu Items
Edit `js/app.js` - modify the `menuData` array:
```javascript
const menuData = [
    { id: 1, name: 'Your Coffee', price: 3.50, type: 'coffee', image: '☕' },
    // Add more items...
];
```

### Change Colors
Edit `css/style.css` - modify CSS variables:
```css
:root {
    --primary-brown: #6B4423;
    --dark-brown: #3E2723;
    --cream: #FFF8E7;
}
```

### Modify Notifications
Edit `api/send_notification.php` to integrate:
- Firebase Cloud Messaging (Push Notifications)
- Twilio (SMS)
- Email services

## Troubleshooting

### Orders not appearing in seller dashboard?
- Check if Apache and MySQL are running in XAMPP
- Verify database is created correctly
- Check browser console for errors (F12)

### Can't connect to database?
- Make sure MySQL is running in XAMPP
- Check database credentials in PHP files
- Verify database name is `coffee_shop`

### CSS/JS not loading?
- Clear browser cache (Ctrl+Shift+Del)
- Check file paths are correct
- Verify files are in correct folders

### Mobile devices can't access?
- Make sure computer and mobile are on same WiFi
- Check firewall settings allow HTTP traffic
- Use correct IP address (not localhost)

## System Requirements

- XAMPP 7.4 or higher
- PHP 7.4+
- MySQL 5.7+
- Modern web browser (Chrome, Firefox, Safari, Edge)

## Security Notes for Production

Before deploying to production:
1. Change database password
2. Add user authentication
3. Implement CSRF protection
4. Use HTTPS (SSL certificate)
5. Sanitize all user inputs
6. Add rate limiting
7. Implement proper error handling

## Support

For issues or questions:
1. Check the troubleshooting section
2. Verify all installation steps completed
3. Check XAMPP error logs in `xampp/apache/logs/`

## License

This project is created for educational and commercial use.

---

**Quick Start Command Summary:**
1. Install XAMPP
2. Copy files to `htdocs/coffee-shop`
3. Import `database/schema.sql` in phpMyAdmin
4. Open `http://localhost/coffee-shop/`
5. Start ordering! ☕
