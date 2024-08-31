![QuranBot](https://your-image-link-here.com)

<hr>

# Quran Bot • Discord Bot for Recurring Athkar Messages

All features:
- Schedule recurring Athkar messages in specified channels
- Role-based access control for scheduling and cancelling Athkar
- Supports flexible intervals (seconds, minutes, hours, days)
- Admin command to cancel scheduled Athkar
- Integrated with MySQL for data storage and retrieval
- Easy configuration with `config.js`
- Secure and scalable MySQL connection pooling

<hr>

# Install Guide

## 1. Configuring Quran Bot

### Requirements
- Node.js and npm installed on your system
- MySQL server installed and running

### Installation Steps

<strong>1.1</strong> Clone the repository and navigate to the project folder:

```bash
git clone https://github.com/8O80/quran-bot.git
cd quran-bot

<strong>1.2</strong> Install the required Node.js dependencies:

npm install

<strong>1.3</strong> Configure config.js by creating or modifying the existing file with your own details:

// config.js
module.exports = {
    botToken: 'YOUR_DISCORD_BOT_TOKEN',
    Roles: {
        adminRole: 'ADMIN_ROLE_ID'  // Replace with your admin role ID
    },
    // Add any other necessary configurations
};

Ensure to replace YOUR_DISCORD_BOT_TOKEN with your actual Discord bot token and ADMIN_ROLE_ID with the role ID that can manage Athkar.

<strong>2.1</strong> Install MySQL server if you haven't already. You can download it from mysql.com.

<strong>2.2</strong> Open your MySQL client and run the following commands to set up the database and table:

CREATE DATABASE quran_bot;

USE quran_bot;

CREATE TABLE athkar_schedule (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id VARCHAR(255) NOT NULL,
    channel_id VARCHAR(255) NOT NULL,
    `interval` VARCHAR(50) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    UNIQUE KEY unique_user_channel (user_id, channel_id)
);

<strong>2.3</strong> Fill in your MySQL connection details in mysql.js:

// mysql.js
const mysql = require('mysql2');

const pool = mysql.createPool({
    host: 'host',  // Replace with your MySQL host
    user: 'user',       // Replace with your MySQL username
    password: 'Password', // Replace with your MySQL password
    database: 'quran_bot',  
    waitForConnections: true,
    connectionLimit: 10,
    queueLimit: 0
});

const db = pool.promise();

module.exports = db;

Replace host, user, password, and database with your actual MySQL server configuration.

<strong>3.1</strong> Start the bot by running the following command:

node index.js

4. Configuring MySQL Credentials

Ensure that your mysql.js file is correctly configured with your database credentials to enable successful connection to the MySQL server.

5. Contributing
Contributions are welcome! Please fork the repository, make your changes, and submit a pull request. For major changes, please open an issue first to discuss what you would like to change.

6. License
This project is licensed under the MIT License. See the LICENSE file for more information.

<hr>

