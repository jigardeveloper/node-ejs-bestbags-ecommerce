## Table of contents

- [Introduction](#introduction)
- [Features](#features)
- [Database Models](#database)
- [Color Palette](#colors)

## Introduction
A virtual ecommerce website using Node js, Express js, and Mongoose.

## Features
The application displays a virtual bags store that contains virtual products and contact information.

Users can do the following:

- Create an account, login or logout
- Browse available products added by the admin
- Add products to the shopping cart
- Delete products from the shopping cart
- Display the shopping cart
- To checkout, a user must be logged in
- Checkout information is processed using stripe and the payment is send to the admin
- The profile contains all the orders a user has made

Admins can do the following:

- Login or logout to the admin panel
- View all the information stored in the database. They can view/add/edit/delete orders, users, products and categories. The cart model cannot be modified by an admin because a cart is either modified by the logged in user before the purchase or deleted after the purchase.

## Database

All the models can be found in the models directory created using mongoose.

### User Schema:

- username (String)
- email (String)
- password (String)

### Category Schema:

- title (String)
- slug (String)

### Product Schema:

- productCode (String)
- title (String)
- imagePath (String)
- description (String)
- price (Number)
- category (ObjectId - a reference to the category schema)
- manufacturer (String)
- available (Boolean)
- createdAt (Date)

### Cart Schema:

- items: an array of objects, each object contains: <br>
  ~ productId (ObjectId - a reference to the product schema) <br>
  ~ qty (Number) <br>
  ~ price (Number) <br>
  ~ title (String) <br>
  ~ productCode (Number) <br>
- totalQty (Number)
- totalCost (Number)
- user (ObjectId - a reference to the user schema)
- createdAt
  <br><br>
  \*\*The reason for including the title, price, and productCode again in the items object is AdminBro. If we are to write our own admin interface, we can remove them and instead populate a product field using the product id. However, AdminBro doesn't populate deep levels, so we had to repeat these fields in the items array in order to display them in the admin panel.

### Order Schema:

- user (ObjectId - a reference to the user schema)
- cart (instead of a reference, we had to structure an object identical to the cart schema because of AdminBro, so we can display the cart's contents in the admin interface under each order)
- address (String)
- paymentId (String)
- createdAt (Date)
- Delivered (Boolean)

## Colors

Below is the color palette used in this application:

- ![#478ba2](https://via.placeholder.com/15/478ba2/000000?text=+) `#478ba2`
- ![#b9d4db](https://via.placeholder.com/15/b9d4db/000000?text=+) `#b9d4db`
- ![#e9765b](https://via.placeholder.com/15/e9765b/000000?text=+) `#e9765b`
- ![#f2a490](https://via.placeholder.com/15/f2a490/000000?text=+) `#f2a490`
- ![#de5b6d](https://via.placeholder.com/15/de5b6d/000000?text=+) `#de5b6d`
- ![#18a558](https://via.placeholder.com/15/18a558/000000?text=+) `#18a558`
- ![#f9f7f4](https://via.placeholder.com/15/f9f7f4/000000?text=+) `#f9f7f4`
- ![#202020](https://via.placeholder.com/15/202020/000000?text=+) `#202020`
- ![#474747](https://via.placeholder.com/15/474747/000000?text=+) `#474747`
