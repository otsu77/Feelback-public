# FEELBACK Project

## Authors
- otsu
- Colin Dufeutrelle
- Willy Beller

## PHP Version

PHP Version 7.4.33

## Description

FEELBACK is a database-centric project designed to manage user feedback for questionnaires, orders, and related products. The project includes the definition and creation of various database tables along with the necessary scripts for database population. This README file will guide you through the database structure, naming conventions, and how to set up and populate the database.

[Online site](https://evvilly.alwaysdata.net/FeelBack/)

## Project Structure

- **SQL Scripts:**
  - `Script_Create_DB.sql`: Contains the SQL code for creating the necessary tables for the FEELBACK system.
  - `Script_Fill_DB.sql`: Contains the SQL code to populate the tables with initial data.
  
- **Naming Conventions:**
  - Schema: `snake_case`
  - Table Names: `snake_case`, plural (e.g., `users`)
  - Column Names: `snake_case` (e.g., `created_at`)
  - Primary Key: `id`
  - Foreign Key: `<table_name>_id` (e.g., `users_id` in a table related to `users`)
  - Pivot Tables: `<table_1>_has_<table_2>` (e.g., `articles_has_tags`)  
  For more detailed information, refer to the [naming convention documentation](https://github.com/ColinDuf/Feelback/blob/main/livrables/FEELBACK%20-%20Convention%20de%20nommage.pdf)

- **Data Dictionary**: The project includes various tables with specific fields and types, including:
  - **Users**: `id`, `username`, `email`, `password`, `created_at`, `updated_at`, `deleted_at`, `roles_id`
  - **Products**: `id`, `title`, `price_ht`, `created_at`, `updated_at`, `deleted_at`
  - **Orders**: `id`, `user_id`, `created_at`, `updated_at`, `deleted_at`
  - **Feedback**: `id`, `feedback_id`, `questionnaire_id`, `created_at`, `updated_at`, `deleted_at`
  
  The detailed data dictionary can be found [here](https://github.com/ColinDuf/Feelback/blob/main/livrables/FEELBACK%20-%20Dictionnaire%20de%20donn%C3%A9es.pdf)

## How to Use

### 1. Setting Up the Database

Run the following SQL script to create the database and its tables: Script_Create_DB.sql
This script will create all the necessary tables and relationships following the database design outlined in the project.

### 2. Populating the Database

After creating the database structure, you can populate it with initial data using the `Script_Fill_DB.sql` file.
This will insert the predefined data into the tables.

## Tables Overview

The database schema consists of several key tables:
- **Users**: Manages user information, roles, and authentication.
- **Products**: Stores information about the products related to the feedback.
- **Orders**: Links users and products through orders.
- **Questionnaires**: Contains feedback questionnaires for users.
- **Feedback**: Stores user responses to feedback questionnaires.
  
Additionally, pivot tables such as `products_has_orders` and `questions_has_questionnaires` handle many-to-many relationships.

## Data Logging and Soft Deletion

- **Data Logging**: Each table has `created_at`, `updated_at` columns for tracking changes.
- **Soft Deletion**: The `deleted_at` column enables soft deletion, allowing data to be marked as deleted without being permanently removed.
