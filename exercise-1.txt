CREATE TABLE account (
    id INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(255),
    password VARCHAR(40),
    createdOn DATETIME,
    modifiedOn DATETIME
);

CREATE TABLE address_book (
    id INT AUTO_INCREMENT PRIMARY KEY,
    account_id INT,
    name VARCHAR(255),
    createdOn DATETIME,
    modifiedOn DATETIME
);

CREATE TABLE entry (
    id INT AUTO_INCREMENT PRIMARY KEY,
    address_book_id INT,
    first_name VARCHAR(255),
    last_name VARCHAR(255),
    birthday DATETIME,
    type ENUM ("phone", "address", "e-mail")
);

CREATE TABLE phone (
    id INT AUTO_INCREMENT PRIMARY KEY,
    entry_id INT,
    type ENUM ("home", "work", "other"),
    subtype ENUM ("landline", "cell", "fax")
);

CREATE TABLE address (
    id INT AUTO_INCREMENT PRIMARY KEY,
    entry_id INT,
    type ENUM ("home", "work", "other"),
    address_line_1 VARCHAR(255),
    address_line_2 VARCHAR(255),
    city VARCHAR(255),
    province VARCHAR(128),
    country VARCHAR(128),
    postal_code VARCHAR(10)
);

CREATE TABLE email (
    id INT AUTO_INCREMENT PRIMARY KEY,
    entry_id INT,
    content VARCHAR(255)
);