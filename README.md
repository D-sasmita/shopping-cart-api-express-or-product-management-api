# shopping-cart-api-express-or-product-management-api
RESTful API for managing product information in a shopping cart application
# Shopping Cart Product API

This is a RESTful API built with Express.js and Node.js to manage product information for a shopping cart application. It provides Create, Read, Update, and Delete (CRUD) operations for products. The API uses MongoDB for data persistence.

## Technologies Used

* Node.js
* Express.js
* Mongoose (for MongoDB)
* cors (for handling Cross-Origin Resource Sharing)

## Setup Instructions

1.  **Clone the repository:**
    ```bash
    git clone [YOUR_REPOSITORY_URL]
    cd [YOUR_REPOSITORY_DIRECTORY]
    ```
    *(Replace `[YOUR_REPOSITORY_URL]` and `[YOUR_REPOSITORY_DIRECTORY]` with your actual repository details)*

2.  **Install dependencies:**
    ```bash
    npm install
    # or
    yarn install
    ```

3.  **Ensure MongoDB is running:**
    Make sure you have MongoDB installed and running on your local machine (typically at `mongodb://127.0.0.1:27017`).

4.  **Start the server:**
    ```bash
    npm start
    # or
    node app.js
    # or
    nodemon app.js
    ```
    The server will start and listen on port `5050`. You should see the message `Server running on http://localhost:5050` and `Connected to MongoDB ✅` in your console.

## API Endpoints

The following endpoints are available for managing products:

* **POST /api/products**
    * Description: Creates a new product.
    * Request Body (JSON):
        ```json
        {
          "name": "Product Name",
          "description": "Product Description",
          "price": 19.99,
          "/* Add other product properties as needed */"
        }
        ```
    * Response Body (Success - 201 Created):
        ```json
        {
          "_id": "someGeneratedProductId",
          "name": "Product Name",
          "description": "Product Description",
          "price": 19.99,
          "__v": 0,
          "/* Other product properties */"
        }
        ```
    * Response Body (Error - 400 Bad Request):
        ```json
        {
          "error": "Validation error message or other error details"
        }
        ```

* **GET /api/products**
    * Description: Retrieves a list of all products.
    * Response Body (Success - 200 OK):
        ```json
        [
          {
            "_id": "productId1",
            "name": "Product A",
            "price": 25.00,
            "/* Other properties */"
          },
          {
            "_id": "productId2",
            "name": "Product B",
            "price": 12.50,
            "/* Other properties */"
          },
          // ... more products
        ]
        ```
    * Response Body (Error - 500 Internal Server Error):
        ```json
        {
          "error": "Error message from the server"
        }
        ```

* **GET /api/products/:id**
    * Description: Retrieves a specific product by its ID.
    * Path Parameter: `id` (the unique identifier of the product).
    * Response Body (Success - 200 OK):
        ```json
        {
          "_id": "requestedProductId",
          "name": "Specific Product",
          "price": 30.00,
          "/* Other properties */"
        }
        ```
    * Response Body (Error - 404 Not Found):
        ```json
        {
          "error": "Product not found"
        }
        ```

* **PUT /api/products/:id**
    * Description: Updates an existing product.
    * Path Parameter: `id` (the ID of the product to update).
    * Request Body (JSON):
        ```json
        {
          "name": "Updated Product Name",
          "price": 29.99,
          "/* Include any properties you want to update */"
        }
        ```
    * Response Body (Success - 200 OK):
        ```json
        {
          "_id": "updatedProductId",
          "name": "Updated Product Name",
          "price": 29.99,
          "/* Other updated properties */"
        }
        ```
    * Response Body (Error - 400 Bad Request):
        ```json
        {
          "error": "Validation error message or other error details"
        }
        ```

* **DELETE /api/products/:id**
    * Description: Deletes a specific product by its ID.
    * Path Parameter: `id` (the ID of the product to delete).
    * Response Body (Success - 200 OK):
        ```json
        {
          "message": "Product deleted"
        }
        ```
    * Response Body (Error - 400 Bad Request):
        ```json
        {
          "error": "Error message indicating deletion failure"
        }
        ```
