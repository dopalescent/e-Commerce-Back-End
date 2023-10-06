# e-Commerce-Back-End
Challenge 13

  ![License](https://img.shields.io/badge/License-MIT-blue)

  ## Description
  This application is the back-end portion of a fictional company's e-Commerce site. It uses Express.js and Sequelize to interact with a MySQL database. While it requires a compatible front-end app to be fully functional, this app's functionality can be observed and tested as is. We used Insomnia for testing in the demo video below.
  
  ## Table of Contents
  - [Installation](#installation)
  - [Usage](#usage)
  - [Contributing](#contributing)
  - [License](#license)
  - [Questions](#questions)
  
  ## Installation
  Clients can make use of this application by cloning it from its repository. They will need to perform a package install, create a .env file containing their mysql credentials, then use MYSQL to source the schema file.
  
  ## Usage
  A visual demonstration of this application's usage can be found at the following:
  https://drive.google.com/file/d/1d0RICb3iw9i0jSgWqTKHnsuqCwi9nMBo/view

  ### Launching the Application
  After running "npm i" and sourcing the database schema, you can optionally seed the database with test data by entering "npm run seed" into the command line. Launch the application by entering "npm run watch" into the command line. The app will default to listening at localhost:3001 unless another port is specified. The app is now ready for testing using the Insomnia application.

  ### Routes and Models
  API requests to Insomnia are made using the "/api" route. The ecommmerce_db database has four tables, three of which can be called by expanding the route using "/categories", "/products", and "/tags", respectively. (There are no routes to call the fourth table, "product tags", at time of release.) An Insomnia API request would look something like this: "http://localhost:3001/api/tags". Below is a description of the tables:

  #### - "category"
  Entries in the "category" table have two attributes:
  "id" - an integer value automatically assigned when the entry is created
  "category_name" - a string of characters giving an informal name to the entry, assigned manually by the user
  
  GET requests to this table will also return product entries within each returned category.

  #### - "product"
  Entries in the "product" table have five attributes:
  "id" - an integer value automatically assigned when the entry is created
  "product_name" - a string of characters giving an informal name to the entry, assigned manually by the user
  "price" - a decimal value, assigned manually by the user
  "stock" - an integer value, assigned manually by the user
  "category_id" - an integer value matching the "id" of an entry in the "category" table, assigned manually by the user, "null" entries are accepted

  #### - "tag"
  Entries in the "tag" table have two attributes:
  "id" - an integer value automatically assigned when the entry is created
  "tag_name" - a string of characters giving an informal name to the entry, assigned manually by the user

  #### - "product_tag"
  Entries in the "product_tag" table have three attributes:
  "id" - an integer value automatically assigned when the entry is created
  "product_id" - an integer value matching the "id" of an entry in the "product" table, assigned manually by the user, "null" entries are accepted
  "tag_id" - an integer value matching the "id" of an entry in the "tag" table, assigned manually by the user, "null" entries are accepted

  This table allows many "tag" entries to be belong to many "product" entries. While this table is not accessible by API request at this time, it is still functional within the database upon entering seed data.

  ### Request Methods
  Requests can be made using the GET, POST, PUT, and DELETE methods:

  #### - GET
  Making an API request to ".../api/{desired table}" using the GET method will return an array of data entries for every item in the requested table. Expanding the route with "/{id number}" will return a single entry from the table with the requested id number. If you seeded the database with test data before launching the app, you can make a GET request to ".../api/categories/2" and expect a returned entry for "shorts" from the "category" table.

  #### - POST
  Making a POST request to ".../api/{desired table}" will add a new entry to the table. This request must be sent with a body portion written in JSON, and include data for each attribute in the entry. The "id" attribute can be omitted in the request, since it is assigned automatically to an entry on its creation. A POST request to ".../api/products" would include a JSON body looking something like this:
```
{
  "product_name": "Pirate Hat",
  "price": 14.99,
  "stock": 1,
  "category_id": 4
}
```
  You can expect the request to return data for your new entry, including the newly-assigned id attribute. If you seeded the database with test data before launching the app, the "id" attribute should have a value of "6"; a GET request including the "id: 4" entry from the category table will also include this "product" table entry within it.

  #### - PUT
  Making a PUT request allows the user to update an existing entry within a table. A PUT request route must be expanded to include the id of the entry to be changed, i.e. ".../api/{desired table}/{id number}". The request must also be sent with a body portion written in JSON, and include data for each attribute in the entry. If you seeded the database with test data before launching the app, you can make a PUT request to ".../api/categories/3" including a JSON body looking something like this:
  ```
{
  "id": 3,
  "category_name": "Vinyls"
}
  ```
  A GET request to ".../api/categories/3" will demonstrate that the entry's "category_name" has been changed from "Music" to "Vinyls". Note that the "id" attribute is required here. While its value can be changed via a PUT request, it can potentially lead to database disorganization or dysfunction and is not recommended.

  #### - DELETE
  Making a DELETE request allows the user to remove an existing entry from a table. A DELETE request route must be expanded to include the id of the entry to be removed, i.e. ".../api/{desired table}/{id number}". If you seeded the database with test data before launching the app, you can make a DELETE request to ".../api/tags/8". A GET request to ".../api/tags" will demonstrate that the "id: 8" entry has been removed.
  

  ## Contributing
  Contributors: Greg Skudlarek
  
  ## License
  [![License](https://img.shields.io/badge/License-MIT-blue)](https://www.opensource.org/licenses/MIT)

  This application is covered under the MIT License. Click the badge to learn more.
  
  ## Questions
  Questions can be sent via the listed methods.
  
 
  GitHub: [dopalescent](https://github.com/dopalescent)
  

  Email: skudlgre000@gmail.com