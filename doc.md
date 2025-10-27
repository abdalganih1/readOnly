
# API Documentation

This document provides documentation for two APIs: a procedural PHP API and a Laravel-based API.

## Procedural PHP API

This API is built with procedural PHP files.

### Authentication

#### Register

*   **Method:** `POST`
*   **URL:** `/register.php`
*   **Parameters:**
    *   `name` (string, required): The user's name.
    *   `email` (string, required): The user's email.
    *   `password` (string, required): The user's password.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "User registered successfully"
    }
    ```

#### Login

*   **Method:** `POST`
*   **URL:** `/login.php`
*   **Parameters:**
    *   `email` (string, required): The user's email.
    *   `password` (string, required): The user's password.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Login successful",
        "user": {
            "id": 1,
            "name": "John Doe",
            "email": "john.doe@example.com"
        }
    }
    ```

#### Forget Password

*   **Method:** `POST`
*   **URL:** `/forget_password.php`
*   **Parameters:**
    *   `email` (string, required): The user's email.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Reset code sent to your email"
    }
    ```

#### Verify Reset Code

*   **Method:** `POST`
*   **URL:** `/verify_reset_code.php`
*   **Parameters:**
    *   `email` (string, required): The user's email.
    *   `reset_code` (string, required): The 6-digit reset code.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Reset code verified"
    }
    ```

#### Reset Password

*   **Method:** `POST`
*   **URL:** `/reset_password.php`
*   **Parameters:**
    *   `email` (string, required): The user's email.
    *   `reset_code` (string, required): The 6-digit reset code.
    *   `new_password` (string, required): The new password.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Password updated successfully"
    }
    ```

### Categories

#### Add Category

*   **Method:** `POST`
*   **URL:** `/add_category.php`
*   **Parameters:**
    *   `name` (string, required): The name of the category.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Category added successfully",
        "category_id": 1
    }
    ```

#### Get Categories

*   **Method:** `GET`
*   **URL:** `/get_categories.php`
*   **Response:**
    ```json
    {
        "success": true,
        "categories": [
            {
                "id": 1,
                "name": "Category 1"
            },
            {
                "id": 2,
                "name": "Category 2"
            }
        ]
    }
    ```

#### Update Category

*   **Method:** `POST`
*   **URL:** `/update_category.php`
*   **Parameters:**
    *   `id` (integer, required): The ID of the category to update.
    *   `name` (string, required): The new name of the category.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Category updated successfully"
    }
    ```

#### Delete Category

*   **Method:** `POST`
*   **URL:** `/delete_category.php`
*   **Parameters:**
    *   `id` (integer, required): The ID of the category to delete.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Category deleted successfully"
    }
    ```

### Products

#### Add Product

*   **Method:** `POST`
*   **URL:** `/add_product.php`
*   **Parameters:**
    *   `category_id` (integer, required): The ID of the category.
    *   `name` (string, required): The name of the product.
    *   `price` (float, required): The price of the product.
    *   `image` (string, required): The URL of the product image.
    *   `colors` (array, required): An array of color IDs.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Product added successfully",
        "product_id": 1
    }
    ```

#### Get Products

*   **Method:** `GET`
*   **URL:** `/get_products.php`
*   **Query Parameters:**
    *   `limit` (integer, optional): The number of products to return. Default is 10.
    *   `offset` (integer, optional): The offset for pagination. Default is 0.
*   **Response:**
    ```json
    {
        "success": true,
        "products": [
            {
                "id": 1,
                "name": "Product 1",
                "price": "10.00",
                "image": "image.jpg",
                "colors": "Red, Blue"
            }
        ]
    }
    ```

#### Get Products by Category

*   **Method:** `GET`
*   **URL:** `/get_products_by_category.php`
*   **Query Parameters:**
    *   `category_id` (integer, required): The ID of the category.
*   **Response:**
    ```json
    {
        "success": true,
        "products": [
            {
                "id": 1,
                "name": "Product 1",
                "price": "10.00",
                "image": "image.jpg",
                "colors": "Red, Blue"
            }
        ]
    }
    ```

#### Update Product

*   **Method:** `POST`
*   **URL:** `/update_product.php`
*   **Parameters:**
    *   `id` (integer, required): The ID of the product to update.
    *   `category_id` (integer, required): The ID of the category.
    *   `name` (string, required): The name of the product.
    *   `price` (float, required): The price of the product.
    *   `image` (string, required): The URL of the product image.
    *   `colors` (array, required): An array of color IDs.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Product updated successfully"
    }
    ```

#### Delete Product

*   **Method:** `POST`
*   **URL:** `/delete_product.php`
*   **Parameters:**
    *   `id` (integer, required): The ID of the product to delete.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Product deleted successfully"
    }
    ```

#### Search Products

*   **Method:** `GET`
*   **URL:** `/search_products.php`
*   **Query Parameters:**
    *   `q` (string, optional): The search term.
    *   `category_id` (integer, optional): The ID of the category.
    *   `color_id` (integer, optional): The ID of the color.
    *   `min_price` (float, optional): The minimum price.
    *   `max_price` (float, optional): The maximum price.
*   **Response:**
    ```json
    {
        "success": true,
        "products": [
            {
                "id": 1,
                "name": "Product 1",
                "price": "10.00",
                "image": "image.jpg",
                "colors": "Red, Blue"
            }
        ]
    }
    ```

### Bookings

#### Create Booking

*   **Method:** `POST`
*   **URL:** `/create_booking.php`
*   **Parameters:**
    *   `user_id` (integer, required): The ID of the user.
    *   `products` (array, required): An array of product objects, each with `product_id` and `quantity`.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Booking created successfully",
        "booking_id": 1
    }
    ```

#### Get User Bookings

*   **Method:** `GET`
*   **URL:** `/get_user_bookings.php`
*   **Query Parameters:**
    *   `user_id` (integer, required): The ID of the user.
*   **Response:**
    ```json
    {
        "success": true,
        "bookings": [
            {
                "booking_id": 1,
                "booking_date": "2025-10-27 10:00:00",
                "status": "pending",
                "product_name": "Product 1",
                "quantity": 2
            }
        ]
    }
    ```

---

## Laravel API

This API is built with the Laravel framework.

### Authentication

#### Register

*   **Method:** `POST`
*   **URL:** `/api/register`
*   **Parameters:**
    *   `name` (string, required): The user's name.
    *   `email` (string, required): The user's email.
    *   `password` (string, required): The user's password.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "User registered successfully"
    }
    ```

#### Login

*   **Method:** `POST`
*   **URL:** `/api/login`
*   **Parameters:**
    *   `email` (string, required): The user's email.
    *   `password` (string, required): The user's password.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Login successful",
        "user": {
            "id": 1,
            "name": "John Doe",
            "email": "john.doe@example.com",
            "email_verified_at": null,
            "created_at": "2025-10-27T10:00:00.000000Z",
            "updated_at": "2025-10-27T10:00:00.000000Z"
        }
    }
    ```

#### Forget Password

*   **Method:** `POST`
*   **URL:** `/api/forget-password`
*   **Parameters:**
    *   `email` (string, required): The user's email.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Reset code sent to your email",
        "reset_code": "123456"
    }
    ```

#### Verify Reset Code

*   **Method:** `POST`
*   **URL:** `/api/verify-reset-code`
*   **Parameters:**
    *   `email` (string, required): The user's email.
    *   `reset_code` (string, required): The 6-digit reset code.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Reset code verified"
    }
    ```

#### Reset Password

*   **Method:** `POST`
*   **URL:** `/api/reset-password`
*   **Parameters:**
    *   `email` (string, required): The user's email.
    *   `reset_code` (string, required): The 6-digit reset code.
    *   `new_password` (string, required): The new password.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Password updated successfully"
    }
    ```

### Categories

#### Get All Categories

*   **Method:** `GET`
*   **URL:** `/api/categories`
*   **Response:**
    ```json
    {
        "success": true,
        "categories": [
            {
                "id": 1,
                "name": "Category 1",
                "created_at": "2025-10-27T10:00:00.000000Z",
                "updated_at": "2025-10-27T10:00:00.000000Z"
            }
        ]
    }
    ```

#### Get Category

*   **Method:** `GET`
*   **URL:** `/api/categories/{id}`
*   **Response:**
    ```json
    {
        "success": true,
        "category": {
            "id": 1,
            "name": "Category 1",
            "created_at": "2025-10-27T10:00:00.000000Z",
            "updated_at": "2025-10-27T10:00:00.000000Z"
        }
    }
    ```

#### Add Category

*   **Method:** `POST`
*   **URL:** `/api/categories`
*   **Parameters:**
    *   `name` (string, required): The name of the category.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Category added successfully",
        "category_id": 1
    }
    ```

#### Update Category

*   **Method:** `PUT/PATCH`
*   **URL:** `/api/categories/{id}`
*   **Parameters:**
    *   `name` (string, required): The new name of the category.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Category updated successfully"
    }
    ```

#### Delete Category

*   **Method:** `DELETE`
*   **URL:** `/api/categories/{id}`
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Category deleted successfully"
    }
    ```

### Products

#### Get All Products

*   **Method:** `GET`
*   **URL:** `/api/products`
*   **Query Parameters:**
    *   `limit` (integer, optional): The number of products to return. Default is 10.
    *   `offset` (integer, optional): The offset for pagination. Default is 0.
*   **Response:**
    ```json
    {
        "success": true,
        "products": [
            {
                "id": 1,
                "name": "Product 1",
                "price": "10.00",
                "image": "image.jpg",
                "colors": "Red, Blue"
            }
        ]
    }
    ```

#### Get Product

*   **Method:** `GET`
*   **URL:** `/api/products/{id}`
*   **Response:**
    ```json
    {
        "success": true,
        "product": {
            "id": 1,
            "category_id": 1,
            "name": "Product 1",
            "price": "10.00",
            "image": "image.jpg",
            "created_at": "2025-10-27T10:00:00.000000Z",
            "updated_at": "2025-10-27T10:00:00.000000Z",
            "category": {
                "id": 1,
                "name": "Category 1",
                "created_at": "2025-10-27T10:00:00.000000Z",
                "updated_at": "2025-10-27T10:00:00.000000Z"
            },
            "colors": [
                {
                    "id": 1,
                    "name": "Red",
                    "created_at": "2025-10-27T10:00:00.000000Z",
                    "updated_at": "2025-10-27T10:00:00.000000Z",
                    "pivot": {
                        "product_id": 1,
                        "color_id": 1
                    }
                }
            ]
        }
    }
    ```

#### Get Products by Category

*   **Method:** `GET`
*   **URL:** `/api/products/category/{categoryId}`
*   **Response:**
    ```json
    {
        "success": true,
        "products": [
            {
                "id": 1,
                "name": "Product 1",
                "price": "10.00",
                "image": "image.jpg",
                "colors": "Red, Blue"
            }
        ]
    }
    ```

#### Add Product

*   **Method:** `POST`
*   **URL:** `/api/products`
*   **Parameters:**
    *   `category_id` (integer, required): The ID of the category.
    *   `name` (string, required): The name of the product.
    *   `price` (float, required): The price of the product.
    *   `image` (string, required): The URL of the product image.
    *   `colors` (array, required): An array of color IDs.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Product added successfully",
        "product_id": 1
    }
    ```

#### Update Product

*   **Method:** `PUT/PATCH`
*   **URL:** `/api/products/{id}`
*   **Parameters:**
    *   `category_id` (integer, optional): The ID of the category.
    *   `name` (string, optional): The name of the product.
    *   `price` (float, optional): The price of the product.
    *   `image` (string, optional): The URL of the product image.
    *   `colors` (array, optional): An array of color IDs.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Product updated successfully"
    }
    ```

#### Delete Product

*   **Method:** `DELETE`
*   **URL:** `/api/products/{id}`
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Product deleted successfully"
    }
    ```

#### Search Products

*   **Method:** `GET`
*   **URL:** `/api/search/products`
*   **Query Parameters:**
    *   `q` (string, optional): The search term.
    *   `category_id` (integer, optional): The ID of the category.
    *   `color_id` (integer, optional): The ID of the color.
    *   `min_price` (float, optional): The minimum price.
    *   `max_price` (float, optional): The maximum price.
*   **Response:**
    ```json
    {
        "success": true,
        "products": [
            {
                "id": 1,
                "name": "Product 1",
                "price": "10.00",
                "image": "image.jpg",
                "colors": "Red, Blue"
            }
        ]
    }
    ```

### Bookings

#### Create Booking

*   **Method:** `POST`
*   **URL:** `/api/bookings`
*   **Authentication:** Required.
*   **Parameters:**
    *   `user_id` (integer, required): The ID of the user.
    *   `products` (array, required): An array of product objects, each with `product_id` and `quantity`.
*   **Response:**
    ```json
    {
        "success": true,
        "message": "Booking created successfully",
        "booking_id": 1
    }
    ```

#### Get User Bookings

*   **Method:** `GET`
*   **URL:** `/api/user-bookings/{userId}`
*   **Response:**
    ```json
    {
        "success": true,
        "bookings": [
            {
                "booking_id": 1,
                "booking_date": "2025-10-27T10:00:00.000000Z",
                "status": "pending",
                "products": [
                    {
                        "product_name": "Product 1",
                        "quantity": 2
                    }
                ]
            }
        ]
    }
    ```
