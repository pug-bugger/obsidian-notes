Make CI/CD with this tutorial: [**Deploy a Full Stack Application With GitHub Actions to a VPS from Hostinger — Part 1**](https://blog.devops.dev/deploy-a-full-stack-application-with-github-actions-to-a-vps-from-hostinger-part-1-fd08bc9d9325)

### Day 1

shh root password: k

Local ssh: cd ~/.ssh

The key fingerprint is: SHA256:I37vjCvsX0c3aguuh7oAir7QSO+nUG9mSWvgVO2HYGU

Password: keypug911

### Day 2

I copied public key to vps.

Connect to ssh with private key (not with password):

`ssh -i ~/.ssh/keypug [root@193.160.119.244](<mailto:root@193.160.119.244>)`

For passphrase use this: `keypug911`

<aside> 💡

Woohoo! it works, nice! now can go forward.

Now we need to create use key pair, for David.

</aside>

Creating user key pair.

1. ssh-keygen -t ed25519 -f ~/.ssh/david
2. User passphrase: david8ug
3. Password in vps user are same as passphrase.
4. login via ssh: `ssh -i ~/.ssh/david david[@](<mailto:robin@31.210.21.179>)193.160.119.244`

### Day 3

Disabled password login and left only login by key pair.

From david user server generated `github_actions` key. This is the key from `cat ~/.ssh/github_actions`

`-----BEGIN OPENSSH PRIVATE KEY----- b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW QyNTUxOQAAACD2L0uKjVpDpK4yDOhBZLXMVjzV80VID9lpfX7JO8yrnQAAAJj7mjP2+5oz 9gAAAAtzc2gtZWQyNTUxOQAAACD2L0uKjVpDpK4yDOhBZLXMVjzV80VID9lpfX7JO8yrnQ AAAEAHQ2IAKOtJm5lsCxy2bHY31psr9Y7pHhvm+dmg0A883/YvS4qNWkOkrjIM6EFktcxW PNXzRUgP2Wl9fsk7zKudAAAADnJvb3RAc3J2OTcwMzg0AQIDBAUGBw== -----END OPENSSH PRIVATE KEY-----`

Testing my action fn.

![Screenshot 2025-10-14 at 14.36.50.png](error-in-github-building.png)

for now is failing.

I do this to fix

1. `sudo chown -R david:david ~/.ssh`
2. `chmod 700 ~/.ssh`
3. and then `cat ~/.ssh/github_actions.pub >> ~/.ssh/authorized_keys`
4. `sudo apt update`
5. `sudo apt install -y nodejs npm`
6. and add this on top of script in yml file in github:

```jsx
script: |
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \\. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \\. "$NVM_DIR/bash_completion"

# Now your npm and pm2 will work

mkdir -p apps/frontend && cd apps/frontend
...
```

This let me fix error of pm2 not find…

Nice, it works good. All changes from commit going to vps and builds app automatically.

### Day 4

in this day i gonna prepare nginx in my vps.

Nginx is prepared, all changes in prod branch are immediately ran on vps server.

Left to do same with backend.

Try with cursor help replace backend logic to separate folder/repository and implement separate action in github to separate changes and make them independent from each other.

### Day 5

Researching server/backens side code preparing for cafe shop app.

### Day 6

Writing server side functionality.

### Day 7

Working on backend. Try to prepare backend server side to work with and synchronize changes between separate devices.

Interesting how to create Java server and deploy to VPS. Maybe it is better to use Java instead of nodejs?

I will use NodeJs backend in this project. And MySQL for database.

### 1. Install MySQL Server

`sudo apt update`

`sudo apt install mysql-server -y`

## Database (MySQL)

Relationships Diagram (simplified)

```jsx
roles ───< users
categories ───< products ───< product_items
│
└──< product_options

users ───< orders ───< order_items ─── product_items
```

Checking mysql status:

```jsx
sudo systemctl status mysql
```

Before start operating with DB, log in as root (database root)

```jsx
sudo mysql
# and then
USE church_cafe_db
```

Create mysql new database:

```jsx
CREATE DATABASE IF NOT EXISTS church_cafe CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
USE church_cafe;
```

Create tables:

```jsx
CREATE TABLE roles (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL UNIQUE,
    description VARCHAR(255)
);
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(120) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL,
    role_id INT,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (role_id) REFERENCES roles(id) ON DELETE SET NULL
);
```

Check tables:

```jsx
SHOW TABLES
```

### Day 8

Back-end start by `npm run dev`

Create users:

### Create users

Let’s say:

- `root` → full control (already exists)
- `david` → your development/admin user
- `staff` → read/write only (for app connection)
- `viewer` → read-only user

```sql
-- Create david user (full privileges)
CREATE USER 'david'@'localhost' IDENTIFIED BY 'yourStrongPassword';
GRANT ALL PRIVILEGES ON *.* TO 'david'@'localhost' WITH GRANT OPTION;

-- Create app user (for backend connection)
CREATE USER 'staff'@'localhost' IDENTIFIED BY 'appPassword123';
GRANT SELECT, INSERT, UPDATE, DELETE ON church_cafe.* TO 'staff'@'localhost';

-- Create viewer user (for analytics/read-only)
CREATE USER 'viewer'@'localhost' IDENTIFIED BY 'readOnlyPass';
GRANT SELECT ON church_cafe.* TO 'viewer'@'localhost';
```

Then apply changes:

```sql
FLUSH PRIVILEGES;
```

<aside> 💡

Need to implement security fn and remote connection in future: Allow Remote MySQL Connections sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf sudo ufw allow from your.ip.address.to.allow to any port 3306 mysql -u david -p

</aside>

### Day 9

Finished postman setup and wrote all endpoints and tested.

All works in local database for now. Same job I need to do in my VPS.

### Day N (2026-02-10)

Updated david user password to keypug911.

Logged to server by ssh

```jsx
CREATE DATABASE church_cafe_db; 
CREATE USER 'david'@'localhost' IDENTIFIED BY 'keypug911';
GRANT ALL ON church_cafe_db.* TO 'david'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

then from local computer

```jsx
scp backup.sql root@193.160.119.244:~
```

then in ssh

```jsx
mysql -u david -p church_cafe_db < backup.sql
# I used sudo to execute this code
```

Added backend part ci/cd.

[pugbug.fun](http://pugbug.fun) displays last ui and node functionality, including socket, but first I need to setup .env

Adding privilege to david user

```jsx
GRANT ALL PRIVILEGES ON church_cafe_db.* TO 'david'@'localhost';
FLUSH PRIVILEGES;
```

ALTER USER 'david'@'localhost' IDENTIFIED BY 'pugOk911';

FLUSH PRIVILEGES;