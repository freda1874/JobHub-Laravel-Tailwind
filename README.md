<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>
 

# ** Project Intro**

This project is a Laravel-based application designed with **MySQL**, **TailwindCSS**, and essential Laravel features such as **Blade templates**, **layouts**, **components**, and **partials**. It includes **user registration**, **authentication**, **authorization**, and a **user-to-listings relationship**.
 
---

## **Usage**

![lar1](https://github.com/user-attachments/assets/9a351425-d5c2-4284-9800-d153b2b43f7b)
### **Registration and Login**
- Access the registration page as a guest to create a new account.
- Login to manage your listings.

![lar4](https://github.com/user-attachments/assets/dae6dceb-593b-4786-9193-62a594b385ce)

### **Manage Listings**
- Create, update, and delete listings.
- View only the listings created by the logged-in user.
![lar3](https://github.com/user-attachments/assets/0655fae0-251e-453a-907a-149736ca6d0e)
### **Protected Routes**
- Only authenticated users can access listing management.
- Guests are redirected to the login page if they attempt to manage listings.
 

---

## **Features**

### **1. Frontend Design with TailwindCSS**
- Tailored responsive design using **TailwindCSS**.
- Consistent structure built with **Blade templates**, **layouts**, **components**, and **partials**.

### **2. Routes**
- Middleware applied to protect specific routes:
  - **Authenticated Middleware**: Ensures only logged-in users can manage listings.
  - **Guest Middleware**: Restricts access to the registration page for authenticated users.

### **3. ORM with Eloquent**
- use of Laravel's **Eloquent ORM** for database interactions.
- Includes **relationships**:
  - `User` has many `Listings`.
  - Each listing belongs to a user.

### **4. Controllers**
- Controllers used to handle business logic:
  - **UserController**: Manages user registration and authentication.
  - **ListingController**: Handles CRUD operations for listings.

### **5. User Registration and Authentication**
- Secure user registration with password encryption using **bcrypt**.
- Authentication implemented using Laravel's **auth()** helper.
- Flash messages for user feedback (e.g., successful login/logout).

### **6. User Listing Relationship**
- **Manage Listings**: Users can only manage the listings they created.
- Listing deletion includes cascading functionality to remove related records securely.
 
## **Setup Instructions**

### **1. Clone the Repository**
```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

### **2. Install Dependencies**
```bash
composer install
npm install
```

### **3. Configure the Environment**
- Copy `.env.example` to `.env`:
  ```bash
  cp .env.example .env
  ```
- Update the `.env` file with your database credentials:
  ```env
  DB_CONNECTION=mysql
  DB_HOST=127.0.0.1
  DB_PORT=3306
  DB_DATABASE=your_database
  DB_USERNAME=your_username
  DB_PASSWORD=your_password
  ```

### **4. Run Migrations and Seed the Database**
```bash
php artisan migrate --seed
```

### **5. Link Storage**
```bash
php artisan storage:link
```

### **6. Serve the Application**
```bash
php artisan serve
```
Access the application at [http://127.0.0.1:8000](http://127.0.0.1:8000).

 
---

## **Key Code Snippets**

### **User-to-Listings Relationship**
**User Model**:
```php
public function listings()
{
    return $this->hasMany(Listing::class, 'user_id');
}
```

**Listing Model**:
```php
public function user()
{
    return $this->belongsTo(User::class, 'user_id');
}
```

### **Middleware Example**
**Route Protection**:
```php
Route::get('/listings/create', [ListingController::class, 'create'])->middleware('auth');
Route::get('/register', [UserController::class, 'create'])->middleware('guest');
```

---

## **Credit**
 I followed this tutorial for this project : https://www.youtube.com/watch?v=MYyJ4PuL4pY 
 
