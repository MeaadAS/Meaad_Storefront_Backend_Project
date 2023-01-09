# API Requirements

The company stakeholders want to create an online storefront to showcase their great product ideas. Users need to be able to browse an index of all products, see the specifics of a single product, and add products to an order that they can view in a cart page. You have been tasked with building the API that will support this application, and your coworker is building the frontend.

These are the notes from a meeting with the frontend developer that describe what endpoints the API needs to supply, as well as data shapes the frontend and backend have agreed meet the requirements of the application.

# API Requirements

The company stakeholders want to create an online storefront to showcase their great product ideas. Users need to be able to browse an index of all products, see the specifics of a single product, and add products to an order that they can view in a cart page. You have been tasked with building the API that will support this application, and your coworker is building the frontend.

These are the notes from a meeting with the frontend developer that describe what endpoints the API needs to supply, as well as data shapes the frontend and backend have agreed meet the requirements of the application.

## API Endpoints

#### Products

- Index:'/products'[GET]
- Show:'/product/:id'[GET]
- Create [token required] '/product' [POST]
- update product [token required] '/product' [PUT]
- delete product [token required] '/product' [DELETE]

#### Users

- Index [token required] '/users' [GET]
- Show [token required] '/user/:id' [GET]
- Create [token required] '/user' [POST]
- update user [token required] '/user' [PUT]
- delete user [token required] '/user' [DELETE]

#### Orders

- Index [token required] '/orders' [GET]
- Show [token required] '/order/:id' [GET]
- Create [token required] '/order' [POST]
- update user [token required] '/order' [PUT]
- delete user [token required] '/order' [DELETE]
- Current Order by user (args: user id)[token required]

#### Order_products

- addProduct [token required] '/orders/products' [POST]
- indexProduct [token required] '/orders/products' [GET]
- editProduct [token required] '/orders/:id/products' [GET]
- updateProduct [token required] '/orders/:id/products/:product_id' [PATCH]
- removeProduct [token required] '/orders/products' [DELETE]

## Data Shapes

### Databases informations

{
"dev": {
"driver": "pg",
"user": {"ENV": "PG_USER_DEV"},
"password": {"ENV": "PG_PASSWORD_DEV"},
"host": {"ENV": "PG_HOST_DEV"},
"database": {"ENV": "PG_DB_DEV"}
},
"test": {
"driver": "pg",
"user": {"ENV": "PG_USER_DEV"},
"password": {"ENV": "PG_PASSWORD_DEV"},
"host": {"ENV": "PG_HOST_TEST"},
"database": {"ENV": "PG_DB_TEST"}
}
}

#### Product

- id
- name
- price
- category
  CREATE TABLE products(
  id SERIAL PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  price integer NOT NULL,
  category VARCHAR(100)
  );

#### User

- id
- firstName
- lastName
- username
- password_digest

CREATE TABLE users
(
id SERIAL PRIMARY KEY,
firstname VARCHAR(255),
lastname VARCHAR(255),
username VARCHAR(255),
password_digest VARCHAR(1024)
);

#### Orders

- id
- id of each product in the order
- quantity of each product in the order
- user_id
- status of order
  CREATE TABLE orders (
  id SERIAL PRIMARY KEY,
  status VARCHAR(100) NOT NULL,
  user_id INT REFERENCES users(id)
  );
  CREATE TABLE order_products(
  id SERIAL PRIMARY KEY,
  quantity integer NOT NULL,
  order_id bigint REFERENCES orders(id),
  product_id bigint REFERENCES products(id)
  );
