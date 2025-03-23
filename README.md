# Laravel CORS Configuration

This guide explains how to configure CORS (Cross-Origin Resource Sharing) in a Laravel 11 application to allow only a specific frontend, such as a React app, to access your backend.

## 1. Publish CORS Configuration File
Laravel 11 does not include a `config/cors.php` file by default. To generate it, run the following command:

```bash
php artisan config:publish cors
```

## 2. Update CORS Configuration
Once generated, edit `config/cors.php` and update the settings to allow only your frontend's URL:

```php
return [
    'paths' => ['api/*', 'sanctum/csrf-cookie'], // Define routes where CORS applies
    'allowed_methods' => ['*'], // Allow all HTTP methods
    'allowed_origins' => ['http://localhost:3000'], // Change this to your frontend URL
    'allowed_origins_patterns' => [],
    'allowed_headers' => ['*'], // Allow all headers
    'exposed_headers' => [],
    'max_age' => 0,
    'supports_credentials' => true, // Enable if using authentication (cookies, JWT)
];
```

## 3. Clear Config Cache
Run the following command to apply changes:

```bash
php artisan config:clear
```

## 4. Restart Laravel Server
Restart your Laravel development server:

```bash
php artisan serve
```

Now, only your specified frontend (e.g., `http://localhost:3000`) can make API requests to your Laravel 11 backend. 🚀
