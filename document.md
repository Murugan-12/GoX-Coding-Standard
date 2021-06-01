# Coding Conventions

## 5. Favor descriptive names over concise

  > Always use make your identifiers self-explanatory
  > Some good way to make the identifiers self - explanatory are

  ### Best practices to name variables

  - Name variables as nouns, since it's just a placeholder,
    - Don't use some random names or single letter names as identifiers like ~~a~~ for something that holds a name of a person, instead give a name properly like **userName**

    ```javascript
    const a = "venkatesan"; // NEVER DO THIS
    ```

    Instead do this

    ```javascript
    const userName = "venkatesan";
    ```

    - Although single letter names are there is a special place where using a single letter names can be used and it is in for loop denoting the index

      ```javascript
      for(let i = 0; i < count; i++){
        // iterating something
      }
      ```
      single variables can be used in places where we inherently know the meaning of the variable since it's widely understood.

    - Always name boolean names such that it is readable and describes that it has a boolean value like `isLoggedIn` , `isEnabled`, `hasToken` etc.
      - Because it makes the code more readable in places like conditional blocks
      ```javascript
      if(isLoggedIn){
        routeTo(dashboard);
      }else{
        redirectTo(loginPage);
      }
      ```
    

  ### Best practices to name functions

  - Always name functions as verbs, since functions always does something
    - Never give a noun as a name for functions.
    - Function names has to be descriptive, meaning that it should describe itself for what it does like `getUserById` not like just ~~`getUser`~~.


    ```javascript
    const getUserById = (id) => {
      // Getting the user from the db based on the id given as argument
    }
    ```

    - Eventhough `getUser` is a verb, yet it isn't as descriptive as `getUserbyId`.
    - Avoid too much descriptive names/ unneccessary names such as ~~`getUserByIdFromDatabase`~~, where `FromDatabse` could be avoided since everyone knows that data comes from database, hence it's redundant to mention in the name.
    - As functions always does something, in particular to designing to `APIs` && `DBs`
    a function always tries to do `create`, `update`, `delete`, `get` operations. In those cases it is always preferred to name functions prefixing with what the operation it tries to do like **`deleteAuthToken`**, **`getProductsByCountry`** etc.


    ```javascript
    const createCategory = (category) => {
      // creates category 
    }

    const updateProduct = (product) => {
      //updates the product
    }

    const getProductsByCountry = (countryId) => {
      // gets the products associated to a particular country using countryId
    }

    const deleteAuthToken = (token) => {
      // deletes the authentication token
    }
    ```
  ### Casing in identifiers
  - For variables there are different options based on the language of your choice. They are
    - camelCase
    - snake lower case
    #### camelCase
      - The name refers to the internal capital letters, which resemble the humps on a camel's back. 
      Example
        ```javascript
        let isLoggedIn = true;
        ```
        in javascript camelcase is preferred while naming variables and functions.
    #### snake_lower_case
      - snake_lower_case combines words by replacing each space with an underscore (_) and all the other letters are lower cased.
      Example
        ```python
        is_variable = True
        ```
        in python identifiers for variables and functions are often in snake lower case.
    #### PascalCase
      - PascalCase combines words by capitalizing all words (even the first word) and removing the space.
      - PascalCase is often used to name classes, constructors and namespaces in several languages.
      Example
        ```java
        LinkedList<String> nameList = new LinkedList<String>();
        ```
      in java class and constructors should be in PascalCase.
    #### SNKAE_UPPER_CASE
      - SNKAE_UPPER_CASE combines words by replacing each space with an underscore (_) and all the other letters are upper cased.
      - It is used to name constants like **`PI` = 3.14**.
      Example
        ```javascript
        const DAYS_IN_LEAP_YEAR = 366
        ```


[Reference: JavaScript Best Practices and Coding Conventions - Write Clean Code from Javascript Mastery](https://www.youtube.com/watch?v=RMN_bkZ1KM0&ab_channel=JavaScriptMastery)