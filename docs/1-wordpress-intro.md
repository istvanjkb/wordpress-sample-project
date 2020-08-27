# WordPress Docker Project

## Scope of the session

The scope is to set up a working WordPress system using docker and get acquainted with its basic features (themes, plugins, routing & more). This document does not provide a detailed description of the tool, for such information check out the [WordPress Documentation](https://wordpress.org/support/) or the [WordPress Developers Documentation](https://developer.wordpress.com/docs/).

## General description

WordPress, written in PHP, is a CMS (Content Management System) designed for developers, content writers and designers. It is user-friendly and makes creating websites possible _without deep programming knowledge_. Still, certain sections can be modified programmatically (we can write custom CSS classes, alter HTML structure etc.).

# Create a custom website with WordPress and Docker

## Step 1: Assemble a docker compose file and run WordPress in it

In order to run a properly working `WordPress` container, we will also need a `MySQL` instance that is used as the basic database responsible for role handling and storing sensitive data. WordPress interfaces with this database by itself, you as an end user, shouldn't have to worry much about its structure.

We will also need a `PhpMyAdmin` client to be able to monitor the data stored in the database.

Create a docker-compose.yaml file as follows, then run `docker-compose up`:

```yaml
version: "3"

services:
  # DATABASE
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
    networks:
      - wpsite
  # PHPMYADMIN
  phpmyadmin:
    depends_on:
      - db
    image: phpmyadmin/phpmyadmin
    restart: always
    ports:
      - "8080:80"
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: password
    networks:
      - wpsite
  # WORDPRESS
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - "8000:80"
    restart: always
    volumes: ["./:/var/www/html"]
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
    networks:
      - wpsite
networks:
  wpsite:
volumes:
  db_data:
```

> If you get the following error message, `"Message":"Unhandled exception: Filesharing has been cancelled"`, make sure to add your working directory to the docker app resources (Docker -> Resources -> File Sharing)

## Step 2: Setup your website

By accessing `localhost:8000` you will get to the intro page of WordPress. There you will create a user and launch your site. From now on, this URL will serve as the entry page of your website. You will notice that it was preloaded with some demo data.

## Step 3: Analyze the admin panel

By typing in `http://localhost:8000/wp-admin` you will be redirected to the admin panel of the site (you might need to log in with your user), which is where all the magic happens.

### Some important menu items:

- **`Media:`** all your multimedia files that are used for the page will be found here
- **`Pages:`** the place to create, edit, publish, unpublish and delete pages (you can work with draft pages until they are finished)
- **`Appearance:`** manage themes and widgets
- **`Users:`** manage users with different roles
- **`Settings:`** create and modify how permalinks are formatted, choose the default page for the application, access and modify general settings & more

## Step 4: Activate a theme from the theme collection

A theme is a library that defines the functionalities and look of the elements used on a site. Some themes even come with more complex predefined components and custom website builders.

- Open the admin panel
- Open Appearance -> Themes on the left
- Click `Add new`, then install and activate a theme

This will set your newly selected theme as active. Check the website (by opening `localhost:8000` or hovering on `Wordpress Simple` in the header and clicking `Visit site`).

## Step 5: Upload a theme from a zip file and activate it.

- Download a custom theme from [here](https://wordpress.org/themes/browse/new/).
- Open Appearance -> Themes on the left
- Click `Add new`
- Click `Upload theme`
- Upload and install the zip file you have just downloaded

This will set your newly selected theme as active. Check the website to see the changes.

> Note: You can change the theme anytime, though it is good practice to remove unused themes from the project and stick to a single theme during the implementation.

## Step 6: Create a new page and set it as the default page of the website

- Go to `Pages`
- Click on `Add new`
- The website builder makes create paging look like playing with puzzles: you can add components, reorganize them and modify their characteristics in the right panel.
- Add some components to the page, then save it and publish it.
- Go to `Settings` -> `Reading` and set your newly created page as the homepage.

Open the website and make sure everything works as expected.

## Step 7: Change the formatting of permalinks

You may have noticed that the urls of different pages look something like `http://localhost:8000/?p=123`. To achieve a more elegant formatting, follow the following steps:

- Go to `Settings` -> `Permalinks`
- Change the common settings to `Post name`

Check a page other than home.

## Step 8: Add a plugin

WordPress plugins offer functionalities that are required for a project, but are missing from the base framework. They can be accessed on the `Plugins` page from the admin panel navigation.

Some plugins are so complex that, after activation, they will be listed in the admin panel navigation (such an example: `Slider Hero with Animation, Video Background & Intro Maker`) where you can create instances of them, then use it on pages/posts.

### Activate a simple plugin:

- Search for `Hello Dolly`
- Install it then activate it

This simple plugin will display a fun quote on your admin panel in the upper right corner. Nothing complicated, but it gets you started.

## Step 9: Play with the features

There are many other features that can be addressed. For instance, you can write some code under `Appearance` -> `Theme Editor` or in the page editor using the combination `Ctrl + Shift + Alt + M` (this toggles the code editor view and the smart website builder interface).

The following video covers many other aspects of WordPress: https://www.youtube.com/watch?v=8AZ8GqW5iak.
