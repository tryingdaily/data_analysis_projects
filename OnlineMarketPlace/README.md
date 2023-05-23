# Online Marketplace Database

This project is a database design for an online marketplace platform. The purpose of the project is to store and manage information about users, products, transactions, and reviews in an organized manner.

## Features

- User table: Stores user information such as user ID, username, email, and registration date.
- Product table: Stores product information including product ID, name, description, price, seller ID, and listing date.
- Transaction table: Records transaction details including transaction ID, product ID, buyer ID, seller ID, transaction date, and transaction status.
- Review table: Stores product review information like review ID, product ID, reviewer ID, review date, and review text.

## Getting Started

To set up the project on your local machine, follow these steps:

1. Clone the repository: `git clone https://github.com/your-username/online-marketplace-database.git`
2. Import the SQL script or database dump file into your preferred SQL database management system.
3. Configure the database connection settings in your application or SQL client.

## Database Schema

Here's an overview of the database schema:

```
User
- user_id (PK)
- username
- email
- registration_date

Product
- product_id (PK)
- name
- description
- price
- seller_id (FK to User.user_id)
- listing_date

Transaction
- transaction_id (PK)
- product_id (FK to Product.product_id)
- buyer_id (FK to User.user_id)
- seller_id (FK to User.user_id)
- transaction_date
- transaction_status

Review
- review_id (PK)
- product_id (FK to Product.product_id)
- reviewer_id (FK to User.user_id)
- review_date
- review_text
```

## Usage

Here are a few examples of SQL queries you can run against the database:

1. Retrieve all products sold by a specific user:
   ```sql
   SELECT *
   FROM Product
   WHERE seller_id = <seller_id>;
   ```

2. Calculate the average rating for a product:
   ```sql
   SELECT AVG(rating)
   FROM Review
   WHERE product_id = <product_id>;
   ```

3. Find the total revenue generated within a specific date range:
   ```sql
   SELECT SUM(price)
   FROM Transaction t
   JOIN Product p ON t.product_id = p.product_id
   WHERE t.transaction_date BETWEEN <start_date> AND <end_date>
   AND t.transaction_status = 'completed';
   ```

## Contributing

Contributions to the project are welcome! If you find any issues or have suggestions for improvements, please open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgements

- [OpenAI](https://openai.com) for providing the GPT-3.5 language model used to generate this README template.
