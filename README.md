# Meaad Storefront Backend Project

Create Database that compose into three table:

- Users
- Orsers
- Products

users(firstname,lastname,password)
orders(product id,quantity,user id,status)
products(name,price,category)

# Database Connection

psql -h localhost -U postgres -p 5432
CREATE USER test_user WITH PASSWORD 'meaad123';
CREATE DATABASE shopping;
\c shopping
GRANT ALL PRIVILEGES ON DATABASE shopping TO test_user;

# Env Variables

ENV=dev

PG_HOST_DEV=localhost
PG_DB_DEV = shopping
PG_DB_TEST = shopping_test
PG_USER_DEV = test_user
PG_PASSWORD_DEV = meaad123
PG_PORT_DEV = 5432

SALT_ROUNDS=10
TOKEN_SECRET=Meaad-Secret-Token
BCRYPT_PASSWORD=Meaad-Secret-Password

# User Actions

the user can create order and add remove update edit and delete products
from this order

A user with authenticate can:
create and delete products from database products
edit existing users
create and delete users
get all the current orders through user

The user is authenticated to a jwt token

# API

(PRODUCTS)

- Index(/products)[GET]
- show(/products/:id)[GET]
- create(/products)[POST]
- Delete(/products/:id)[DELETE]

(USERS)

- Index(/users)[GET]
- show(/users/:id)[GET]
- create(/users)[POST]
- Delete(/users/:id)[DELETE]
- Authenticate(/users/authenticate)[POST]

(ORDERS)

- Index(/orders)[GET]
- show(/orders/:id)[GET]
- create(/orders)[POST]
- Delete(/orders/:id)[DELETE]
- Index the product that associated with products(/orders/products)[GET]
- Add the product to the order(/orders/:id/products)[POST]
- Edit the product from order(/orders/:id/products)[get]
- Update the quantity to order(/orders/:id/products/:product_id)[patch]
- Remoce the product from the order(/orders/:id/products/:product_id)[delete]

# Scripts

(Run Server)
[npm run watch] [npm run start]
(Build the application)
[npm run watch ]
(Build typescript and run all tests)
[npm run start]
(run jasmine test)
[npm run jasmine]
(Run eslint)
[npm run eslint]
[npm run eslint:fix to apply fixes]

(Run prettier)
[npm run prettier]
[npm run prettier:fix to apply fixes]
