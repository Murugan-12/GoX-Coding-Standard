# Coding Conventions
Coding conventions secure quality, code readabilty and make code maintanence easier.   

# Rules of JavaScript

## 1.Magic Numbers

>
> Assiging a number with no meaning
> for example: for(let i=0;i<86400;i++) where 86400 means nothing
> 
> To make it easier to read we can use **const SECONDS_IN_A_DAY = 86400**


## 2.Deep Nesting

>
> const exampleArr = [ [ ['value'] ] ]  
> To retrieve the value we will be doing nested for loops  
> for example: exampleArr.forEach((arr1)=>{ arr1.foreach((arr2)=>{ arr2.foreach((element)=> return element ) }) })  
>
> Instead of reusing the code several times we can create a recusive function   
> for example: const retrieveValue = (element) => {   
>   if(Array.isarray(element)){ retrieveValue(element) }  
>   return element  
> }  
> retrieveValue(exampleArr)


## 3.Stop writing comments

>
> Its a little bit subjective topic but when you write a program which is self explanatory, the whole program will look clean and 
> it will be really helpful for others to understand code as it improves readability
> 


## 4.Avoid large functions

>
> For example: const arithmeticOperations = (a,b,c) => {  
> const addition = a + b + c;  
> const subtraction = a - b - c;  
> const multiplication = a * b * c;  
> return { addition, subtraction, multiplication}  
> }  
>
> In above example we are calling a function we does mupltiple operations, as we took simple example the code looks easy to understand but
> in real time projects we will be dealing with too many operations in that case we can allocate functions for each opeartion and call
> wherever we want.
>
> For example: const arithmeticOperations = (a,b,c) => {  
> return { addition(), subtraction(), multiplication()}  
> }  
> 
> const addition = (a,b,c) => return {a + b + c};  
> const subtraction = (a,b,c) => return {a - b - c};  
> const multiplication = (a,b,c) => return {a * b * c};  

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

