# Laravel Sanctum Authentication

##  Objective
Secure API endpoints using token-based authentication with Laravel Sanctum.

## Approach Used

1. **Installed Laravel Sanctum**:
   - Added Sanctum to the project via Composer.
   -  Created the `api.php` file using composer install and ran the required database migrations to create the `personal_access_tokens` table.

2. **Configured Middleware**:
   - Updated the `api` middleware group to include Sanctum’s stateful middleware for proper token handling.

3. **Built Authentication Endpoints**:
   - Created a custom `AuthController` to handle login and logout functionality.
   - On login, the controller validates credentials and issues a personal access token.
   - On logout, it revokes the current token using Laravel’s built-in methods.

4. **Protected API Routes**:
   - Grouped relevant routes (e.g., property-related endpoints) under the `auth:sanctum` middleware to restrict access to authenticated users only.

5. **Tested with Postman**:
   - Used Postman to verify login, logout, token usage, and access to protected routes.

##  Setup Instructions

1. **Install Sanctum:**
   ```bash
   composer require laravel/sanctum
    ```
2. Run Migrations
```bash
php artisan migrate
```
## Authentication API Endpoints

| Method | Endpoint           | Description                               | Authentication Required |
|--------|--------------------|-------------------------------------------|--------------------------|
| POST   | `/api/login`       | Logs in a user and returns a token        |  No                    |
| POST   | `/api/logout`      | Logs out the user and revokes token       |  Yes      
| POST   | `/api/posts`       |Creates new Post     |Yes             |
| GET    | `/api/posts`  | Lists all posts                      |  Yes                   |
| POST   | `/api/register`  | Creates a new user                   | Yes
| GET   | `/api/posts/{post}` | Get a specific post         |  Yes                   |
| PUT   | `/api/posts/{post}` | Updates a specific post         |  Yes                   |
| DELETE | `/api/posts/{post}` | Deletes a specific post         |  Yes  

## Testing Using Postman

1. Start the server
```bash
php artisan migrate
```
2. Add an header with key `Accept` and value as `application/json`

3. Login:

- Send a POST request to /api/login with JSON body:
```json
{
  "email": "user@example.com",
  "password": "your_password"
}
```
4. Receive Token:

- The response will include a token. Copy it.

5. Access Protected Routes:

- Under the Authorizaation tab, select `Bearer Token`as auth type and put the copied token in the dialog box.

6. Logout:

- Send a POST request to /api/logout with the same Bearer token.

---

##  Conclusion

This implementation demonstrates a secure and practical approach to API authentication using Laravel Sanctum. It ensures that sensitive endpoints are protected and accessible only to authenticated users, providing a solid foundation for building secure Laravel applications.
