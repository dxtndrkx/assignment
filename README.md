npm ## Run Locally

Clone the project

```bash
  git clone https://dredsoft-admin@bitbucket.org/dredsoft/ecommerce.git
```

Go to the project directory

```bash
  cd eCommerce
```

Install dependencies

```bash
  npm install

  or

  npm install react-material-ui-carousel --save --legacy-peer-deps
```

Start the server

```bash
  npm start
```

The server should now be running. You can access the application by opening a web browser and entering the following URL:

```bash
  http://localhost:3000
```

## How This Assignment Was Solved

1. **Product API Endpoints:**

   - The main product endpoints were already present in the codebase.
   - I updated the `getAllProducts` function in `api/controllers/productController.js` to support filtering products by category name using a query parameter (e.g., `/api/v1/products?category=Apparel`).

2. **API Documentation:**

   - Added a section in this `README.md` with details about the API endpoints, tech stack, how to run the project, and sample curl requests.

3. **Postman Collection:**
   - Created a Postman collection file (`api/ProductAPI.postman_collection.json`) so you can easily test all the Product API endpoints.

---

## Product API Documentation

### Tech Stack

- **Backend:** Node.js, Express.js, MongoDB (Mongoose)

### How to Run the Project

1. Copy `api/config/config.env.example` to `api/config/config.env` and fill in your environment variables (MongoDB, Cloudinary, etc).
2. Install dependencies:
   ```bash
   cd api
   npm install
   ```
3. Start the backend server:
   ```bash
   npm start
   ```
   The server will run on the port specified in your `.env` (default: 4000 or 4001).

---

## Product API Endpoints

### 1. Get All Products

- **Endpoint:** `GET /api/v1/products`
- **Description:** Returns a list of all products. Supports filtering by category via query string.
- **Query Parameters:**
  - `category` (optional): Filter by category name (e.g., `?category=Apparel`)
- **Sample Request:**
  ```bash
  curl http://localhost:4001/api/v1/products
  curl http://localhost:4001/api/v1/products?category=Apparel
  ```

### 2. Get Product by ID

- **Endpoint:** `GET /api/v1/product/:id`
- **Description:** Returns a single product by its MongoDB ID.
- **Sample Request:**
  ```bash
  curl http://localhost:4001/api/v1/product/60f6c0b5e1d2c8a1b8e4d123
  ```

### 3. Create a New Product (Admin Only)

- **Endpoint:** `POST /api/v1/admin/product/new`
- **Description:** Adds a new product. Requires authentication and admin role. Data validation is performed.
- **Sample Request:**
  ```bash
  curl -X POST http://localhost:4001/api/v1/admin/product/new \
    -H "Content-Type: application/json" \
    -d '{
      "name": "T-Shirt",
      "description": "A cool t-shirt",
      "highlights": ["100% cotton", "Unisex"],
      "specifications": [{"title": "Material", "description": "Cotton"}],
      "price": 20,
      "cuttedPrice": 25,
      "images": ["<base64 or url>"],
      "brandname": "BrandX",
      "logo": "<base64 or url>",
      "category": "Apparel",
      "stock": 100
    }'
  ```

---

## Notes

- All endpoints are prefixed with `/api/v1`.
- For POST/PUT/DELETE endpoints, authentication and admin role are required.
- For more details, see the code in `api/routes/productRoute.js` and `api/controllers/productController.js`.
