# Coding Conventions

Coding conventions secure quality, code readability and make code maintenance easier.

# Rules of JavaScript

## 1.Magic Numbers

Having a number with no meaning
For example:

```javascript
for(let i = 0;i < 86400; i++)
```

where `86400` means nothing

To make it easier to read we can use const

```javascript
const SECONDS_IN_A_DAY = 86400;
```

## 2.Deep Nesting

Consider

```javascript
const exampleArr = [[["value"]]];
```

To retrieve the value we will be using nested for loops  
For example:

```javascript
exampleArr.forEach((arr1)=>{
  arr1.foreach((arr2)=>{
      arr2.foreach((element)=>
      return element
      )
      })
      })
```

Instead of reusing the code several times, we can create a recursive function that could be more readable.

For example:

```javascript
const retrieveValue = (element) => {
  if (Array.isarray(element)) {
    retrieveValue(element);
  }
  return element;
};

retrieveValue(exampleArr);
```

## 3.Stop writing comments

It's a little bit subjective topic but when you write a program, which is self-explanatory, the whole program will look clean and,

It will be really helpful for others to understand code as it improves readability.

## 4.Avoid large functions

```
Always write your functions as `modular` as possible
```

For example:

Consider the arithmeticoperations function below,

```javascript
const arithmeticOperations = (a, b, c) => {
  const addition = a + b + c;
  const subtraction = a - b - c;
  const multiplication = a * b * c;
  return { addition, subtraction, multiplication };
};
```

In the above example, we are calling a function that does multiple operations, as we took simple example the code looks easy to understand but,
In real-time projects we will be dealing with too many operations in that case we can allocate functions for each operation and call wherever we want.

For example:

```javascript
const addition = (a,b,c) => return {a + b + c};
const subtraction = (a,b,c) => return {a - b - c};
const multiplication = (a,b,c) => return {a * b * c};
const arithmeticOperations = (a,b,c) => {
  return { addition(), subtraction(), multiplication()}
}
```

## 5. Favor descriptive names over concise

Always use make your identifiers self-explanatory
Some good way to make the identifiers self-explanatory are

### Best practices to name variables

- Name variables as nouns, since it's just a placeholder,

  - Don't use some random names or single-letter names as identifiers like ~~a~~ for something that holds a name of a person, instead give a name properly like **userName**

    ```javascript
    const a = "johndoe"; // NEVER DO THIS
    ```

    Instead, do this

    ```javascript
    const userName = "johndoe";
    ```

  - Although single letter names are there is a special place where using a single letter name can be used and it is in for loop denoting the index

    >

    ```javascript
    for (let i = 0; i < count; i++) {
      // iterating something
    }
    ```

    single variables can be used in places where we inherently know the meaning of the variable since it's widely understood.

  - Always name boolean names such that it is readable and describes that it has a boolean value like `isLoggedIn`, `isEnabled`, `hasToken` etc.
    - Because it makes the code more readable in places like conditional blocks
      >
    ```javascript
    if (isLoggedIn) {
      routeTo(dashboard);
    } else {
      redirectTo(loginPage);
    }
    ```

### Best practices to name functions

- Always name functions as verbs, since functions always do something

  - Never give a noun as a name for functions.
  - Function names have to be descriptive, meaning that it should describe itself for what it does like `getUserById` not like just ~~`getUser`~~.

    >

    ```javascript
    const getUserById = (id) => {
      // Getting the user from the db based on the id given as argument
    };
    ```

  - Even though `getUser` is a verb, yet it isn't as descriptive as `getUserbyId`.
  - Avoid too many descriptive names/ unnecessary names such as ~~`getUserByIdFromDatabase`~~, where `FromDatabse` could be avoided since everyone knows that data comes from a database, hence it's redundant to mention in the name.
  - As functions always do something, in particular to designing to `APIs` && `DBs`
    a function always tries to do `create`, `update`, `delete`, `get` operations. In those cases, it is always preferred to name functions prefixing with what the operation it tries to do like **`deleteAuthToken`**, **`getProductsByCountry`**, etc.

    >

    ```javascript
    const createCategory = (category) => {
      // creates category
    };

    const updateProduct = (product) => {
      //updates the product
    };

    const getProductsByCountry = (countryId) => {
      // gets the products associated to a particular country using countryId
    };

    const deleteAuthToken = (token) => {
      // deletes the authentication token
    };
    ```

### Casing in identifiers

- For variables, there are different options based on the language of your choice. They are
  - camelCase
  - snake lower case
  #### camelCase
  - The name refers to the internal capital letters, which resemble the humps on a camel's back.
  - Example
    ```javascript
    let isLoggedIn = true;
    ```
    in javascript, camelcase is preferred while naming variables and functions.
  #### snake_lower_case
  - snake*lower_case combines words by replacing each space with an underscore (*) and all the other letters are lowercased.
  - Example
    ```python
    is_variable = True
    ```
    in python identifiers for variables and functions are often in snake lower case.
  #### PascalCase
  - PascalCase combines words by capitalizing all words (even the first word) and removing the space.
  - PascalCase is often used to name classes, constructors and namespaces in several languages.
  - Example
  ```java
  LinkedList<String> nameList = new LinkedList<String>();
  ```
  in java class and constructors should be in PascalCase.
  #### SNAKE_UPPER_CASE
  - SNKAE*UPPER_CASE combines words by replacing each space with an underscore (*) and all the other letters are upper cased.
  - It is used to name constants like **`PI` = 3.14`**.
  - Example
    ```javascript
    const DAYS_IN_LEAP_YEAR = 366;
    ```

## 6.Code Repetition

If we are using the same code that was used before then it is a sign that the repeated block may need to be extracted into a separate function.

for example:

Here we are having a deeply nested looping statement. where we have three times repeated the same for each statement.
For example:

We have a lot of repeated code so it is much better to extract it to a separate function.

```javascript
exampleArray.forEach((arr1) => {
  arr1.forEach((arr2) => {
    arr2.forEach((el) => {
      console.log(el);
    });
  });
});
```

Instead of reusing the code several times, we can create a recursive function.

```javascript
const retrieveValue = (element) => {
  if (Array.isarray(element)) {
    retrieveValue(element);
  }
  return element;
};
retrieveValue(exampleArr);
```

Another great way to understand Code Repetition is retrieving data from parameters.

For example:

```javascript
const getUserCredentials = (user) => {
  const name = user.name;
  const surname = user.surname;
  const password = user.password;
  const email = user.email;
};
```

Here we are reading the value quite a lot and this is not a good practice.
With es6 object destructuring we can do the following.

```javascript
const getUserCredentials = (user) => {
  const { name, surname, password, email } = user;
};
```

This is the same thing with much less repeated code!!

## 7.Variable Naming

#### Camel case :

Camel case is a naming standard that is used for identifier names example variables and functions.

It states that the name needs to begin with lowercase and every first letter of the next word is uppercase.

For example:

```javascript
const camelCase = '';
const thisIsARandomCamelCaseName;
let getUserCredentials;
```

#### Meaningful Names :

The most important rule regarding variable naming is to use meaningful names and they need to express their exact meaning.

For example:
If you are fetching posts from some user we can give the variable name as,

```javascript
const getUserData;
```

But what data we are actually getting is the better way to name it.

```javascript
const getUserPosts;
```

#### Favor description over concise :

If you are having difficulty in finding a two or three-word description for your variable name or if you feel your concise name is not conveying the right meaning it is better to be descriptive.

For example:

```javascript
const findUserByNameOrEmail;
const setUserLoggedInTrue;
```

#### Use Nouns for classNames :

Classes don't take things. They are Things.

```javascript
class Car = {
  //...
}
```

#### Use PascalCase for classNames :

PascalCase is simply like camelCase but the first letter is also capitalized.

```javascript
❌  class task = {
      //...
    }

✅  class Task = {
      //...
    }
```

#### Capitalize constant values :

A constant value is something that won't change.
We write them in _SNAKE UPPER CASE_.
eg.,

```javascript
const SECOND_IN_A_DAY = 86400;
```

But in Javascript const variables can be mutated with re-assignment.
So it is advised to write const variables that you will not mutate in _SNAKE UPPER CASE_ and those you will mutate in _LOWER CASE_.

i.e.,
Constants that you **don't mutate** should be written as

```javascript
const HOURS_IN_A_DAY = 24;
const USER_AGE = 34;
```

Constants that you **mutate** should be written as

```javascript
const today = new Date();
```

#### Avoid one letter variable names :

It is easy to forget what a one-letter variable later in your code.
So give proper understandable names for better readability.

```javascript
❌ const q = () = {}
✅ const query = () = {}

❌ const d = new Date()
✅ const newDate = new Date()

❌ for(let i = 0; i < 10; i++){}
✅ for(let index = 0; index < 10; index++){}
```

---

[![](https://www.youtube.com/s/desktop/1f277c2a/img/favicon_32.png)](https://www.youtube.com/watch?v=RMN_bkZ1KM0&ab_channel=JavaScriptMastery)
[Reference: JavaScript Best Practices and Coding Conventions - Write Clean Code from Javascript Mastery](https://www.youtube.com/watch?v=RMN_bkZ1KM0&ab_channel=JavaScriptMastery)
