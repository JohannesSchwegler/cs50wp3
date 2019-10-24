## HarvardX CS50W: Web Programming with Python and JavaScript

### Course's link
See [here](https://www.edx.org/course/cs50s-web-programming-with-python-and-javascript).

### My certificate
See [here](https://courses.edx.org/certificates/ce24e09f0bb74979b9cfb4535e72d444).

### Requirements
In this project, you’ll build an web application for handling a pizza restaurant’s online orders. Users will be able to browse the restaurant’s menu, add items to their cart, and submit their orders. Meanwhile, the restaurant owners will be able to add and update menu items, and view orders that have been placed.

Here are the requirements:

  - Menu: Your web application should support all of the available menu items for Pinnochio’s Pizza & Subs (a popular pizza place in Cambridge). It’s up to you, based on analyzing the menu and the various types of possible ordered items (small vs. large, toppings, additions, etc.) to decide how to construct your models to best represent the information. Add your models to orders/models.py, make the necessary migration files, and apply those migrations.
  - Adding Items: Using Django Admin, site administrators (restaurant owners) should be able to add, update, and remove items on the menu. Add all of the items from the Pinnochio’s menu into your database using either the Admin UI or by running Python commands in Django’s shell.
  - Registration, Login, Logout: Site users (customers) should be able to register for your web application with a username, password, first name, last name, and email address. Customers should then be able to log in and log out of your website.
  - Shopping Cart: Once logged in, users should see a representation of the restaurant’s menu, where they can add items (along with toppings or extras, if appropriate) to their virtual “shopping cart.” The contents of the shopping should be saved even if a user closes the window, or logs out and logs back in again.
  - Placing an Order: Once there is at least one item in a user’s shopping cart, they should be able to place an order, whereby the user is asked to confirm the items in the shopping cart, and the total (no need to worry about tax!) before placing an order.
  - Viewing Orders: Site administrators should have access to a page where they can view any orders that have already been placed.
  - Personal Touch: Add at least one additional feature of your choosing to the web application. Possibilities include: allowing site administrators to mark orders as complete and allowing users to see the status of their pending or completed orders, integrating with the Stripe API to allow users to actually use a credit card to make a purchase during checkout, or supporting sending users a confirmation email once their purchase is complete. If you need to use any credentials (like passwords or API credentials) for your personal touch, be sure not to store any credentials in your source code, better to use environment variables!
  - In README.md, include a short writeup describing your project, what’s contained in each file you created or modified, and (optionally) any other additional information the staff should know about your project. Also, include a description of your personal touch and what you chose to add to the project.
  - If you’ve added any Python packages that need to be installed in order to run your web application, be sure to add them to requirements.txt!

Beyond these requirements, the design, look, and feel of the website are up to you! You’re also welcome to add additional features to your website, so long as you meet the requirements laid out in the above specification!

### Project 3

Project 3 named "Django's Pizzeria" is a Django-based website that allows customers to make orders online. While it is based on Django Web framework, the project also uses a lot of JavaScript in frontend. Also I used Bootstrap as a CSS framework.

## Initialization
To run the website following things need to be done:
  - Install dependencies with `pip install -r requirements.txt`. Besides Django it contains Pillow library to work with images.
  - Make migrations with `python manage.py makemigrations`.
  - Apply migrations with `python manage.py migrate`.
  - Create superuser with `python manage.py createsuperuser`.
  - (Optionally) You can populate the database with menu items from http://www.pinocchiospizza.net/menu.html page by running `python populate_db.py`.

## Some notable DB models from orders/models.py
  - `Size`. Product variations item. After running populating script have two values: `Small` and `Large`.
  - `Topping`. Contains various toppings for pizza items.
  - `SubAddon`. Contains various addons for subs (Sorry, I don't know how to name these things properly).
  - `PizzaName`. Populating with two values: `Regular` and `Sicilian`.
  - `Pizza`. Pizza items themselves. Includes `toppings_count` field that can be 0, 1, 2, 3 or 5 for Special Pizza.
  - `SubName`. Contains all Subs names.
  - `Sub`. Subs themselves.
  - `Pasta`. A model for all pastas.
  - `Salad`. Salads.
  - `DinnerPlatterName`. Contains all possible Dinner Platters names.
  - `DinnerPlatter`. A model for Dinner Platters items.
  - `Order`. Represents customers orders (current or closed).
  - `OrderPizza`, `OrderSub`, `OrderPasta`, `OrderSalad`, `OrderDinnerPlatter`. These models are "helper" models used for Order model and contain actual order items parameters.

## Files and directories description
  - `media`. A directory for storing items images. It contains `no_photo_available.png`, a default image for all items.
  - `orders/static/orders` directory contains all static files used in project.
    - `scss`. It contains source SCSS file name `style.scss`.
    - `css`. Compiled CSS file, `style.css` and `style.css.map`.
    - `js`. A directory for JavaScript files.
      - `confirm.js`. A script user in order confirming page.
      - `remove.js`. Contains actions run while removing order itens.
      - `scripts.js`. Contains all other actions that run throughout the website.
  - `orders/templates/orders`. A directory to store templates files.
    - `base.html`. Base HTML template.
    - `index.html`. Index page template that contains all menu items.
    - `login.html`. Login page.
    - `modal.html`. This template contains modal window markup. Actually it is a Handlebars template that is included in `index.html` page.
    - `order.html`. A template for showing a single order items.
    - `orders_history.html`. This template shows all orders page.
    - `register.html`. A register template.
  - `orders/templatetags/orders`. A directory for storing orders template tags.
    - `get_class.py`. This script registers a `get_class` template tag that is used for including class name in `order.html` template.
  - `orders`. Some notable files in this application directory:
    - `admin.py`. Contains admin classes for orders application.
    - `models.py`. This file includes all orders models, some of them were listed above.
    - `urls.py`. Here I included all URLs of orders application.
    - `views.py`. Includes all the views from orders application.
  - `populate_db.py`. This script populates DB with items taken from http://www.pinocchiospizza.net/menu.html page.

## Personal touch
As a personal touch I have added two features:
  - All site administrators are able to mark orders as "Completed" through Admin UI.
  - A customer can remove items from current order before confirm.

The project's video: https://www.youtube.com/watch?v=CI0xDUe1TKA
