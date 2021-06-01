## code repetition
>
>If we are using the same code that was used before then it is a sign that the repeated block may need to be extracted into a separate function.

>for example:

>Here we are having a deeply nested looping statement. where we have three times repeated the same for each statement.

>We have a lot of repeated code so it is much better to extract it to a separate function.

>exampleArray.forEach((arr1) => {
>    arr1.forEach((arr2) => {
>        arr2.forEach((el) => {
>            console.log(el);
>        })
>    })
>})

>Instead of reusing the code several times, we can create a recursive function

>const retrieveValue = (element) => {
>    if(Array.isarray(element)){ retrieveValue(element) }
>        return element
>}
>retrieveValue(exampleArr)


>Another great way to understand Code Repetition is retrieving data from parameters.

>for example:

>const getUserCredentials = (user) =>{
>    const name = user.name;
>    const surname = user.surname;
>    const password = user.password;
>    const email = user.email;
>}

>Here we are reading the value quite a lot and this is not a good practice.
>With es6 object destructuring we can do the following.

>const getUserCredentials = (user) =>{
>    const { name, surname, password, email } = user;
>}

>This is the same thing with much less repeated code!!
>

## Variable Naming
>
### Camel case
>
>Camel case is a naming standard that is used for identifier names example variables and functions.

>It states that the name needs to begin with lowercase and every first letter of the next word is uppercase.

>for example:

>const camelCase = '';
>const thisIsARandomCamelCaseName;
>let getUserCredentials;
>
### Meaningful Names
>
>The most important rule regarding variable naming is to use meaningful names and they need to express their exact meaning.

>for example:
>If you are fetching posts from some user we can give the variable name as,

>const getUserData;

>But what data we are actually getting is the better way to name it.

>const getUserPosts;
>
#### Favor description over concise
>
>If you are having difficulty in finding a two or three-word description for your variable name or if you feel your concise name is not conveying the right meaning it is better to be descriptive.

>for example:

>const findUserByNameOrEmail;
>const setUserLoggedInTrue;

