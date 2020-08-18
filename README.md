# OnlineShop-MR-Project (Cucci)

> Creating E-Commerce Application for Customers - 
This is an application that works as a digital store for our Cucci Viatu products.
This app has :
* RESTful endpoints for CRUD operation
* JSON formatted response

`environment variables:`
>> file .env values:
> - PORT=
> - SECRET_KEY=
> - CLIENT_ID=

`link deploy:`
> - heroku : https://queen-ecommerce.herokuapp.com
> - firebase :  https://cucciofficial-29e18.web.app (Client Site)
> - firebase : https://cucciofficialcms.web.app (Admin Site)

`registered account:`
> - email: raka@mail.com | password: asdasdasd (Customer)
> - email: admin@mail.com | password: 1234 (Admin) 

`fitur tambahan:`
> - _checkout feature_
> - _email confirm after checkout_


`Cucci Viatu Application for Admin Guides:`
> - Cucci Viatu & Logo - this button automatically guide you to our home page with the entire collections
> - Men - this button automatically guide you to our Men page
> - Women - this button automatically guide you to our Women page
> - Cart (Bag icon) - this button allows you check your list of selected product(s) to buy in the cart page.
> - Dropdown Logout - this button allows you to log yourself out from the application. This will automatically route you back to our Login page.
> - Login - this button will guide you to our login page. logging out is necessary when you are logged in
> - Register - this button will guide you to our register page. logging out is necessary when you are logged in
> - Buy - this button will guide you to the selected product detail in the details page. loggin in is required
> - Add To Cart - this button will automatically add an amount (demand) of the selected product to the cart list. it comes with a confirmation modal that will guide you to the cart page or the home page.
> - Minus(-) - this button will allow you to subtract an amount of your demand
> - Plus(+) - this button will allow you to add an amount of your demand
> - Bin icon - this button will allow you to remove your selected product from your cart list
> - Confirm payment - this button will guide you to a modal of your payment detail complete with Cucci Viatu transfer accounts. It comes with a confirmation modal that will allows you to checkout from store and eliminate all your cart list as the stocks being calculated. Another is to cancel your checkout.

&nbsp;
## RESTful endpoints
---
### Global Responses
_Response (500 - Unknown error)_
> This endpoint should always return response below,
```
{ "message": "Interval Server Error" }
```

---

### POST /register

> Create a new user account

_Request Header_
```
  no need
```
_Request Body_
```
{
  email: <email input>,
  password: <email password>
}
```
_Response (201)_
```
{
    "id": <created id>,
    "email": <created email>,
    "password": <hashed password>,
    "status": "Admin",
    "updatedAt": "2020-05-05T08:39:37.867Z",
    "createdAt": "2020-05-05T08:39:37.867Z"
}
```
_Response (400 - Bad Request)_
```
{ message: 'Email already exist' }
```

---
### POST /login

> Create access_token to confirm selected account based on registered accounts

_Request Header_
```
  no need
```
_Request Body_
```
{
  email: <email input>,
  password: <email password>
}
```
_Response (201)_
```
{
    "access_token": <created access_token>
}
```
_Response (400 - Bad request)_
```
{ "message": "Invalid, check email or password" }
```

---
### GET /user/checkOut

> Determine product(s) in cart after checkout

_Request Header_
```
{
  "access_token": "<your access token>"
}
```
_Request Body_
```
not needed
```
_Response (200)_
```
{ message: "Checkout Successfully" }
```

---

### GET /products

> Show all products list

_Request Header_
```
{
  "access_token": "<your access token>"
}
```
_Request Body_
```
not needed
```
_Response (200)_
```
[
    {
        "id": "<product id>",
        "name": "<product name>",
        "img_url": "<product img_url>",
        "price": "<product price>",
        "stock": "<product stock>",
        "UserId": "<product UserId>",
        "category": "<product category>",
        "description": "<product description>",
        "createdAt": "2020-05-09T07:43:14.693Z",
        "updatedAt": "2020-05-09T08:05:31.782Z",
        "User": "<register response>"
    },
    {
        "id": "<product id>",
        "name": "<product name>",
        "img_url": "<product img_url>",
        "price": "<product price>",
        "stock": "<product stock>",
        "UserId": "<product UserId>",
        "category": "<product category>",
        "description": "<product description>",
        "createdAt": "2020-05-09T07:43:14.693Z",
        "updatedAt": "2020-05-09T08:05:31.782Z",
        "User": "<register response>"
    }
]
```

---
### POST /products

> Create a new product to the products list

_Request Header_
```
{
    "access_token": "<your access token>"
}
```
_Request Body_
```
{
	  "name": "<name to get insert into>",
    "img_url": "<img_url to get insert into>",
    "price": "<price to get insert into>",
    "stock": "<stock to get insert into>",
    "category": "<category to get insert into>",
    "description": "<description to get insert into>",
}
```
_Response (201 - Created)_
```
{
    "id": "<given id by system>",
    "name": "<posted name>",
    "img_url": "<posted img_url>",
    "price": "<posted price>",
    "stock": "<posted stock>",
    "UserId": "<posted UserId>",
    "category": "<posted category>",
    "description": "<posted description>",
    "updatedAt": "2020-05-09T08:07:50.265Z",
    "createdAt": "2020-05-09T08:07:50.265Z"

}
```
_Response(400- bad request)_
```
{ "message": "Unable created data product" }
```

---
### PUT /products/:id

> Update a selected product by ID

_Request Header_
```
{
  "access_token": "<your access token>"
}
```
_Request Body_
```
{
    "name": "<name to get insert into>",
    "img_url": "<img_url to get insert into>",
    "price": "<price to get insert into>",
    "stock": "<stock to get insert into>",
    "category": "<category to get insert into>",
    "description": "<description to get insert into>",
}
```
_Response(200)_
```
{ "message": "Update selected product successfully" }
```
_Response(400 - bad request)_
```
{ "message": "Unable updated data product" }
```
_Response(404 - not found)_
```
{ "message": "Data product not found" }
```

---
### DELETE /products/:id

> Delete a selected product by ID

_Request Header_
```
{
  "access_token": "<your access token>"
}
```
_Request Body_
```
not needed
```
_Response(200)_
```
{ "message": "Delete selected product successfully" }
```
_Response(404 - not found)_
```
{ "message": "Delete data product not found" }
```

---

### GET /banners

> Show all banners list

_Request Header_
```
{
  "access_token": "<your access token>"
}
```
_Request Body_
```
not needed
```
_Response (200)_
```
[
    {
        "id": "<banner id>",
        "name": "<banner name>",
        "img_url": "<banner img_url>",
        "UserId": "<banner UserId>",
        "createdAt": "2020-05-09T07:43:14.693Z",
        "updatedAt": "2020-05-09T08:05:31.782Z",
    },
    {
        "id": "<banner id>",
        "name": "<banner name>",
        "img_url": "<banner img_url>",
        "UserId": "<banner UserId>",
        "createdAt": "2020-05-09T07:43:14.693Z",
        "updatedAt": "2020-05-09T08:05:31.782Z",
    }
]
```

---
### POST /banners

> Create a new banner to the banners list

_Request Header_
```
{
    "access_token": "<your access token>"
}
```
_Request Body_
```
{
	"name": "<name to get insert into>",
  "img_url": "<img_url to get insert into>",
}
```
_Response (201 - Created)_
```
{
    "id": "<given id by system>",
    "name": "<posted name>",
    "img_url": "<posted img_url>",
    "UserId": "<posted UserId>",
    "updatedAt": "2020-05-09T08:07:50.265Z",
    "createdAt": "2020-05-09T08:07:50.265Z"

}
```
_Response(400- bad request)_
```
{ "message": "Unable created data banner" }
```

---
### DELETE /banners/:id
> Delete a selected banner by ID

_Request Header_
```
{
  "access_token": "<your access token>"
}
```
_Request Body_
```
not needed
```
_Response(200)_
```
{ "message": "Delete selected banner successfully" }
```
_Response(404 - not found)_
```
{ "message": "Delete data banner not found" }
```
---

### POST /carts

> Create a new cart for the selected product to the cart list

_Request Header_
```
{
    "access_token": "<your access token>"
}
```
_Request Body_
```
{
    "quantity": "<quantity to get insert into>",
}
```
_Response (201 - Created)_
```
{
    "id": "<given id by system>",
    "ProductId": "<given id by system>",
    "UserId": "<given id by system>",
    "quantity": "<cart quantity>",
    "totalPrice": "<computed totalPrice>",
    "createdAt": "2020-05-30T08:26:05.154Z",
    "updatedAt": "2020-05-30T08:26:05.154Z",
}
```
_Response(400- bad request)_
```
{ "message": "OWN_PRODUCT" }
or
{ "message": "OUT_OF_STOCK" }
```
_Response(404- not found)_
```
{ "message": "DATA NOT FOUND" }
```

---
### GET /carts/myCart

> Show all carts list

_Request Header_
```
{
  "access_token": "<your access token>"
}
```
_Request Body_
```
not needed
```
_Response (200)_
```
{
    "cart": [
        {
            "ProductId": "<cart ProductId>",
            "UserId": "<cart UserId>",
            "quantity": "<cart ProductId>",
            "totalPrice": "<cart ProductId>",
            "createdAt": "2020-05-30T08:26:05.154Z",
            "updatedAt": "2020-05-30T08:26:05.154Z",
            "Product": "<GET /products response>",
            "User": "<POST /register response>"
        },
        {
            "ProductId": "<cart ProductId>",
            "UserId": "<cart UserId>",
            "quantity": "<cart ProductId>",
            "totalPrice": "<cart ProductId>",
            "createdAt": "2020-05-30T08:26:05.154Z",
            "updatedAt": "2020-05-30T08:26:05.154Z",
            "Product": "<GET /products response>",
            "User": "<POST /register response>"
        },
    ]
}
```

---
### PUT /carts/updateCart

> Update a selected product by ID

_Request Header_
```
{
  "access_token": "<your access token>"
}
```
_Request Body_
```
{
    "quantity": "<quantity to get insert into>",
}
```
_Response (200)_
```
{ "message": "Succesfully update cart for selected product" }
```
_Response(400 - bad request)_
```
{ "message": "Unable update cart for selected product" }
```
---
### DELETE /carts/deleteCart

> Delete a cart for selected product

_Request Header_
```
{
  "access_token": "<your access token>"
}
```
_Request Body_
```
not needed
```
_Response(200)_
```
{ "message": "Sucessfully delete cart for selected product" }
```
_Response(404 - not found)_
```
{ "message": "Delete data cart for selected product not found" }
```

---
